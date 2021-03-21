# Simple-Regression

  import matplotlib.pyplot as plt

  def read_file(filename):
      inputfile = open(filename)
      lines = inputfile.readlines()[1:]
      x = []
      y = []
      x2 = []
      y2 = []
      xy = []
      for line in lines:
          x.append(float(line.split(",")[0]))
          y.append(float(line.split(",")[1]))
          x2.append(float(line.split(",")[0]) ** 2)
          y2.append(float(line.split(",")[1]) ** 2)
          xy.append(float(line.split(",")[0]) * float(line.split(",")[1]))
      return [x, y, x2, y2, xy, len(lines)]

  filename = "car_data_2.txt"
  variables = read_file(filename)

  Ex = sum(variables[0])
  Ey = sum(variables[1])
  Ex2 = sum(variables[2])
  Ey2 = sum(variables[3])
  Exy = sum(variables[4])
  n = variables[5]

  a = (((Ey * Ex2) - (Ex * Exy)) / ((n * Ex2) - (Ex) ** 2))
  b = (((n * Exy) - (Ex * Ey)) / ((n * Ex2) - (Ex) ** 2))

  print("y = " + str(b) + "x + " + str(a))

  maxx = round(max(variables[0])) + 5


  plt.plot([0, maxx], [b, (maxx * b + a)])
  plt.scatter(variables[0], variables[1])
  plt.show()
