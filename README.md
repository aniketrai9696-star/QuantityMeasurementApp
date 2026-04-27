Here is your content **properly arranged and structured** in a clean, report-style format:

---

# 📘 Quantity Measurement — Java

A progressive Java implementation of a **Quantity Measurement system** that supports:

* Length unit comparisons
* Unit conversions
* Addition across multiple units

---

# 📁 Project Structure

```
quantity_measurement_fixed/
├── UC1.java – Feet equality
├── UC2.java – Feet & Inches same-unit equality
├── UC3.java – Cross-unit length equality (feet ↔ inches)
├── UC4.java – Extended units: Yards & Centimeters
├── UC5.java – Unit conversion utility (QuantityLengthConverter)
├── UC6.java – Addition of lengths (result in first operand's unit)
├── UC7.java – Addition with explicit target unit
├── UC8.java – Refactored: conversion logic inside LengthUnit enum
└── UC9.java – Weight measurement (Kilogram, Gram, Pound)
```

---

# ⚙️ Use Cases

## 🔹 UC1 — Feet Equality

Compare two `Feet` objects using `equals()` and `hashCode()`.

```java
Feet a = new Feet(1.0);
Feet b = new Feet(1.0);
a.equals(b); // true
```

---

## 🔹 UC2 — Same-Unit Equality (Feet & Inches)

Compare values within the same unit only.

```java
UC2.areEqualFeet(1.0, 1.0); // true
UC2.areEqualInches(1.0, 2.0); // false
```

---

## 🔹 UC3 — Cross-Unit Length Equality

Compare values across different units by converting to a base unit.

```java
UC3.areEqual(1.0, "feet", 12.0, "inches"); // true
UC3.areEqual(1.0, "feet", 2.0, "inches");  // false
```

---

## 🔹 UC4 — Extended Length Units

Supports Yards and Centimeters.

```java
UC4.areEqual(1.0, "YARDS", 3.0, "FEET");     // true
UC4.areEqual(1.0, "YARDS", 36.0, "INCHES");  // true
```

---

## 🔹 UC5 — Unit Conversion Utility

Convert between supported units.

```java
QuantityLengthConverter.convert(1.0, LengthUnit.FEET, LengthUnit.INCHES); // 12.0
QuantityLengthConverter.convert(1.0, LengthUnit.YARDS, LengthUnit.FEET);  // 3.0
```

---

## 🔹 UC6 — Length Addition (Implicit Unit)

Result is in the first operand's unit.

```java
QuantityLength.add(new QuantityLength(1.0, FEET),
                   new QuantityLength(12.0, INCHES)); // → 2.0 FEET

QuantityLength.add(new QuantityLength(12.0, INCHES),
                   new QuantityLength(1.0, FEET)); // → 24.0 INCHES
```

---

## 🔹 UC7 — Length Addition (Explicit Unit)

Specify output unit.

```java
QuantityLength.add(new QuantityLength(1.0, FEET),
                   new QuantityLength(12.0, INCHES), YARDS); // → 0.6667 YARDS

QuantityLength.add(new QuantityLength(1.0, INCHES),
                   new QuantityLength(1.0, INCHES), CENTIMETERS); // → 5.08 CM
```

---

## 🔹 UC8 — Enum-Driven Conversion

All conversion logic moved to `LengthUnit` enum.

```java
new QuantityLength(30.48, CENTIMETERS)
    .equals(new QuantityLength(1.0, FEET)); // true

new QuantityLength(1.0, YARDS).convertTo(FEET); // 3.0 FEET
```

---

## 🔹 UC9 — Weight Measurement

Supports Kilogram, Gram, Pound.

```java
new QuantityWeight(1.0, KILOGRAM)
    .equals(new QuantityWeight(1000.0, GRAM)); // true

new QuantityWeight(500.0, GRAM)
    .add(new QuantityWeight(500.0, GRAM), KILOGRAM); // → 1.0 KG
```

---

# 📏 Supported Units

## 🔸 Length Units

| Unit        | Enum Constant | Relative to Feet |
| ----------- | ------------- | ---------------- |
| Feet        | FEET          | 1.0              |
| Inches      | INCHES        | 1/12 ft          |
| Yards       | YARDS         | 3.0 ft           |
| Centimeters | CENTIMETERS   | 1/30.48 ft       |

---

## 🔸 Weight Units

| Unit     | Enum Constant | Relative to Kilogram |
| -------- | ------------- | -------------------- |
| Kilogram | KILOGRAM      | 1.0                  |
| Gram     | GRAM          | 1/1000 kg            |
| Pound    | POUND         | 0.45359237 kg        |

---

# 🧠 Design Principles

* **Base-unit normalization**
  All values converted to a base unit (feet/kg) before comparison

* **Floating-point safety**
  Uses `Double.compare()` or epsilon comparison

* **equals/hashCode consistency**
  Proper overriding for correctness

* **Immutability**
  Classes use final fields, no setters

* **Enum-driven conversion (UC8+)**
  Conversion logic centralized in enums

---

# ▶️ Compilation & Execution

### Compile:

```bash
javac quantity_measurement_fixed/*.java
```

### Run:

```bash
java -cp quantity_measurement_fixed UC1
java -cp quantity_measurement_fixed UC2
...
java -cp quantity_measurement_fixed UC9
```

---

# ⚠️ Requirements

* Java 17 or later
* No external dependencies for UC1–UC9
* JUnit 5 used only in UC5–UC7 tests

---

# 🐞 Bugs Fixed

| File    | Issue                                  |
| ------- | -------------------------------------- |
| UC1–UC4 | Incorrect class names                  |
| UC4     | Instance method used in static context |
| UC4     | Wrong class reference                  |
| UC5     | Missing converter methods              |
| UC6–UC7 | Missing getters and add()              |
| UC8     | Wrong centimeter conversion factor     |
| UC9     | Typo and incomplete equals()           |

---

This version is now **clean, readable, and ready for report submission or documentation**.

If you want, I can also:

* Convert this into a **PDF report**
* Add **diagrams / flowcharts**
* Or format it into a **college assignment template**

Just tell me 👍
