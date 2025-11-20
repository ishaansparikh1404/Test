# /// script
# requires-python = ">=3.11"
# dependencies = [
#     "marimo",
#     "numpy",
#     "pandas",
#     "matplotlib",
# ]
# ///

import marimo as mo
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

__generated_with = "0.10.0"
app = marimo.App()

# Email comment as requested
# Author: 25f1000038@ds.study.iitm.ac.in
# Interactive Data Analysis Notebook demonstrating variable relationships

@app.cell
def __():
    # Cell 1: Import required libraries and setup
    # This cell establishes the foundation for our data analysis
    
    import marimo as mo
    import numpy as np
    import pandas as pd
    import matplotlib.pyplot as plt
    
    # Set random seed for reproducibility
    np.random.seed(42)
    
    return mo, np, pd, plt

@app.cell
def __(np):
    # Cell 2: Generate synthetic dataset with dependent variables
    # This cell creates sample data showing relationship between study hours and exam scores
    
    # Generate study hours (independent variable)
    study_hours = np.random.normal(15, 5, 100)
    study_hours = np.clip(study_hours, 0, 40)  # Ensure realistic bounds
    
    # Generate exam scores with some noise (dependent variable)
    # Base relationship: score = 2.5 * hours + 50 + noise
    noise = np.random.normal(0, 10, 100)
    exam_scores = 2.5 * study_hours + 50 + noise
    
    # Create DataFrame for better data handling
    student_data = pd.DataFrame({
        'study_hours': study_hours,
        'exam_scores': exam_scores,
        'attendance_rate': np.random.uniform(70, 100, 100)
    })
    
    return exam_scores, noise, student_data, study_hours

@app.cell
def __(mo):
    # Cell 3: Create interactive slider widget
    # This slider allows users to filter data by minimum study hours
    
    min_hours_slider = mo.ui.slider(
        start=0,
        stop=40,
        step=2,
        value=10,  # Default value
        label="Minimum Study Hours Filter",
        show_value=True
    )
    
    return min_hours_slider

@app.cell
def __(min_hours_slider, student_data):
    # Cell 4: Filter data based on slider value
    # This cell depends on both the slider widget and the original data
    # Data flow: min_hours_slider.value -> filtered_data
    
    # Filter students who studied more than the slider threshold
    filtered_data = student_data[
        student_data['study_hours'] >= min_hours_slider.value
    ].copy()
    
    # Calculate correlation coefficient for filtered data
    if len(filtered_data) > 1:
        correlation = filtered_data['study_hours'].corr(filtered_data['exam_scores'])
    else:
        correlation = 0.0
    
    return correlation, filtered_data

@app.cell
def __(correlation, filtered_data, min_hours_slider, plt):
    # Cell 5: Create visualization based on filtered data
    # This cell creates a scatter plot showing the relationship
    
    plt.figure(figsize=(10, 6))
    
    # Create scatter plot
    plt.scatter(filtered_data['study_hours'], filtered_data['exam_scores'], 
                alpha=0.6, c='blue', s=50)
    
    # Add trend line if we have enough data points
    if len(filtered_data) > 1:
        z = np.polyfit(filtered_data['study_hours'], filtered_data['exam_scores'], 1)
        p = np.poly1d(z)
        plt.plot(filtered_data['study_hours'], p(filtered_data['study_hours']), 
                "r--", alpha=0.8, linewidth=2)
    
    plt.xlabel('Study Hours per Week')
    plt.ylabel('Exam Score')
    plt.title(f'Relationship between Study Hours and Exam Scores\n'
              f'(Filtered: ≥{min_hours_slider.value} hours, n={len(filtered_data)})')
    plt.grid(True, alpha=0.3)
    
    # Set consistent axis limits for better comparison
    plt.xlim(0, 40)
    plt.ylim(0, 150)
    
    plt.tight_layout()
    plot_figure = plt
    
    return plot_figure

@app.cell
def __(correlation, filtered_data, min_hours_slider, mo):
    # Cell 6: Dynamic markdown output based on widget state
    # This cell creates dynamic documentation that updates with the slider
    
    # Calculate summary statistics
    avg_hours = filtered_data['study_hours'].mean()
    avg_score = filtered_data['exam_scores'].mean()
    sample_size = len(filtered_data)
    
    # Create dynamic markdown
    dynamic_report = mo.md(f"""
    ## 📊 Interactive Data Analysis Report
    
    **Data Scientist:** 25f1000038@ds.study.iitm.ac.in
    
    ### Current Analysis Parameters
    - **Minimum Study Hours Filter:** {min_hours_slider.value} hours/week
    - **Sample Size:** {sample_size} students
    - **Correlation Coefficient:** {correlation:.3f}
    
    ### Key Findings
    - Students who studied ≥{min_hours_slider.value} hours/week:
      - Average study time: {avg_hours:.1f} hours/week
      - Average exam score: {avg_score:.1f} points
      - **Correlation strength:** {"Strong" if abs(correlation) > 0.7 else "Moderate" if abs(correlation) > 0.4 else "Weak"}
    
    ### Data Quality Notes
    {"⚠️ **Note:** Small sample size may affect reliability of correlation" if sample_size < 20 else "✅ **Sample size is adequate** for reliable correlation analysis"}
    
    ---
    
    **Last Updated:** {pd.Timestamp.now().strftime('%Y-%m-%d %H:%M:%S')}
    """)
    
    return dynamic_report, sample_size

@app.cell
def __(correlation, mo, sample_size):
    # Cell 7: Additional analysis with variable dependencies
    # This cell depends on correlation and sample_size from previous cells
    
    # Perform statistical significance test
    from scipy import stats
    
    if sample_size > 2:
        # Create t-statistic for correlation significance
        t_stat = correlation * np.sqrt((sample_size - 2) / (1 - correlation**2))
        p_value = 2 * (1 - stats.t.cdf(abs(t_stat), sample_size - 2))
        
        significance = "significant" if p_value < 0.05 else "not significant"
        confidence = 1 - p_value
    else:
        t_stat = 0
        p_value = 1.0
        significance = "insufficient data"
        confidence = 0
    
    statistical_summary = mo.md(f"""
    ### 📈 Statistical Analysis
    
    **Correlation Analysis:**
    - Correlation coefficient: {correlation:.4f}
    - T-statistic: {t_stat:.4f}
    - P-value: {p_value:.4f}
    - Statistical significance: {significance}
    - Confidence level: {confidence:.1%}
    
    {"**Interpretation:** The correlation is statistically significant at the 0.05 level" if p_value < 0.05 and sample_size > 2 else "**Interpretation:** The correlation is not statistically significant" if sample_size > 2 else "**Interpretation:** Insufficient data for statistical testing"}
    """)
    
    return statistical_summary, t_stat, p_value, significance, confidence

@app.cell
def __(plt):
    # Cell 8: Display the final plot
    # This cell renders the matplotlib figure
    
    plt.show()
    return

if __name__ == "__main__":
    app.run()
