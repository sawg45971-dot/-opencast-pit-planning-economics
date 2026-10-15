# Opencast Pit Planning & Economics Study

An Excel model that takes a coal deposit from **borehole data to a go/no-go answer**: how much coal is in the pit, which blocks are worth mining, how many machines are needed, and what the project is worth (NPV).

> **Sample data only.** Every input is an illustrative value in a typical range. It is **not** data from any real mine. Replace the yellow cells with textbook or published figures to run your own case.

## Key result (sample dataset)

| Result | Value |
|---|---|
| Coal in place | 2.21 million t |
| Recoverable coal (economic blocks) | 1.69 million t |
| Break-even stripping ratio | 4.21 m³/t |
| Blocks worth mining | 16 of 20 |
| Fleet required | 2 excavators, 6 dumpers |
| All-in cost / profit per tonne | ₹1,989 / ₹211 |
| Mine life | 3.4 years |
| NPV (10% discount rate) | ₹19.1 crore |

**Verdict: viable on average**. The four blocks with the thickest overburden (A5, B5, C5, D5) have a stripping ratio above break-even and are left out of the pit.

![Summary sheet](screenshots/summary.png)

## What is in the workbook

| Sheet | Question it answers |
|---|---|
| **Inputs** | All assumptions in one place: block size, densities, machine specs, costs, coal price |
| **Reserve** | How much coal and overburden is there, and which blocks are economic (borehole-grid block method) |
| **Fleet** | How many excavators and dumpers does the production target need |
| **Economics** | Cost of removing overburden and winning coal, and the break-even stripping ratio |
| **Cash flow** | Year-by-year profit and NPV over the mine life |
| **Summary** | All key results on one page |

Every number is a live formula, so changing an input recalculates everything. Colour code: blue text on yellow = input, black = formula, green = pulled from another sheet.

## Method

1. **Inputs:** set the block size, densities, machine specs, costs and price.
2. **Reserve:** block volume = area × thickness; coal tonnes = coal volume × relative density; stripping ratio (SR) = overburden volume ÷ coal tonnes.
3. **Fleet:** excavator output = payload per pass × passes per hour; dumper output = payload per trip × trips per hour; machines = hours needed ÷ effective hours per machine, rounded up.
4. **Economics:** break-even SR = (price − coal winning cost) ÷ overburden removal cost. A block above this SR loses money, so it is excluded (the idea behind a pit limit).
5. **Cash flow:** yearly profit discounted to today; NPV = sum of discounted profits − non-equipment capital cost.

| | |
|---|---|
| ![Reserve sheet](screenshots/reserve.png) | ![Fleet sheet](screenshots/fleet.png) |

## How to use it

1. Open `Opencast_Pit_Planning_Economics_Starter.xlsx` in Excel, LibreOffice or Google Sheets.
2. Go through the sheets in the order above, starting with **Inputs**.
3. Replace the sample borehole thicknesses on **Reserve** and the yellow cells on **Inputs** with your own data.

Experiments to try:
- Raise coal price from ₹2,200 to ₹2,600/t. What happens to the break-even SR and the number of economic blocks?
- Double the overburden haul distance. How many more dumpers are needed, and why?
- Change the bucket from 4 m³ to 6 m³. Which numbers change and which do not?

## Limitations

- Flat-lying seam, one borehole per block, one seam only
- Constant average stripping ratio
- No pit slopes, ramps or benches
- No tax or depreciation (pre-tax NPV)
- Cash flow table covers 10 years; extend it if the mine life is longer
- Royalty and levy figures are placeholders; check current statutory rates
- Real mine planning uses software (e.g. Surpac, Datamine, Whittle) for 3D block models and optimised pit shells

## Tech

Microsoft Excel (formulas only, no macros).

