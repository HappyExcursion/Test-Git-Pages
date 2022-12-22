An alternative way of constructing the buttons would be using for loops. The bottons in the passcode exercise all have the same size and shape, so it's possible to use for loops to create them.

Because buttons are arranged in rows, we can use a for loop for the rows:

	for i in range(3):
		# create the 3 buttons in one row
			for j in range(3):
				button= Button()
				button.grid(row=i, column=j)

The buttons don't have any text. To assign the appropriate number for each button, we need a way to track each buttons (*nth* button is being created). There're 3 buttons in a row, so for a given row, n (counter) should be i (counter for row, (0...2)) \* 3 + j + 1 (j starts at 0 so we need to add one to it):

	for i in range(3):
		# create the 3 buttons in one row
			for j in range(3):
				index = i\*3 + j + 1 
				button= Button(text = f"{index}")
				button.grid(row=i, column=j)
Here I'm using f string (formated string) to pass in the text parameter. It can also be achieved in other ways:
* text = str(index) # text takes a string so we need to convert the inteegr index into a string
* text = "{}".format(index)
f string is usually used when including a variable in a string in Python 3

That still leaves on important problem, the command function which the button press evokes. It'd be tempting to do:

	def btn_handler(num):
		print(num, end="", flush=True)
	for i in range(3):
		# create the 3 buttons in one row
			for j in range(3):
				index = i\*3 + j + 1 
				button= Button(text = f"{index}", command = btn_handler(index))
				button.grid(row=i, column=j)
Output:

	123456789