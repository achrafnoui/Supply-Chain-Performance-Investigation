## How I Got Into This Shit

I got the idea while searching for a PwC Job Simulation. I came across an analyst named Phan Chenh from Australia. At first, I downloaded her portfolio project from GitHub: **Tracking Trends in Supply Chain – A Sales and Profit Review (2015–2017)**.

When I looked through her PDF report and Power BI dashboard, I was amazed. At the same time, I realized how inexperienced I was compared with someone who had done the real work. I studied the report and dashboard for a while, then asked myself: *Why can't I replicate what she did?* I already had the dataset link, so I decided to give it a shot.

That first attempt hit me with the full force of messy-data hell. It was my first time working with a supply chain dataset, and I was staring at 53 columns and more than 180K rows without knowing what to do. I took a sample of the dataset, fed it to ChatGPT alongside the original portfolio files from GitHub, and asked for a step-by-step plan to reproduce the project's output.

The result wasn't what I needed. It felt too much like taking shortcuts, and I still didn't understand how to transform the messy source data into a polished, portfolio-level project. I gave up on the project several times because I couldn't figure out how to bridge that gap.

On my latest attempt to get the project moving, I gave myself a reminder: *“You know the drill. You know the way. Stay disciplined, take it step by step, and you'll get through it.”* That talk reignited the fire in me and kicked off the next phase of the project.

## The Data Modeling Phase

After loading the messy CSV dataset into pandas, I immediately ran into a strange error. Pandas couldn't read the file because of an encoding issue related to UTF-8. After asking ChatGPT for help, I learned that the source file used a different encoding. I changed the import setting to `encoding="latin-1"`, and that fixed the problem.

The next challenge was figuring out which columns belonged in fact tables and which belonged in dimension tables. I used `raw_data.columns.to_list()` to list all the column names and get a clearer picture of the data I had to work with.

I noticed that the column names contained spaces and inconsistent capitalization, so I standardized them into `snake_case`: lowercase words separated by underscores. That made selecting columns in pandas much easier.

Next, I exported the column list to Excel and manually drafted my first classification of the fact and dimension tables. I showed the draft to ChatGPT, and it looked like I had completed roughly 70% of the work. Since this was my first time doing supply chain analysis—and my first serious experience with messy data—I asked for help reviewing and finishing the classification.

After that, I created a Jupyter Notebook that loads `raw_data` and splits it into fact and dimension tables. It was exhausting. I tried to make the process easier with KNIME's drag-and-drop data modeling, but that went badly because I had never used KNIME before. So I returned to my old reliable combination: Jupyter Notebook and pandas.

Step by step, I made it through the process and exported the cleaned tables into separate CSV files. I also excluded some columns into `dim_trash` because they had very high numbers of null values.

## The Power BI Phase

At the beginning of this project, I kept one rule in mind: *“Before asking questions, visualize the data first. Understand what the hell is going on, then start the FBI-level investigation.”*

My goal for this phase is to build a Power BI report with four pages, each designed for a different audience:

1. **Operational Dashboard** — for team members.
2. **Analytical Dashboard** — for analysts.
3. **Tactical Dashboard** — for team managers.
4. **Strategic Dashboard** — for senior management.

The idea is to build one report that serves all four audiences, with each page focused on the decisions and questions relevant to that group.
