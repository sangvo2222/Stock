Code Plugin 1
//@version=5
indicator("SangChikin Value Line", overlay = false)

// Input fields for manual input of numbers
inputNumber1 = input.float(defval=1.0, title="Enter EPS/RPS/BVPS")
inputNumber2 = input.float(defval=1.0, title="Enter MAX Value")
inputNumber3 = input.float(defval=1.0, title="Enter MIN Value")
inputNumber4 = input.float(defval=1.0, title="Enter AVERAGE Value")

// Calculation: Price divided by the first input number
dividedPrice = close / inputNumber1
// Determine color based on the conditions
colorDividedPrice = dividedPrice > inputNumber2 ? color.red : 
     dividedPrice < inputNumber3 ? color.green : 
     (dividedPrice < inputNumber2 and dividedPrice > inputNumber4) ? color.orange : color.blue

// Plot the divided price with dynamic color
plot(dividedPrice, title="Enter EPS/RPS/BVPS", color=colorDividedPrice, linewidth=2, format=format.price, precision=2)

// Plot standard lines for inputNumber2, inputNumber3, and inputNumber4
plot(inputNumber2, title="Enter MAX Value", color=color.red, linewidth=1, style=plot.style_line, format=format.price, precision=2)
plot(inputNumber3, title="Enter MIN Value", color=color.orange, linewidth=1, style=plot.style_line, format=format.price, precision=2)
plot(inputNumber4, title="Enter AVERAGE Value", color=color.green, linewidth=1, style=plot.style_line, format=format.price, precision=2)

