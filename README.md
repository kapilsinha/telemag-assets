```
████████╗███████╗██╗     ███████╗███╗   ███╗ █████╗  ██████╗ 
╚══██╔══╝██╔════╝██║     ██╔════╝████╗ ████║██╔══██╗██╔════╝ 
   ██║   █████╗  ██║     █████╗  ██╔████╔██║███████║██║  ███╗
   ██║   ██╔══╝  ██║     ██╔══╝  ██║╚██╔╝██║██╔══██║██║   ██║
   ██║   ███████╗███████╗███████╗██║ ╚═╝ ██║██║  ██║╚██████╔╝
   ╚═╝   ╚══════╝╚══════╝╚══════╝╚═╝     ╚═╝╚═╝  ╚═╝ ╚═════╝ 
```
# Telemag

**Telemag** improves visibility, accountability, and performance across your fleet. This guide covers best practices and essential setup information to help you get the most value from your reports.


## Farm managers use Telemag to make data-informed decisions

How?
- Quantify lost productivity in **acres/hour** and **dollars/day**
- Help back-office track and plan budgets in real-time (no more manual estimates!)
- Benchmark drivers, tractors, and crews to goal metrics (and to one another)
- Surface inefficiencies in field operations  


## Hardware Installation

Our devices connect directly to your equipment via the **J1939 diagnostic port**.

### Port Location (Common Examples)
- Lower right side of the operator station (knee level)
- Under the driver seat
- Outside the cab near the chassis (especially in older models)

If you're unsure where to plug in, contact us—we’re happy to help.  
> In some cases, a **weatherproof box** may be required to protect the device.


## Crew & Field Data Integration

We currently support:
- **HeavyConnect**
- **PetTiger**
- **KMZ/KML geofence (field boundary) files**

Please us send any relevant files and contacts



## Report Setup

We generate:
- **Daily reports** (delivered each morning)
- **Weekly summaries** (delivered Sundays)
- **Custom reports** (on request)

> **Please provide a list of email addresses** for everyone who should receive reports.


## Best Practices

### Use Reports as a Management Tool

- Review daily reports each morning to identify issues and recognize performance.
- Use weekly reports to spot trends, crew variability, or recurring bottlenecks.
- Incorporate insights into team meetings or planning decisions.

### Keep Data Clean

- Let us know if you add or remove tractors, crews, or fields.
- Ensure we always have an up-to-date crew list and field boundaries.
- Mismatched or missing data limits the accuracy of our insights.

### Follow Up on Downtime or Low Output

- Use report insights to ask better questions.
- Track follow-ups: was a mechanical issue resolved? Was the crew slowed by external factors?

### Adjust Based on Patterns

- Evaluate performance by task, crop, or tractor type.
- Rotate crews or shift assignments based on measurable output.
- Use Telemag as a tool to fine-tune decision-making.


## Technical Details
These are up-to-date as of July 23, 2025. These details may change without notice. 

### Shift Timings
* Shift timings: By default, we call 6 am - 6 pm PT the "day shift" and 6 pm - 6 am the "night shift". Contact us if you would like that changed

### Metrics
* downtime = sum of stop durations
  - A tractor is considered **stopped** if the speed drops below 0.2 mph for over 30 seconds
* uptime = engine hours - downtime
* Calculating cost / acre: our formula is a function of labor hours (payroll), engine hours (equipment depreciation and maintenance), and fuel used (fuel costs). The formula is written on our daily reports.
* Calculating acres: we developed a proprietary algorithm to compute acres covered by analyzing the machine's GPS trajectory.
  - Empirically, the algorithm works well across many operations and implements
  - If your implement is particularly narrow, please let us know and we will configure our algorithm differently


### Geofencing
If you provided us geofence files, we use them to populate ranch and field and potentially split the daily reports per ranch/field. This is our high-level procedure to do so:
1. Determine which ranch + fields were worked. We determine a field was worked if the equipment was on that field for at least 30 minutes.
2. If more than one ranch + field was worked, split the work into time intervals corresponding to each field. There is some logic to denoise this segmentation (e.g. a tractor moves along the road between two fields).
3. Generate a report per field.

Notes:
1. If you see the machine being transported on a report, that is likely because there was only one field worked. Hence after step 1, we determine that we will generate only one report for the shift.
2. Reports with "insufficient data" (typically less than 30 min of runtime) are skipped.


## Troubleshooting
In general, email us at [evan@gotelemag.com](mailto:evan@gotelemag.com). If you need attention the same day, please text/call us (you have our number).

### How to Add a Missed or Corrected Shift
We allow users to backfill or edit shifts that were missed or logged incorrectly.

### Easiest Way to Update:
- Email us with:
  - Operator name  
  - Date  
  - Time in / time out  
  - Operation performed  
  - Assigned equipment (if applicable)

We’ll update the system and regenerate your report if needed.

### Report Looks Off?

- Double-check tractor assignments and shift times.
- Ensure the operator was properly checked in for the day.
- Reach out and we’ll help investigate.



Thanks for using Telemag. 

