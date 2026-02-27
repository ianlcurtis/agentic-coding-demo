# Health Metrics Dashboard — Requirements

## Overview

A web application that allows users to log personal health vitals, visualize trends over time, and receive alerts when values fall outside healthy ranges.

---

## User Stories

### 1. Vital Entry

**US-1.1:** As a user, I want to log my blood pressure (systolic and diastolic) so that I can track it over time.

**US-1.2:** As a user, I want to log my heart rate (bpm) so that I can monitor my cardiovascular health.

**US-1.3:** As a user, I want to log my weight (lbs or kg) so that I can track changes over time.

**US-1.4:** As a user, I want to log my blood glucose level (mg/dL) so that I can monitor for abnormal values.

**US-1.5:** As a user, I want each vital entry to automatically record the date and time so that I know when the reading was taken.

**US-1.6:** As a user, I want to be able to manually select a date and time for a reading so that I can log past measurements.

### 2. Dashboard & Visualization

**US-2.1:** As a user, I want to see a dashboard with summary cards showing my most recent reading for each vital so that I get a quick snapshot of my health.

**US-2.2:** As a user, I want to see a line chart for each vital type showing how my values have changed over time so that I can identify trends.

**US-2.3:** As a user, I want to toggle between different time ranges (7 days, 30 days, 90 days, all time) on the charts so that I can zoom in or out on trends.

**US-2.4:** As a user, I want healthy range reference bands displayed on charts (e.g., shaded green zone for normal blood pressure) so that I can visually see where my readings fall.

### 3. Alerts & Thresholds

**US-3.1:** As a user, I want to see a visual warning indicator on the dashboard when my most recent reading is outside the healthy range so that I am immediately aware of concerning values.

**US-3.2:** As a user, I want the app to use the following default healthy ranges:
- **Blood Pressure:** Systolic 90–120 mmHg, Diastolic 60–80 mmHg
- **Heart Rate:** 60–100 bpm
- **Weight:** No default alert (user-configurable)
- **Blood Glucose:** 70–100 mg/dL (fasting)

**US-3.3:** As a user, I want to customize my personal healthy ranges for any vital so that alerts are relevant to my individual health profile.

### 4. History & Filtering

**US-4.1:** As a user, I want to view a history table listing all my recorded vitals so that I can review past entries.

**US-4.2:** As a user, I want to filter the history table by vital type so that I can focus on a specific metric.

**US-4.3:** As a user, I want to filter the history table by a date range so that I can find readings from a specific period.

**US-4.4:** As a user, I want to delete an individual entry from my history so that I can remove erroneous readings.

### 5. Data Persistence

**US-5.1:** As a user, I want my data to be saved locally in the browser so that it persists between sessions without requiring an account or backend.

**US-5.2:** As a user, I want to export my health data as a file so that I can share it with my healthcare provider.

**US-5.3:** As a user, I want to import health data from a file so that I can restore or migrate my records.

### 6. UI / UX

**US-6.1:** As a user, I want the application to be responsive so that I can use it on both desktop and mobile devices.

**US-6.2:** As a user, I want a clean, medical-themed design with clear typography and adequate contrast so that the interface is easy to read.

**US-6.3:** As a user, I want a navigation bar with links to the Dashboard, Log Entry, and History pages so that I can move between features easily.

**US-6.4:** As a user, I want form validation with clear error messages when I submit invalid vital readings (e.g., negative numbers, empty fields) so that my data stays accurate.

### 7. Accessibility

**US-7.1:** As a user, I want all interactive elements to be keyboard-navigable so that the app is usable without a mouse.

**US-7.2:** As a user, I want charts to include accessible labels and a tabular fallback so that screen reader users can access the data.

---

## Acceptance Criteria (Global)

- The app builds and runs with no errors.
- All vitals can be logged, viewed on the dashboard, charted, and listed in history.
- Alerts correctly flag out-of-range values based on default or custom thresholds.
- Data survives a full page refresh.
- The UI is responsive down to 375px viewport width.
