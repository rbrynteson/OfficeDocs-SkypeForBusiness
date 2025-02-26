---
title: View Microsoft Teams utilization in Power BI using CQD data
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: siunies, jamp
ms.date: 12/16/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
description: Use the Teams Usage Power BI reports to access Microsoft Teams Call Quality Dashboard (CQD) data to track Microsoft Teams usage in your organization.
---

# View Microsoft Teams utilization in Power BI using CQD data

The Teams Usage report is available as part of our downloadable [Power BI query templates for CQD](https://www.microsoft.com/download/details.aspx?id=102291). 

This report lets you see how (and how much) your users are using Microsoft Teams by accessing Teams Call Quality Dashboard (CQD) data. These reports are intended to be a centralized location that both administrators and business leaders can quickly go to for this data. We advise [not relying on this data for concrete numbers due to the nature of call quality telemetry](CQD-frequently-asked-questions.md#im-trying-to-use-cqd-for-usage-type-reports-and-find-that-some-of-the-data-is-incomplete----why-is-that).

The Teams Usage Power BI report consists of two primary reports: **[Call Count Summary](#call-count-summary-report)** and **[Audio Minutes Summary](#audio-minutes-summary-report)**. The [Daily Usage](#daily-usage), [Regional Audio Details](#regional-audio-details), [Conference Details](#conference-details), and [User List](#user-list) reports come into play when a user takes advantage of the drill-down reports, as detailed later in this article. For best results, ensure that your tenant has the latest [building and subnet data](cqd-upload-tenant-building-data.md) uploaded so that you can use regional and network filtering capabilities.

> [!NOTE]
> We recommend using our new Quality of Experience Report (QER) for for viewing your Teams CQD data in Power BI. While the Teams Usage report is still supported, only the QER will receive new updates and coverage for the latest Teams features and calling scenarios. If you haven't tried the QER, it is also available in the same downloadable [Power BI query templates for CQD](https://www.microsoft.com/download/details.aspx?id=102291) package as the Teams Usage report.


## Call Count Summary Report

The main page, Call Count Summary, immediately provides the number of audio, video, and screen sharing sessions over the last 30 and 90 days as noted in the section title. The data initially displayed is for the organization as a whole. You can filter the data by using the slicer dropdown options on the left side of the page.

![Screenshot of Call Count Summary report in Teams Usage Reports.](media/CQD-teams-utilization-report1.png)

1. To the right of the slicer dropdowns, the number of calls by media type is broken down to an internal/external view over the past 30 days. We can see through the above screenshot that there are more calls happening from outside organizational locations.
  ![Screenshot of Monthly Call Count by Media Type for the last 90 days in Teams Usage Reports.](media/CQD-teams-utilization-report2.png)

1. To the right of the media type count box, we have the Monthly Call Count by Media Type for the last 90 days. You can display the count for a previous month or the current month to date, providing usage trend information.
  ![Screenshot of Daily Call Count by Media Type for the past 30 days in Teams Usage Reports.](media/CQD-teams-utilization-report3.png)

1. The middle graph functions as the 90-day graph does, however it provides a daily usage view for the past 30 days and allows a user to select and drill down into details for a specific day.
  ![Screenshot of Daily Call Count by Media Type for the past 30 days drill-down in Teams Usage Reports.](media/CQD-teams-utilization-report4.png)

On the bottom left section of the page, you can find a table providing total values for each media type over the past year. 
    ![Screenshot of table drillthrough providing total values for each media type over the past year in Teams Usage Reports.](media/CQD-teams-utilization-report5.png)
    ![Screenshot of table providing total values for each media type over the past year in Teams Usage Reports.](media/CQD-teams-utilization-report6.png)   

To the right of the table, a bar chart shows clients with the most use (calls/streams) for the past 30 days.

   ![Screenshot of chart showing clients with the most use (calls/streams) for the past 30 days in Teams Usage Reports.](media/CQD-teams-utilization-report7.png)

The last set of charts for this page show each media type individually, with a breakdown showing conference and P2P usage. The charts below show that there is a significantly higher number of conference usages as compared to P2P.

  ![Screenshot of charts showing each media type individually, with a breakdown showing conference and P2P usage in Teams Usage Reports.](media/CQD-teams-utilization-report8.png)

## Audio Minutes Summary Report

The Audio Minutes usage report provides the total minute usage through a few different views. 

The thirty-day usage summary is shown next to the slicers as text boxes. The top number shows the thirty-day total, with internal and external breakdowns below that.

![Screenshot of Audio Minutes usage report in Teams Usage Reports.](media/CQD-teams-utilization-report9.png)

The top right bar graph provides a yearlong view of conference audio usage. Hover over the month to show the conference audio minutes.

To show the difference in P2P and conference audio, the bottom left chart takes all audio for the past year and breaks it up between the two types.

![Screenshot of all audio for the past year in Teams Usage Reports.](media/CQD-teams-utilization-report10.png)

The last chart for the Audio minutes page shows audio minute usage on a global map overlay. This chart only works if building and subnet data is uploaded to the tenant. You can drill into the pie chart overlay on the map, subsequently providing regional audio usage.

![Screenshot showing audio minute usage on a global map overlay in Teams Usage Reports.](media/CQD-teams-utilization-report11.png)


## Drillthrough capabilities

As previously noted, users can drillthrough the daily and regional usage reports.

### Daily Usage

The Daily Usage report allows an administrator to identify peak consumption periods through the course of a day. In addition to usage, we're also able to capture overall user sentiment and feedback for that day.

![Screenshot showing Daily Usage report in Teams Usage Reports.](media/CQD-teams-utilization-report12.png)

The Daily Usage report displays the number of Audio, Video, and Screen shares for the selected day with the added ability to differentiate between internal and external connectivity. A Conference and Peer to Peer breakdown is to the immediate right of the modality total box. The top right of the report provides a list of conferences with their associated ID and participants for the day. The conference list provides an additional drillthrough to the Conference Details report.

![Screenshot of Daily Call Count by media type for the past 30 days in Teams Usage Reports.](media/CQD-teams-utilization-report13.png)

The bar graph in the center area allows the user to identify peak consumption periods through the course of a day. Users can drill down into the hour represented on the graph, which presents the User List report for the hour.

To the right of the bar graph, User Feedback is presented in a visual format. User feedback provides insight that can be used to identify potential issues.

The bottom table provides a range of metrics for the day. Poor percentages along with failure rates can provide an administrator with potential areas of improvement. Each hour can also be selected individually as shown below.

This data can be used to identify regions having problems during peak consumption times.

Select the column for that day to display metrics for that hour.

![Screenshot of Hourly Trend by Media Type in Teams Usage Reports.](media/CQD-teams-utilization-report14.png)
  
  1.  The table below the chart displays the metrics for that hour. This table can be sorted by any column header. However, we would be interested in finding problematic areas.
    ![Screenshot of Hourly Trend by Media Type metrics in Teams Usage Reports.](media/CQD-teams-utilization-report15.png)
    
  1.  We see that the IND region is experiencing poor video performance in conferences during this time frame. After, the CQD QER Microsoft reports can be used to narrow down the problematic location as the region and time frame have been identified.

### Conference Details

The Conference Details report provides additional insight for meetings, from an attendee list, to the media types used during the session.

Select a conference from the participant bar in the conference ID chart on the Daily Usage page to drill down into the conference details.

![Screenshot of conference participant bar for Conference Details report in Teams Usage Reports.](media/CQD-teams-utilization-report24.png)

![Screenshot of Participant Count by Conference ID for Conference Details report in Teams Usage Reports.](media/CQD-teams-utilization-report25.png)

We can see the participants in the conference and all the pertinent information down to packet loss and jitter to assist with potential troubleshooting efforts in the bottom table.

![Screenshot of drill-down table for Conference Details report in Teams Usage Reports.](media/CQD-teams-utilization-report26.png)


### Regional Audio Details

The Regional Audio Details drill-down specifically shows the audio minute usage for the selected region. Users with access to CQD can see usage trends for both P2P and conference audio within the selected region.

1.  On the Call Count Summary page, drillthrough to a specific region through the table.
  ![Screenshot of Call Count Summary report drillthrough in Teams Usage Reports.](media/CQD-teams-utilization-report16.png)

1.  Select the row with the region that you need additional information on.
  ![Screenshot of region details in Call Count Summary report in Teams Usage Reports.](media/CQD-teams-utilization-report17.png)

1.  The data trends show a significant number of minutes being used on the internal network, with conferencing far surpassing P2P use.
  ![Screenshot of data trends in Call Count Summary report in Teams Usage Reports.](media/CQD-teams-utilization-report18.png)

The regional audio trend can be used to show how users are impacted by external influences in the world. Specifically, right now, we would expect to see the external usage for the EMEA and APAC regions to increase with people being asked to work remotely.

### User List

The User List drill-down provides user-specific information for a specific hour selected by the person viewing the report. The User List report is accessible through a drill-down in the Hourly Trends graph on the Daily Usage report. Right-click on the hour additional information is needed for and select Drill through and User List, as shown below.

![Screenshot of User List drill-down report in Teams Usage Reports.](media/CQD-teams-utilization-report19.png)

The User List report shows internal/external connectivity through the doughnut chart in the top center of the page. We can see that there is a large amount of participation from Outside the corporate network in the below image.

The top right of the graph shows the number of calls made by each user within that hour.

![Screenshot of User List drill-down table in Teams Usage Reports.](media/CQD-teams-utilization-report20.png)

The bottom table provides detailed information for the sessions each user participated in during that hour. The Failure Type column is useful in determining what caused a call to drop. The Capture and Render Device columns are useful in identifying why a call was reported having poor quality.


## Related topics

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md)

[Set up Skype for Business Call Analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Call Analytics and Call Quality Dashboard](./monitor-call-quality-qos.md)

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
