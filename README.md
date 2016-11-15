# ip-hw-4
rows and columns
def swapRows(A,row1,row2):
	A[row1],A[row2]=A[row2],A[row1]

def Row_Transformation(A,x,row1,row2):
	for i in range(len(A[0])):
		A[row2][i]=A[row2][i]+x*A[row1][i]

def MatrixRank(A):
	rank=len(A[0])
	tr=len(A)
	tc=len(A[0])
	row=0
	while row<rank:
		if A[row][row]!=0:
			p=row+1
			while p<len(A):
				x=float(A[p][row]/A[row][row])*(-1)
				Row_Transformation(A,x,row,p)
				p+=1
		else:
			p=row+1
			count=0
			while p<len(A):
				if A[p][row]!=0:
					swapRows(A,p,row)
					row-=1
					break
				if A[p][row]==0:
					count+=1
			if count==len(A)-row:
				rank-=1
				for k in range(len(A)):
					A[k][row],A[len(A[0])][row]=A[len(A[0])][row],A[k][row]
			if row==len(A)-1 and A[row][row]==0:
				rank-=1
		row+=1
	return(rank)
