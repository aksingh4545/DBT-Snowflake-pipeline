

<h1>MovieLens Data Pipeline Tutorial Web App</h1>

<img src="https://via.placeholder.com/800x200?text=MovieLens+Pipeline+Diagram" alt="Pipeline Diagram"> <!-- Placeholder for a banner image; replace with actual if available -->

<h2>Overview</h2>

<p>This repository contains a static web application that serves as a comprehensive, interactive tutorial for building a data pipeline using the MovieLens dataset. The pipeline integrates Amazon S3 for storage, Snowflake for data warehousing, dbt (data build tool) for transformations, and Power BI for visualization.</p>

<p>The web app is designed to be beginner-friendly yet detailed enough for experienced data engineers. It explains <strong>how to use</strong> each component (step-by-step commands and configurations) and <strong>how it works</strong> (underlying concepts, best practices, and troubleshooting). The tutorial covers the entire workflow from loading raw CSV data to creating analytics-ready tables and connecting to BI tools.</p>

<p>Key features:</p>
<ul>
    <li><strong>Interactive Code Examples</strong>: Code blocks with syntax highlighting and a "Copy" button for easy pasting into your environment.</li>
    <li><strong>Navigation Menu</strong>: Jump to sections like Snowflake Setup, dbt Materializations, or Power BI Connection.</li>
    <li><strong>Visual Aids</strong>: Diagrams, notes, and explanations to make complex topics accessible.</li>
    <li><strong>Real-World Focus</strong>: Includes common errors, fixes, and advanced topics like incremental loading and SCD Type 2.</li>
</ul>

<p>This project is ideal for:</p>
<ul>
    <li>Learning data engineering with modern tools.</li>
    <li>Building a resume-worthy portfolio project.</li>
    <li>Understanding ELT (Extract, Load, Transform) pipelines.</li>
</ul>

<p>The web app is built as a single <code>index.html</code> file using HTML, CSS, JavaScript, and Prism.js for code highlighting. No backend server is required—simply open it in a browser.</p>

<h2>Table of Contents</h2>

<ul>
    <li><a href="#overview">Overview</a></li>
    <li><a href="#prerequisites">Prerequisites</a></li>
    <li><a href="#installation">Installation</a></li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#project-structure">Project Structure</a></li>
    <li><a href="#features">Features</a></li>
    <li><a href="#how-the-pipeline-works">How the Pipeline Works</a></li>
    <li><a href="#troubleshooting">Troubleshooting</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
</ul>

<h2 id="prerequisites">Prerequisites</h2>

<p>To follow the tutorial and set up the pipeline yourself:</p>
<ul>
    <li><strong>Snowflake Account</strong>: Free trial available at <a href="https://snowflake.com">snowflake.com</a>.</li>
    <li><strong>Amazon S3 Bucket</strong>: With MovieLens CSV files (download from <a href="https://grouplens.org/datasets/movielens/">grouplens.org/datasets/movielens</a>).</li>
    <li><strong>Python 3.x</strong>: For dbt installation.</li>
    <li><strong>AWS Credentials</strong>: For S3 access.</li>
    <li><strong>Power BI Desktop</strong>: Free download from <a href="https://powerbi.microsoft.com/desktop">Microsoft</a>.</li>
    <li><strong>Browser</strong>: Modern browser like Chrome or Firefox to view the web app.</li>
</ul>

<p>No prerequisites are needed to view the web app itself.</p>

<h2 id="installation">Installation</h2>

<ol>
    <li>Clone the repository:
        <pre><code>git clone https://github.com/yourusername/movielens-pipeline-tutorial.git</code></pre>
    </li>
    <li>Navigate to the project directory:
        <pre><code>cd movielens-pipeline-tutorial</code></pre>
    </li>
    <li>Open <code>index.html</code> in your browser:
        <ul>
            <li>Double-click the file, or</li>
            <li>Use a local server (optional for better experience): <code>python -m http.server</code> and visit <a href="http://localhost:8000">http://localhost:8000</a>.</li>
        </ul>
    </li>
</ol>

<p>If you want to customize or extend the app:</p>
<ul>
    <li>Edit <code>index.html</code> directly.</li>
    <li>The app uses CDN links for Prism.js (syntax highlighting) and no external dependencies beyond that.</li>
</ul>

<h2 id="usage">Usage</h2>

<h3>Viewing the Web App</h3>
<ul>
    <li>Open <code>index.html</code> in a browser.</li>
    <li>Use the navigation menu to jump to sections.</li>
    <li>Hover over code blocks to reveal the "Copy" button—click to copy code to your clipboard.</li>
    <li>Follow the steps sequentially to build the pipeline in your own environment.</li>
</ul>

<h3>Building the Pipeline</h3>
<p>The tutorial guides you through:</p>
<ol>
    <li><strong>Snowflake Setup</strong>: Creating roles, users, warehouses, databases, stages, and loading raw data from S3.</li>
    <li><strong>dbt Setup</strong>: Installing dbt, initializing a project, connecting to Snowflake, and building models.</li>
    <li><strong>Transformations</strong>: Staging models (views), dev models (tables/incremental), and using packages like dbt_utils.</li>
    <li><strong>Power BI Integration</strong>: Connecting to Snowflake and querying transformed tables.</li>
    <li><strong>Advanced Topics</strong>: Materializations, error fixes, and next steps like adding tests or SCD.</li>
</ol>

<p>Example: To load movies data in Snowflake (from the tutorial):</p>
<pre><code class="language-sql">CREATE OR REPLACE TABLE raw_movies (
  movieId INTEGER,
  title STRING,
  genres STRING
);
COPY INTO raw_movies
FROM @netflixstage/movies.csv
FILE_FORMAT = (
  TYPE = 'CSV'
  SKIP_HEADER = 1
  FIELD_OPTIONALLY_ENCLOSED_BY = '"'
);</code></pre>

<h2 id="project-structure">Project Structure</h2>

<pre>
movielens-pipeline-tutorial/
├── index.html       # The main web app file (HTML, CSS, JS embedded)
├── README.md        # This file
└── (optional) assets/  # Add images or other static files if needed
</pre>

<ul>
    <li><strong>index.html</strong>: Contains all content, styles, and scripts. It's self-contained for easy sharing.</li>
</ul>

<h2 id="features">Features</h2>

<ul>
    <li><strong>Interactive Elements</strong>: Copyable code with Prism syntax highlighting for SQL, Bash, etc.</li>
    <li><strong>Sectioned Layout</strong>: Modular sections with headers, steps, notes, and diagrams.</li>
    <li><strong>Educational Depth</strong>: Explains "why" behind each step, including best practices (e.g., least privilege permissions, layering in dbt).</li>
    <li><strong>Visual Enhancements</strong>: ASCII diagrams for pipeline flow; notes for tips and warnings.</li>
    <li><strong>Extensibility</strong>: Easy to add more sections or JavaScript features (e.g., search functionality).</li>
</ul>

<h2 id="how-the-pipeline-works">How the Pipeline Works</h2>

<h3>High-Level Architecture</h3>
<ul>
    <li><strong>Source</strong>: Raw CSV files in S3 (movies.csv, ratings.csv, etc.).</li>
    <li><strong>Ingestion</strong>: Snowflake stage connects to S3; <code>COPY INTO</code> loads data into RAW schema tables.</li>
    <li><strong>Transformation</strong>: dbt models clean (staging views) and transform (dev tables) data. Uses materializations like views for staging and incremental for facts.</li>
    <li><strong>Consumption</strong>: Power BI connects to DEV schema for querying and dashboards.</li>
</ul>

<h3>Data Flow Diagram</h3>
<pre>
S3 CSV Files → Snowflake Stage → RAW Tables (untouched source)
                     ↓ (dbt run)
Staging Views (cleaning: rename, cast types)
                     ↓ (refs in models)
Dev Tables (analytics: facts, dims, aggregates)
                     ↓
Power BI Dashboards (visuals: top movies, ratings trends)
</pre>

<h3>Key Concepts</h3>
<ul>
    <li><strong>Security</strong>: Roles (ACCOUNTADMIN, TRANSFORM) and service users (dbt) for controlled access.</li>
    <li><strong>Scalability</strong>: Warehouses for compute; incremental models for large datasets.</li>
    <li><strong>Best Practices</strong>: Separate schemas (RAW, STAGING, DEV); validate loads; use dbt packages for macros.</li>
</ul>

<h2 id="troubleshooting">Troubleshooting</h2>

<p>Common issues covered in the app:</p>
<ul>
    <li><strong>dbt Adapter Mismatch</strong>: Edit <code>profiles.yml</code> to remove old configs (e.g., Databricks remnants).</li>
    <li><strong>Connection Failures</strong>: Run <code>dbt debug</code> from the project folder; ensure role/warehouse match.</li>
    <li><strong>Package Errors</strong>: Create <code>packages.yml</code> and run <code>dbt deps</code> for dbt_utils.</li>
    <li><strong>Power BI</strong>: Use correct server URL (without https://) and DEV schema only.</li>
</ul>

<p>For web app issues: Ensure browser supports modern JS; check console for errors.</p>

<h2 id="contributing">Contributing</h2>

<p>Contributions welcome! Fork the repo and submit a pull request.</p>
<ul>
    <li>Add new sections (e.g., Airflow scheduling).</li>
    <li>Improve diagrams or add real screenshots.</li>
    <li>Fix typos or enhance explanations.</li>
</ul>

<p>Please follow standard GitHub flow.</p>

<h2 id="license">License</h2>

<p>This project is licensed under the MIT License. See <a href="LICENSE">LICENSE</a> for details.</p>

<hr>

</body>
</html>
