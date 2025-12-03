# Warden Darkness Coverage Planner

A visual calculator for optimally covering a Minecraft area with Warden darkness effects using a hexagonal grid pattern.

**Best values have been pre-configured.** Increasing overlap to 7 will increase the number of required zones, while decreasing overlap down to 1 doesn't reduce the zone count but does reduce coverage quality.

## What This Does

Calculates the optimal placement of Warden darkness effect zones (20-block radius) to cover a square Minecraft area. Uses a hexagonal offset grid pattern where every second row is shifted horizontally by half the spacing distance for efficient coverage.

## How to Download and Run Locally

1. **Download the file:**
   - Download `darkness-grid.html` from this repository
   - Save it anywhere on your computer

2. **Run the file:**
   - Double-click `darkness-grid.html` to open it in your web browser
   - Or right-click → Open With → choose your preferred browser
   - No installation, server, or internet connection required

## Inputs

- **Grid size** (default: 400)
  The area to cover in blocks (creates a square: gridSize × gridSize). Example: 400 = 400×400 block area.

- **Radius** (default: 21)
  The radius of the Warden darkness effect in blocks.

- **X overlap** (default: 6)
  How many blocks the effect zones overlap horizontally. Higher overlap = more coverage redundancy, more zones required.

- **Y overlap** (default: 6)
  How many blocks the effect zones overlap vertically. Higher overlap = more coverage redundancy, more zones required.

## Outputs

- **Req** (Required zones)
  Total number of Warden darkness effect zones needed to cover the entire area.

- **1st X**
  The horizontal offset from the **left edge** of the grid where the first effect zone center should be placed.

- **1st Y**
  The vertical offset from the **top edge** of the grid where the first effect zone center should be placed.

- **X Dist** (X Distance)
  Horizontal spacing between adjacent effect zone centers in the same row.

- **Y Dist** (Y Distance)
  Vertical spacing between rows of effect zone centers.

- **Nx × Ny**
  Grid dimensions: number of zones horizontally × number of zones vertically.

## Understanding the Hex Pattern

The calculator uses a hexagonal offset grid pattern:

1. **First row:** Centers start at `1st X`, spaced by `X Dist`
   - Example: If `1st X = 18.5` and `X Dist = 36`, first row centers are at x-positions: 18.5, 54.5, 90.5, 126.5...

2. **Second row:** Centers start at `1st X + (X Dist / 2)`, spaced by `X Dist`
   - This row is offset by **half** the X distance to create the hex pattern
   - Example: If `1st X = 18.5` and `X Dist = 36`, second row centers are at: 36.5, 72.5, 108.5...

3. **Rows alternate:** Odd rows (1st, 3rd, 5th...) use `1st X`, even rows (2nd, 4th, 6th...) use `1st X + (X Dist / 2)`

4. **Vertical spacing:** All rows are spaced by `Y Dist` starting from `1st Y`

## Example Usage

For a 400×400 block area with default settings (radius=21, overlaps=6):
- You'll need **121 zones** (11×11 grid)
- First zone center at coordinates (18.50, 18.50)
- Horizontal spacing: 36 blocks
- Vertical spacing: 36 blocks
- Second row starts at x=36.50 (shifted by 18 blocks, which is 36/2)

## Visualization

The canvas shows:
- **Black square:** Your grid area boundary
- **Cyan circles:** Effect zone coverage areas
- **Hex pattern:** Notice how circles in alternating rows are offset horizontally
