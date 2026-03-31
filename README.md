<div align="center">
  <h1>Analytics Platform Admin Dashboard</h1>
  <p>
    <img src="https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI" />
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
    <img src="https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge" alt="DAX" />
  </p>
</div>

<hr>

<h2>Overview</h2>
<p>This repository contains an end-to-end Business Intelligence project designed to track the adoption, engagement, and retention of users on a hypothetical SaaS Analytics Platform.</p>
<p>The project goes beyond standard data visualization by incorporating <strong>custom Python-based synthetic data engineering</strong> to simulate realistic user behaviors, funnel drop-offs, and feature adoption distributions. It also includes a <strong>Systems Architecture Proposal</strong> for securely handling document access within a BI environment.</p>

<hr>

<h2>Business Questions Answered</h2>
<p>The dashboard provides a "single-pane-of-glass" view for platform administrators, answering critical questions:</p>
<ul>
  <li><strong>Acquisition:</strong> Is the platform growing, and what is the demographic makeup of our users?</li>
  <li><strong>Engagement:</strong> How deeply are users engaging, and where do they drop off in the activation funnel?</li>
  <li><strong>Feature Adoption:</strong> Which features (EDA, Machine Learning, Reporting) drive the most value, and which are ignored?</li>
  <li><strong>Retention & Churn:</strong> Are users building a habit? How quickly do we lose them, and who is currently at risk?</li>
</ul>

<hr>

<hr>

<h2>Part 1: Dashboard Engineering & Analytics</h2>

<h3>1. Data Engineering (Python)</h3>
<p>To ensure the dashboard reflects realistic business scenarios, the dataset was generated using Python (<code>faker</code>, <code>random</code>, <code>datetime</code>).</p>
<ul>
  <li><strong>User Personas:</strong> Users are assigned hidden "personas" (Power, Standard, Casual) that dictate their session frequency and feature access, creating realistic engagement funnels.</li>
  <li><strong>Algorithmic Variance:</strong> Feature usage utilizes probability weights and seasonal modifiers (e.g., "Data Export" spikes in Q4) to avoid flat, unrealistic data distributions.</li>
</ul>

<h3>2. Data Modeling</h3>
<p>The data is structured in a highly optimized <strong>Star Schema</strong> to ensure efficient processing and straightforward DAX calculations:</p>
<ul>
  <li><strong>Dimensions:</strong> <code>dim_date</code>, <code>dim_user</code>, <code>dim_feature</code></li>
  <li><strong>Facts:</strong> <code>fact_sessions</code>, <code>fact_feature_usage</code>, <code>fact_retention</code></li>
</ul>

<h3>3. Advanced DAX & Analytics</h3>
<p>The dashboard utilizes over 20 custom DAX measures, highlighting advanced context transition and table manipulation:</p>
<ul>
  <li><strong>Cohort Analysis:</strong> Utilized disconnected parameter tables (<code>GENERATESERIES</code>) and the <code>INTERSECT()</code> function to build dynamic, week-by-week retention matrices.</li>
  <li><strong>Churn Tracking:</strong> Implemented rolling 30-day churn calculations using <code>DATESINPERIOD</code> and <code>EXCEPT()</code> logic.</li>
  <li><strong>Filter Context Management:</strong> Used <code>REMOVEFILTERS()</code> to ensure accurate feature adoption percentages across categorical matrix visuals.</li>
</ul>

<h3>4. Dashboard Layout</h3>
<p>The Power BI report is divided into four highly interactive pages navigated via a custom sidebar menu:</p>
<ol>
  <li><strong>Executive Overview:</strong> High-level KPIs (DAU, MAU, Stickiness) and demographic distributions.</li>
  <li><strong>User Engagement:</strong> Activation funnel analysis and session behavior tracking.</li>
  <li><strong>Feature Adoption:</strong> Deep-dives into specific tool usage, highlighting the drop-off between standard Reporting features and advanced Machine Learning features.</li>
  <li><strong>Retention & Churn:</strong> A dynamic Cohort Matrix and retention curves segmented by subscription tier.</li>
</ol>

<hr>

<h2>Part 2: Secure Document Architecture Proposal</h2>
<p>As part of solving complex BI challenges, this repository includes an architectural design document addressing a common enterprise requirement: <strong>Securely viewing documents (PDFs) within Power BI without exposing public URLs.</strong></p>
<p>The proposed architecture relies on the Microsoft Power Platform ecosystem:</p>
<ol>
  <li><strong>Storage (SharePoint Online):</strong> Documents are stored securely governed by Entra ID.</li>
  <li><strong>Integration (Power Apps):</strong> A custom Canvas App acts as a secure viewing portal.</li>
  <li><strong>Presentation (Power BI):</strong> The Power App is embedded in the dashboard, with Power BI passing Row-Level Security (RLS) filtered parameters to fetch only authorized documents.</li>
</ol>
<p><em>Read the full proposal in the <code>Secure Document Access.docx</code> file.</em></p>

<hr>

<hr>
<p align="center"><em>Created by Nikhil Gupta as a showcase of end-to-end Data Analytics and BI Architecture skills.</em></p>
