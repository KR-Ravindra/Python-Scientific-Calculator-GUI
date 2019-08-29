# Welcome, this is a project implementing GUI and Some random libraries of Python.
---

`

from tkinter import *

from math import log, sqrt, exp, ceil, floor
from math import degrees, radians,pi
from math import asin, acos, atan
from math import sin, cos, tan


input_list = []

def on():
	"""
	# Method is called when ON is clicked
	# Sets display to '0'
	# Clears input_list
	"""

	global input_list

	input_list = []

	equation.set("0")

def display_input(input_list):
	"""
	# Returns input expression in string format
	"""

	input_string = ""

	for input_value in input_list:
		input_string += input_value

	return input_string

def new_input(input):
	"""
	# Called when a button is pressed
	"""
	global input_list
	
	input_list.append(input)

	input_string = display_input(input_list)

	input_string = input_string.replace('asin', 'sin-1').replace('acos', 'cos-1').replace('atan', 'tan-1').replace('**' , '^').replace('*' , 'x').replace('/' , '÷')

	equation.set(input_string)

def evaluate():
	"""
	# Called when '=' is pressed
	"""
	global input_list
	
	try:
		eval_exp = eval( display_input(input_list))

		equation.set(eval_exp)

		input_list = []

		new_input(str(eval_exp))		
		
	except:
		equation.set("syntax error")
		input_list=[]

def delete():
	"""
	# Called when DEL is pressed
	"""
	global input_list

	if input_list:
		input_list.pop()

	input_string = display_input(input_list)

	input_string = input_string.replace('asin', 'sin-1').replace('acos', 'cos-1').replace('atan', 'tan-1').replace('**' , '^').replace('*' , 'x').replace('/' , '÷')

	equation.set(input_string)

	
def all_clear():
	"""
	# Called when DEL is pressed
	"""
	global input_list

	input_list = []

	equation.set("0")

def rad_to_deg():
	"""
	# Called when Degrees is pressed
	# Converts radians to degrees
	"""
	global input_list
	
	rad_value = equation.get()
	
	rad_value = float(rad_value)
	
	deg_value = degrees(rad_value)
	
	input_list = []
	
	equation.set(deg_value)
	
	new_input(str(deg_value))
	
def deg_to_rad():
	"""
	# Called when Radians is pressed
	# Converts degrees to radians
	"""
	global input_list
	
	deg_value = equation.get()
	
	deg_value = float(deg_value)
	
	rad_value = radians(deg_value)
	
	input_list = []
	
	equation.set(rad_value)
	
	new_input(str(rad_value))
	

	
	
root=Tk()
root.title("Scientific Calculator")

var=IntVar()

equation=StringVar()

text_box=Entry(root,justify=LEFT,bg="grey",fg="black",width=38,font="Times 16 bold",textvariable=equation)
text_box.grid(row=0,column=0,padx=10,pady=10,columnspan=8)


	

Button(root,text="log",width=2,bg="black",fg="White",command=lambda:new_input("log(")).grid(row=1,column=0,padx=1,pady=1)
Button(root,text="(",width=2,bg="black",fg="white",command=lambda:new_input("(")).grid(row=1,column=1,padx=1,pady=1)
Button(root,text=")",width=2,bg="black",fg="white",command=lambda:new_input(")")).grid(row=1,column=2,padx=1,pady=1)
Radiobutton(root,text="Degree",variable=var,value=1,command=rad_to_deg).grid(row=1,column=3,padx=1,pady=1)
Radiobutton(root,text="Radian",variable=var,value=2,command=deg_to_rad).grid(row=1,column=4,padx=1,pady=1)
Button(root,text="ON",width=2,bg="grey",fg="white",command=on).grid(row=1,column=5,padx=1,pady=2)
Button(root,text="sin",width=2,bg="black",fg="white",command=lambda:new_input("sin(")).grid(row=2,column=0,padx=1,pady=4)
Button(root,text="cos",width=2,bg="Black",fg="White",command=lambda:new_input("cos(")).grid(row=2,column=1,padx=1,pady=4)
Button(root,text="sin-1",width=2,bg="black",fg="white",command=lambda:new_input("asin(")).grid(row=2,column=3,padx=1,pady=4)
Button(root,text="tan",width=2,bg="black",fg="white",command=lambda:new_input("tan(")).grid(row=2,column=2,padx=1,pady=4)
Button(root,text="cos-1",width=2,bg="black",fg="white",command=lambda:new_input("acos(")).grid(row=2,column=4,padx=1,pady=4)
Button(root,text="tan-1",width=2,bg="black",fg="white",command=lambda:new_input("atan(")).grid(row=2,column=5,padx=1,pady=4)
Button(root,text="sqrt",width=2,bg="black",fg="white",command=lambda:new_input("sqrt(")).grid(row=3,column=0,padx=1,pady=2)
Button(root,text="pi",width=2,bg="black",fg="white",command=lambda:new_input("pi")).grid(row=3,column=1,padx=1,pady=2)
Button(root,text="ex",width=2,bg="black",fg="white",command=lambda:new_input("exp(")).grid(row=3,column=2,padx=1,pady=2)
Button(root,text="abs",width=2,bg="black",fg="white",command=lambda:new_input("abs(")).grid(row=3,column=3,padx=1,pady=2)
Button(root,text="ceil",width=2,bg="black",fg="white",command=lambda:new_input("ceil(")).grid(row=3,column=4,padx=1,pady=2)
Button(root,text="floor",width=2,bg="black",fg="white",command=lambda:new_input("floor(")).grid(row=3,column=5,padx=1,pady=2)



Button(root,text="7",width=2,bg="grey",fg="white",command=lambda:new_input("7")).grid(row=4,column=0,padx=1,pady=2)
Button(root,text="8",width=2,bg="grey",fg="white",command=lambda:new_input("8")).grid(row=4,column=1,padx=1,pady=2)
Button(root,text="9",width=2,bg="grey",fg="white",command=lambda:new_input("9")).grid(row=4,column=2,padx=1,pady=2)
Button(root,text="4",width=2,bg="grey",fg="white",command=lambda:new_input("4")).grid(row=5,column=0,padx=1,pady=2)
Button(root,text="5",width=2,bg="grey",fg="white",command=lambda:new_input("5")).grid(row=5,column=1,padx=1,pady=2)
Button(root,text="6",width=2,bg="grey",fg="white",command=lambda:new_input("6")).grid(row=5,column=2,padx=1,pady=2)
Button(root,text="1",width=2,bg="grey",fg="white",command=lambda:new_input("1")).grid(row=6,column=0,padx=1,pady=2)
Button(root,text="2",width=2,bg="grey",fg="white",command=lambda:new_input("2")).grid(row=6,column=1,padx=1,pady=2)
Button(root,text="3",width=2,bg="grey",fg="white",command=lambda:new_input("3")).grid(row=6,column=2,padx=1,pady=2)
Button(root,text="0",width=2,bg="grey",fg="white",command=lambda:new_input("0")).grid(row=7,column=0,padx=1,pady=2)



Button(root,text="DEL",width=2,bg="red",fg="white",command=delete).grid(row=4,column=3,padx=1,pady=2)
Button(root,text="AC",width=2,bg="red",fg="white",command=all_clear).grid(row=4,column=4,padx=1,pady=2)
Button(root,text="OFF",width=2,bg="red",fg="white",command=root.destroy).grid(row=4,column=5,padx=1,pady=2)
Button(root,text="x",width=2,bg="grey",fg="white",command=lambda:new_input("*")).grid(row=5,column=3,padx=1,pady=2)
Button(root,text="÷",width=2,bg="grey",fg="white",command=lambda:new_input("/")).grid(row=5,column=4,padx=1,pady=2)
Button(root,text="^",width=2,bg="grey",fg="white",command=lambda:new_input("**")).grid(row=5,column=5,padx=1,pady=2)
Button(root,text="+",width=2,bg="grey",fg="white",command=lambda:new_input("+")).grid(row=6,column=3,padx=1,pady=2)
Button(root,text="-",width=2,bg="grey",fg="white",command=lambda:new_input("-")).grid(row=6,column=4,padx=1,pady=2)
Button(root,text="//",width=2,bg="grey",fg="white",command=lambda:new_input("//")).grid(row=6,column=5,padx=1,pady=2)
Button(root,text=".",width=2,bg="grey",fg="white",command=lambda:new_input(".")).grid(row=7,column=1,padx=1,pady=2)
Button(root,text="%",width=2,bg="grey",fg="white",command=lambda:new_input("%")).grid(row=7,column=2,padx=1,pady=2)
Button(root,text=",",width=2,bg="grey",fg="white",command=lambda:new_input(",")).grid(row=7,column=3,padx=1,pady=2)
Button(root,text="=",width=10,bg="grey",fg="white",command=evaluate).grid(row=7,column=4,rowspan=1,columnspan=2,padx=1,pady=2)

root.mainloop()


`

You can reach me at [LinkedIn](https://www.linkedin.com/in/krajaravindra)
