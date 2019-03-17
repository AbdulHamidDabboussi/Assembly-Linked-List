##	-	-IMPORTANT-	    -
##	The general structure;
##
##		-Main menu
##		-LinkedList creater
## 		-LinkedList displayer
## 		
##is given to you, necessary functions are empty, you have to ##fill them 
##	efficiently for lab3 part 1.
##	Necessary register defined. 	
##IF YOU READ INSTRUCTIONS CAREFULLY YOU FIGURE OUT THAT IT IS ##NOT DIFFICULT TO HANDLE
###############################################################

##

##	A program that calls linked list utility functions,

##		 depending on user selection.  The program outputs a 

##		message, then lists the menu options and get the user

##		selection, then calls the chosen routine, and repeats

##

##	a0 - used for input arguments to syscalls and for passing the 

##		pointer to the linked list to the utility functions

##	a1 - used for 2nd input argument to the utility functions that need it

##	a2 - used for 3rd input argument to the utility functions that need it

##	v0 - used for input and output values for syscalls

##	s0 - used to safely hold the pointer to the linked list

##	s1 - used to hold the user input choice of which menu option			


##   


##      linked list consists of 0 or more elements, in 


##		dynamic memory segment (i.e. heap)


##	elements of the linked list contain 2 parts:


##		at address z: pointerToNext element (unsigned integer), 4 bytes


##		at address z+4: value of the element (signed integer), 4 bytes


##

##

###################################################################

#
#					 	

#
#		text segment			

#
#						

#
####################################################################



	

	.text		
 	

	.globl _Lab3main
 


_Lab3main:		# execution starts here


	li $s0, 0	# initialize pointer storage register to 0 (=Null pointer)



	la $a0,msg110	# put msg110 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg110 string






##

##	Output the menu to the terminal,

##	   and get the user's choice

##

##



MenuZ:	
la $a0,msg111	# put msg111 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg111 string




	
la $a0,msg112	# put msg112 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg112 string




	
la $a0,msg113	# put msg113 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg113 string




	
la $a0,msg114	# put msg114 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg114 string




	
la $a0,msg115	# put msg115 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg115 string




	
la $a0,msg116	# put msg116 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg116 string




	
la $a0,msg117	# put msg117 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg117 string



	
la $a0,msg118	# put msg118 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg118 string
	
	
	
la $a0,msg1181	# put msg118 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg1181 string


la $a0,msg1182	# put msg118 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg1182 string
	
	
la $a0,msg1183	# put msg118 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg1183 string


EnterChoice:

	
la $a0,msg119	# put msg119 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg119 string




	li $v0,5	# system call to read  
	

	syscall		# in the integer


	move $s1, $v0	# move choice into $s1





##

##

##	T1 through T7no use an if-else tree to test the user choice (in $s1)

##	   and act on it by calling the correct routine

##

##



T1:	bne $s1,1, T2	# if s1 = 1, do these things. Else go to T2 test

	jal create_list

	move $s0, $v0	# put pointer to linked list in s0 for safe storage

	j MenuZ		# task is done, go to top of menu and repeat



T2:	bne $s1,2, T3	# if s1 = 2, do these things. Else go to T3 test

	move $a0, $s0	# put pointer to linked list in a0 before the call

	jal display_list 

	j MenuZ		# task is done, go to top of menu and repeat



T3:	bne $s1,3, T4	# if s1 = 3, do these things. Else go to T4 test

	
la $a0,msg200	# put msg200 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg120 string




	li $v0,5	# system call to read  
	

	syscall		#   in the integer


	move $a1, $v0	# put integer value into a1 before the call

	move $a0, $s0	# put pointer to linked list in a0 before the call

	jal AddNodes

	j ReportZ 



T4:	bne $s1,4, T5	# if s1 = 4, do these things. Else go to T5 test

	
la $a0,msg120	# put msg120 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg120 string




	li $v0,5	# system call to read  
	

	syscall		#   in the value

	move $a1, $v0	# put integer value into a1 before the call




	la $a0,msg124	# put msg124 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg124 string




	li $v0,5	# system call to read  
	

	syscall		#   in the position number

	move $a2, $v0	# put position number into a2 before the call



	move $a0, $s0	# put pointer to linked list in a0 before the call

	jal Insert_n

	move $s0, $v1	# put the (possibly revised) pointer into s0

	j ReportZ



T5:	bne $s1,5, T6	# if s1 = 5, do these things. Else go to T6 test

	
la $a0,msg125	# put msg125 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg125 string




	li $v0,5	# system call to read  
	

	syscall		#   in the position number

	move $a1, $v0	# put position number into a1 before the call

	move $a0, $s0	# put pointer to linked list in a0 before the call

	jal Delete_n

	move $s0, $v1	# put the (possibly revised) pointer into s0

	j ReportZ



T6:	bne $s1,6, T7	# if s1 = 6, do these things. Else go to T7 test

	
la $a0,msg126	# put msg126 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg126 string




	li $v0,5	# system call to read  
	

	syscall		#   in the value x

	move $a1, $v0	# put x value into a1 before the call

	move $a0, $s0	# put pointer to linked list in a0 before the call

	jal Delete_x

	move $s0, $v1	# put the (possibly revised) pointer into s0

	j ReportZ



T7:	bne $s1,7, T8	# if s1 = 7, do these things. Else go to T8 test


	la $a0,msg127	# put msg127 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the thank you string
	
	li $v0,10
	# the exit syscall is 10

	syscall		# goodbye...
	
	
	
T8:	bne $s1,8, T9	# if s1 = 8, do these things. Else go to T9 test

	
la $a0,msg201	# put msg126 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg126 string




	li $v0,5	# system call to read  
	

	syscall		#   in the value x

	move $a1, $v0	# put x value into a1 before the call

	move $a0, $s0	# put pointer to linked list in a0 before the call

	jal SwapNodes

	move $s0, $v1	# put the (possibly revised) pointer into s0

	j ReportZ



T9:	bne $s1,9, T10	# if s1 = 9, do these things. Else go to T10 test


	jal CountCommonValues


	j ReportZ



T10:	bne $s1,10, T7no	# if s1 = 10, do these things. Else go to T7no

	
la $a0,msg202	# put msg126 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg126 string




	li $v0,5	# system call to read  
	

	syscall		#   in the value x

	move $a1, $v0	# put x value into a1 before the call
	
	li $v0,5	# system call to read  
	

	syscall		#   in the value y

	move $a2, $v0	# put y value into a2 before the call

	move $a0, $s0	# put pointer to linked list in a0 before the call

	jal FindSumInRange

	move $s0, $v1	# put the (possibly revised) pointer into s0

	j ReportZ



T7no:	
la $a0,msg128	# put msg128 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg128 string

	j EnterChoice	# go to the place to enter the choice





##

##

##	ReportZ determines if the return value in $v0 is

##	   0 for success, -1 for failure, or other (invalid)

##

##



ReportZ: beq $v0,0,Succeed

	 beq $v0,-1,Fail



Invalid: la $a0,msg130  # put msg130 address into a0
	

	 li $v0,4	# system call to print
	

	 syscall	#   out the invalid message

	 j MenuZ	# task is done, go to top of menu and repeat

	

Succeed: la $a0,msg131  # put msg131 address into a0
	

	 li $v0,4	# system call to print
	

	 syscall	#   out the success message

	 j MenuZ	# task is done, go to top of menu and repeat



Fail:	 la $a0,msg132  # put msg132 address into a0
	

	 li $v0,4	# system call to print
	

	 syscall	#   out the failure message

	 j MenuZ	# task is done, go to top of menu and repeat

	
	






###################################################################

##

#### create_list - a linked list utility routine, 

##			which creates the contents, element 

##			by element, of a linked list

##

##	a0 - used for input arguments to syscalls

##	s0 - holds final value of pointer to linked list (to be put in v0 at exit)

##	t0 - temp value, holds # of current element being created; is loop control variable

##	t1 - temp value, holds n+1, where n is the user input for length of list

##	s1 - value of pointer to current element

##	s2 - value of pointer to previous element

##	v0 - used as input value for syscalls (1, 4, 5 and 9),

##		but also for the return value, to hold the address of the 

##		first element in the newly-created linked list

##	sp - stack pointer, used for saving s-register values on stack

##

##################################################################   




create_list:		# entry point for this utility routine

	

	addi $sp,$sp,-12 # make room on stack for 3 new items
	

	sw $s0, 8 ($sp) # push $s0 value onto stack
	

	sw $s1, 4 ($sp) # push $s1 value onto stack
	

	sw $s2, 0 ($sp) # push $s2 value onto stack
	

	



	la $a0, msg91	# put msg91 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg91 string

	



	la $a0, msg92	# put msg92 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg92 string

	



	li $v0,5	# system call to read  
	

	syscall		#   in the integer
	



	addi $t1,$v0,1	# put limit value of n+1 into t1 for loop testing

	



	bne $v0, $zero, devam90 #if n = 0, finish up and leave

	



	la $a0, msg93	# put msg93 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg93 string

	



	move $s0, $zero # the pointer to the 0-element list will be Null
	

	j Finish90	# 
	






devam90:		# continue here if n>0
	

	li $t0, 1	# t=1

	

	li $a0, 16	# get 16 bytes of heap from OS
	

	li $v0, 9	# syscall for sbrk (dynamic memory allocation)
	

	syscall
	



	move $s0, $v0	# the final value of list pointer is put in $s0
	

	move $s1, $v0	# the pointer to the current element in the list is put in $s1
	

	j Prompt90	# 
		




Top90:	move $s2, $s1	# pointer to previous element is updated with pointer to current element

	

	

	sll $t2,$t0,4	# $t2 is 16 x the number of the current element ($t0)
	

	move $a0, $t2	# get $t2 bytes of heap from OS
	

	li $v0, 9	# syscall for sbrk (dynamic memory allocation)
	

	syscall
	



	move $s1, $v0	# the pointer to the new current element in the list is put in $s1
	

	sw $s1, 0($s2)	# the previous element's pointerToNext is loaded with the new element's address

	



Prompt90: la $a0,msg94	# put msg94 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg94 string

	



	move $a0, $t0	# put x (the current element #) in $a0
	

	li $v0,1	# system call to print
	

	syscall		#   out the integer in $a0

	

	

	la $a0, msg95	# put msg95 address into a0
	

	li $v0,4	# system call to print
	

	syscall		#   out the msg95 string

	



	li $v0, 5	# system call to read in  
	

	syscall		#   the integer from user
	

	sw $v0, 4($s1) 	# store the value from user into

 
			#   current element's value part


	



	addi $t0,$t0,1	# x = x+1  increment element count
	

	bne $t0,$t1, Top90 # If x != n+1, go back to top of loop and iterate again


   
	

	sw $0,0($s1)	# Put Null value into pointerToNext part of last element in list

	





Finish90: move $v0,$s0	# put pointer to linked list in $v0 before return

	

	lw $s0, 8 ($sp) # restore $s0 value from stack
	

	lw $s1, 4 ($sp) # restore $s1 value from stack
	

	lw $s2, 0 ($sp) # restore $s2 value from stack
		

	addi $sp,$sp,12 # restore $sp to original value (i.e. pop 3 items)
	

	jr $ra		# return to point of call






##################################################################

#### display_list - a linked list utility routine, 

##			which shows the contents, element 

##			by element, of a linked list

##

##	a0 - input argument: points to the linked list, i.e. contains

##		the address of the first element in the list

##	s0 - current pointer, to element being displayed

##	s1 - value of pointerToNext part of current element

##	v0 - used only as input value to syscalls (1, 4, and 34)

##	sp - stack pointer is used, for protecting s0 and s1

##

################################################################# 

  



display_list:		# entry point for this utility routine

	

	addi $sp, $sp,-8 # make room on stack for 2 new items
	

	sw $s0, 4 ($sp) # push $s0 value onto stack
	

	sw $s1, 0 ($sp) # push $s1 value onto stack



	

	move $s0, $a0	# put the pointer to the current element in $s0
	



	la $a0, msg81	# put msg81 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg81 string

	



	bne $s0, $zero, devam80	# if pointer is NULL, there is no list

	



	la $a0, msg82	# put msg82 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg82 string
	

	j Return80	# done, so go home





devam80:		# top of loop	
	

	la $a0, msg83	# put msg83 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg83 string

	

	

	lw $s1, ($s0)	# read the value of pointerToNext
	

	move $a0, $s1	# put the pointerToNext value into a0
	

	li $v0, 34	# system call to print out the integer 
	

	syscall		#   in hex format

	



	la $a0, msg84	# put msg84 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg84 string

	



	lw $a0, 4($s0)	# read the value part, put into a0
	

	li $v0, 1	# system call to print  
	

	syscall		#   out the integer

	



	la $a0, msg85	# put msg85 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg85 string (new line)





Top80:	beq $s1, $zero, Return80 # if pointerToNext is NULL, there are no more elements

	

	

	la $a0, msg86	# put msg86 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg86 string

	



	move $s0, $s1	# update the current pointer, to point to the new element

	

	lw $s1, ($s0)	# read the value of pointerToNext in current element
	

	move $a0, $s1	# put the pointerToNext value into a0
	

	li $v0, 34	# system call to print out the integer 
	

	syscall		#   in hex format

	



	la $a0, msg84	# put msg84 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg84 string

	



	lw $a0, 4($s0)	# read the value part, put into a0
	

	li $v0, 1	# system call to print  
	

	syscall		#   out the integer

	



	la $a0, msg85	# put msg85 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		#   out the msg85 string (new line)

	



	j Top80		# go back to top of loop, to test and

 
			#   possibly iterate again





Return80:	
	

	la $a0, msg89	# put msg89 address into a0
	

	li $v0, 4	# system call to print
	

	syscall		# out the msg89 string

	



	lw $s0, 4 ($sp) # restore $s0 value from stack
	

	lw $s1, 0 ($sp) # restore $s1 value from stack
	

	addi $sp, $sp, 8 # restore $sp to original value (i.e. pop 2 items)
	

	jr $ra		# return to point of call







#################################################

##

##

##	

##

##

###############################################
#

### Fill Those functions
AddNodes:

	li $v0, -1
	move $t0, $a0	#current pointer
	
    loopAddNodes:
    	subi $a1, $a1, 1 #decrement counter
    	lw $t2, 0($t0) #next address
    	beqz $t2, exitAddNodes #end of list, exit
    	bgt $a1, $zero, movePointerAddNode
    	blt $a1, $zero, exitAddNodes #wrong input
    	lw $t1, 4($t0) #value of arr[n]
    	lw $t3, 4($t2) #value of arr[n+1]
    	add $t1, $t1, $t3 # arr[n] + arr[n+1]
    	sw $t1, 4($t0) #store
    	lw $t3, 0($t2) #next of next
    	sw $t3, 0($t0) #change pointer
    	li $v0, 0 #successful   		
    exitAddNodes:
	move $v1, $a0
	jr $ra #return
    movePointerAddNode:
    	lw $t0, 0($t0) #move current pointer to next
    	j loopAddNodes

SwapNodes:

	li $v0, -1
	subi $a1, $a1, 1 #off by one
	move $t0, $a0 #current pointer
	ble  $a1, -1, exitSwapNodes
	bnez $a1, loopSwapNodes #if not head, otherwise continue
	lw $t1, 0($a0) #swaps
	lw $t2, 0($t1)
	sw $t2, 0($a0)
	sw $a0, 0($t1)
	move $a0, $t1
	li $v0, 0 #successful
	j exitSwapNodes
    loopSwapNodes:
    	subi $a1, $a1, 1 #decrement counter
    	lw $t1, 0($t0) #next address
    	beqz $t1, exitSwapNodes
    	lw $t2, 0($t1) #next of next
    	beqz $t2, exitSwapNodes
    continueSwapNodes:
    	bnez $a1, fixSwapNodes
    	lw $t1, 0($t0) #swaps
	lw $t2, 0($t1)
	lw $t3, 0($t2)
	sw $t2, 0($t0)
	sw $t3, 0($t1)
    	sw $t1, 0($t2)
    	li $v0, 0
    	j exitSwapNodes
    fixSwapNodes: 
    	lw $t0, 0($t0) #incremet pointer
    	j loopSwapNodes
    exitSwapNodes:
	move $v1, $a0
	jr $ra
	
CountCommonValues:

	move $a2, $ra
	jal create_list
	move $t8, $v0 # pointer to head of first list
	jal create_list
	move $t9, $v0 #pointer to head of second list
	move $a0, $t9
	li $v0, 0 #counter
	move $ra, $a2
	
    for1:
    	lw $t0, 4($t8)
    	for2:
    		lw $t1, 4($t9)
    		bne $t1, $t0, skipAdd
    		addi $v0, $v0, 1
    	    skipAdd:
    		lw $t3, 0($t9)
    		beqz $t3, exitfor2
    		lw $t9, 0($t9)
    		j for2
    exitfor2:
    	lw $t3, 0($t8)
     	beqz $t3, exitfor1
 	lw $t8, 0($t8)
 	move $t9, $a0
 	j for1
	    	
    exitfor1:
	move $a0, $v0
	li $v0, 1
	syscall
	la $a0, msg85
	li $v0, 4
	syscall
	li $v0, 0
	jr $ra
	

Insert_n:

	li $v0, -1
	subi $a2, $a2, 1 #for the off by one error
	blt $a2, 1, exitInsert
	move $v1, $a0
	move $t0, $a0 #current pointer
	
    loopInsert:
	subi $a2, $a2, 1 #decrement counter
	lw $t2, 0($t0) #next address
    	beqz $t2, continueInsert #end of list, exit
    	bgt $a2, $zero, movePointerInsert
    continueInsert:
    	li $a0, 8 #allocate 8 bytes
    	li $v0, 9
    	syscall
    	move $t1, $v0 #pointer to new node
    	sw $t2, 0($t1) #next of new node
    	sw $a1, 4($t1) #value of new node
    	sw $t1, 0($t0) #next of current is new
    	li $v0, 0 #successful   
    exitInsert:
	jr $ra
    movePointerInsert:
    	lw $t0, 0($t0) #move current pointer to next
    	j loopInsert


Delete_n:

	li $v0, -1
	subi $a1, $a1, 1 #off by one
	move $t0, $a0 #current pointer
	ble  $a1, -1, exitDelete_n
	bnez $a1, loopDelete_n #if not head, otherwise continue
	lw $a0, 0($a0) #head.next
	j exitDelete_n
    loopDelete_n:
    	subi $a1, $a1, 1 #decrement counter
    	lw $t1, 0($t0) #next address
    	beqz $t1, exitDelete_n
    	lw $t2, 0($t1) #next of next
    	bnez $t2, continueDelete_n
    	sw $zero, 0($t0) #delete LAST element
    	li $v0, 0
    	j exitDelete_n
    continueDelete_n:
    	bnez $a1, fixPointerDelete_n
    	lw $t1, 0($t0) #next address
    	lw $t2, 0($t1) #next of next
    	sw $t2, 0($t0)
    	li $v0, 0
    	j exitDelete_n
    fixPointerDelete_n: 
    	lw $t0, 0($t0) #incremet pointer
    	j loopDelete_n
    exitDelete_n:
	move $v1, $a0
	jr $ra


FindSumInRange:

	li $v0, 0
	move $v1, $a0
	move $a3, $ra
	jal recurse
	move $a0, $v0
	li $v0, 1
	syscall
	la $a0, msg85
	li $v0, 4
	syscall
	li $v0, 0
	move $ra, $a3
	jr $ra
	
    recurse:
    	addi $sp, $sp, -8
    	sw $a0, 4($sp)
    	sw $ra, 0($sp)
    	#base case check
    	lw $t0, 0($a0)
    	bnez $t0, else
    	lw $t0, 4($a0) #value
    	blt $t0, $a1, continueRecurse
    	bgt $t0, $a2, continueRecurse
    	add $v0, $v0, $t0
    continueRecurse:
    	addi $sp, $sp, 8
    	jr $ra
    	
    else:
    	lw $a0, 0($a0)
    	jal recurse
    	lw $a0, 4($sp)
    	lw $t0, 4($a0) #value
    	blt $t0, $a1, skip
    	bgt $t0, $a2, skip
    	add $v0, $v0, $t0
    skip:
    	lw $ra, 0($sp)
    	addi $sp, $sp, 8
    	jr $ra
    	
    	
    	


Delete_x:
	li $v0, 0
	move $t0, $a0	#current pointer
	move $t1, $a0	#prev pointer
    deleteHead:
    	lw $t3, 4($t0)
    	bne $t3, $a1, fixpointer
    	lw $t3, 0($t0)
    	move $a0, $t3	#fix head
    	move $t0, $a0	#current pointer
	move $t1, $a0	#prev pointer
	addi $v0, $v0, 1 #counter++
	beqz $a0, exitDelete_x
	lw   $t3, 0($a0)
	beqz $t3, exitDelete_x
	j deleteHead
    fixpointer:
    	lw $t3, 0($t0)
    	beqz $a0, exitDelete_x
    	move $t0, $t3	#current pointer
	move $t1, $a0	#prev pointer
	
    loopDelete_x:
    	lw $t3, 4($t0)	#value
    	bne $t3, $a1, nextDelete_x
    	addi $v0, $v0, 1 #counter++
    	lw $t3, 0($t0)	#pointer to next
    	beqz $t3, exitDelete_x
    	sw $t3, 0($t1)	#prev.next = curr.next
    	lw $t0, 0($t1)	#fix curr
    	j loopDelete_x
    	
    nextDelete_x:
    	lw $t0, 0($t0)
    	beqz $t0, exitDelete_x
    	lw $t1, 0($t1)	#shift both pointers
    	j loopDelete_x
    	
    exitDelete_x:
	move $v1, $a0
	jr $ra
	
	nop



################################################

#
#

#
#     	 	data segment			

#
#						

#
#

################################################



	 .data


msg81:	 .asciiz "This is the current contents of the linked list: \n"


msg82:   .asciiz "No linked list is found, pointer is NULL. \n"


msg83:   .asciiz "The first node contains:  pointerToNext = "


msg84:   .asciiz ", and value = "


msg85:   .asciiz "\n"


msg86:   .asciiz "The next node contains:  pointerToNext = "


msg89:   .asciiz "The linked list has been completely displayed. \n"


msg91:	 .asciiz "This routine will help you create your linked list. \n"


msg92:   .asciiz "How many elements do you want in your linked list? Give a non-negative integer value: 0, 1, 2, etc.\n"


msg93:   .asciiz "Your list is empty, it has no elements. Also, it cannot not be displayed. \n"


msg94:   .asciiz "Input the integer value for list element #"


msg95:   .asciiz ": \n"




msg110:  .asciiz "Welcome to this program about linked lists.\n"


msg111:  .asciiz "Here are the options you can choose: \n"

msg112:  .asciiz "1 - create a new linked list \n"

msg113:  .asciiz "2 - display the current linked list \n"

msg114:  .asciiz "3 - add element at position n and n+1, then delete n+1 \n"

msg115:  .asciiz "4 - insert element into linked list at position n  \n"

msg116:  .asciiz "5 - delete element at position n from linked list \n"

msg117:  .asciiz "6 - delete element from linked list with value x \n"

msg118:  .asciiz "7 - exit this program \n"

msg1181: .asciiz "8 - swap node n with node n + 1 \n"

msg1182: .asciiz "9 - count common values in two lists \n"

msg1183: .asciiz "10 - find sum in range [x, y] \n"

msg119:  .asciiz "Enter the integer for the action you choose:  "

msg120:  .asciiz "Enter the integer value of the element that you want to insert:  "

msg124:  .asciiz "Enter the position number in the linked list where you want to insert the element:  "	

msg125:  .asciiz "Enter the position number in the linked list of the element you want to delete:  "

msg126:  .asciiz "Enter the integer value of the element that you want to delete:  "

msg200:  .asciiz "Enter the position number in the linked list where you want to add consecutive nodes:  "	

msg201:  .asciiz "Enter the position number in the linked list where you want to swap two nodes:  "	

msg202:  .asciiz "Enter the start and end positions you want to find the sum in between:  "	



msg127:  .asciiz "Thanks for using this program about linked lists.\n"


msg128:  .asciiz "You must enter an integer from 1 to 7. \n"

msg130:  .asciiz "The return value was invalid, so it isn't known if the requested action succeeded or failed. \n"	

msg131:  .asciiz "The requested action succeeded. \n"

msg132:  .asciiz "The requested action failed. \n"

  

##


## end of file Lab3main.txt
##SK
