import math

def calculate_distance(x1, y1, x2, y2, target_unit="meters"):
  """Calculates 2D distance and converts it into the requested unit.

  Assumes the base grid coordinates (x, y) are measured in meters.
  """
  # 1. Calculate base distance in meters
  base_distance = math.sqrt((x2 - x1) ** 2 + (y2 - y1) ** 2)

  # 2. Define conversion rates relative to 1 Meter
  conversions = {
      "meters": 1.0,
      "kilometers": 0.001,
      "centimeters": 100.0,
      "cm": 100.0,
      "millimeters": 1000.0,
      "mm": 1000.0,
      "yards": 1.09361,
      "feet": 3.28084,
      "miles": 0.000621371,
      "inches": 39.3701,
  }

  unit = target_unit.lower().strip()

  if unit in conversions:
    converted_distance = base_distance * conversions[unit]
    return converted_distance, unit
  else:
    # Default fallback to meters if unit is unrecognized
    return base_distance, "meters"

# --- Example Usage ---
# Coordinates: Point A (0, 0) and Point B (5, 12)
x1, y1 = 0, 0
x2, y2 = 5, 12

# Calculate in Yards
dist_yd, unit_yd = calculate_distance(x1, y1, x2, y2, "yards")
print(f"Distance: {dist_yd:.2f} {unit_yd}")

# Calculate in Centimeters (cm)
dist_cm, unit_cm = calculate_distance(x1, y1, x2, y2, "cm")
print(f"Distance: {dist_cm:.2f} {unit_cm}")

# Calculate in Millimeters (mm)
dist_mm, unit_mm = calculate_distance(x1, y1, x2, y2, "mm")
print(f"Distance: {dist_mm:.2f} {unit_mm}")
