# sEMG-feature-extration
Extracting intermuscular network features from EMG data provided in the ninapro dataset

#Data
The NinaPro dataset captures electromyographic (EMG) data from human subjects using a setup involving twelve strategically placed electrodes on the arm. The first eight electrodes densely sample muscles around the forearm, while the remaining four target specific muscles crucial for hand and forearm control. Electrodes are secured with adhesive tape and a self-adhesive bandage to prevent displacement. Subjects, seated at a desk, perform hand movements instructed through a video on a laptop, completing six repetitions of 17 movements each, with brief rest intervals. The dataset collects data on age, gender, and other personal information, with ethical approval from the relevant authority. This setup provides a comprehensive dataset covering various hand postures encountered in daily activities.

# Processing
We conducted an analysis using data from the [Ninapro dataset](http://ninaweb.hevs.ch/), focusing on samples collected from five different subjects. Specifically, we worked with EMG (Electromyography) data recorded from 12 sensors, following the dataset's specifications and settings outlined on its webpage.

To prepare the data for analysis, we organized EMG samples based on the exercise numbers performed by the subjects. For each subject and exercise combination, we segmented the data into six samples by cropping the signal according to the repetitions array. This allowed us to create a standardized set of samples for analysis.

Next, we employed a filtering technique to reduce noise in the EMG signals. Using an averaging filter with a window size of 3, we smoothed out fluctuations and artifacts present in the data, enhancing its clarity and quality.

With the cleaned data, we proceeded to calculate the Power Spectral Density (PSD) for each individual sample. The PSD provides insight into the frequency content of the EMG signals, revealing important information about muscle activity patterns.

After obtaining the PSDs for all samples, we averaged them across repetitions and subjects. This enabled us to generate a comprehensive representation of the global PSD for each exercise, capturing the collective characteristics of the muscle activity during the performed exercises.

Furthermore, we explored the relationships between different muscles by computing the Cross Power Spectral Density (Cross PSD) for each pair of muscles (a total of 66 values, considering combinations of 12 sensors taken 2 at a time). This analysis allowed us to examine how the muscle activities interacted and coordinated with each other during the exercises.

Finally, we utilized the Cross PSD values to calculate the coherence of the intermuscular network. Coherence provides a measure of the synchronization between muscle activities, shedding light on the coordination and communication within the muscle groups involved in the performed exercises.
The results where analysed using the box and whisker plot and the ANOVA statistic test. 

# Insights on data patterns 
The box and whisker plot illustrates the degree of intermuscular coherence (IMC) for each of the 17 hand exercises in the NinaPro dataset. 

Key insights from the plot:
1. Exercise 9 exhibits the highest median degree of coherence, suggesting strong synchronization between muscle pairs during this particular movement.
2. Exercises 4, 5, and 7 also show relatively high median coherence degrees, indicating significant coordination between muscles.
3. The variability in coherence degrees across exercises suggests that certain movements may require more precise muscle coordination than others.
4. Exercises 1, 2, 6, 10, 12, 13, and 16 demonstrate lower median coherence degrees, indicating less synchronization between muscle pairs during these movements.
5. Outliers in exercises 3, 8, 9, and 14 suggest variability in coherence degrees within these exercises, possibly due to individual differences in muscle activation patterns or movement execution.

Overall, the plot provides valuable insights into the coordination patterns of hand muscles during different exercises, which can inform our understanding of hand motor control and rehabilitation strategies.

# Statistical analysis
The F-statistic of approximately 3.76 indicates a significant difference in coherence degrees among the first five exercises in the NinaPro dataset. With a p-value of approximately 0.0157, this difference is statistically significant, suggesting distinct patterns of muscle coordination or synchronization between these exercises.