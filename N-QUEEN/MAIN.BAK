#include <iostream.h>
#include <graphics.h>
#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <dos.h>



struct Node {
    int row;
    int col;
    Node *next;
};
struct Stack {
    Node *top;
    Stack() {
    top=NULL;
    }
};
int isFull() {
    Node *newNode=new Node;
    if(!newNode) {
	return 1;
    }
    else {
	return 0;
    }
}
int isEmpty(Stack *s) {
    if(s->top==NULL) {
	return 1;
    }
    else {
	return 0;
    }
}
int insert(Stack *s, int row, int col) {
    Node *newNode=new Node;
    if(!newNode)
     {
	return 1;
    }
    newNode->row=row;
    newNode->col=col;
    newNode->next=s->top;
    s->top=newNode;
    return 0;
}
int pop(Stack *s, int *row, int *col) {
    if(isEmpty(s)) {
	return 1;
    }
    Node *temp=s->top;
    *row=s->top->row;
    *col=s->top->col;
    s->top=s->top->next;
    delete temp;
    return 0;
}
int peak(Stack *s, int *row, int *col) {
    if(isEmpty(s)) {
	return 1;
    }
    *row=s->top->row;
    *col=s->top->col;
    return 0;
}




int isUnproctected(int ***grid, int row, int col, int n) {
    //row check
    for(int i=0; i<n; i++) {
	if(grid[0][row][i]) {
	    return 0;
	}
    }
    //column check
    for(int j=0; j<n; j++) {
	if(grid[0][j][col]) {
	    return 0;
	}
    }
    //top-left diagonal check
    int r=row, c=col;
    while(r >= 0 && c >= 0) {
	if(grid[0][r][c]) {
	    return 0;
	}
	r--; c--;
    }
    //top-right diagonal check
    r=row; c=col;
    while(c < n && r >= 0) {
	if(grid[0][r][c]) {
	    return 0;
	}
	r--; c++;
    }
    return 1;
}
void printqueen(int X,int Y, int x, int y,int type) {
   setcolor(GREEN);
   if(!type) setcolor(14);
    rectangle(X+0.4*x,Y+0.31*y,X+0.6*x,Y+y*0.7);
   if(!type) {setcolor(4);}
    circle(X+0.5*x,Y+0.2*y,0.1*y);
   if(!type) {setcolor(6); }
    rectangle(X+0.3*x,Y+y*0.7,X+0.7*x,Y+y*0.9);
   setcolor(14);
}
int **solveNQueen(int n) {
    setlinestyle(SOLID_LINE,1,3);
    int row=0;
    int col=0;
    Stack s;
    //initialize the grid
    int **grid = new int*[n];
    for(int z=0; z<n; z++) {
	grid[z] = new int[n];
    }
    for(int t=0; t<n; t++) {
	for(int d=0; d<n; d++) {
	    grid[t][d]=0;
	}
    }
    // graph initialize
    int x=getmaxx();
    int y=getmaxy();
    int X=x/n;
    int Y=y/n;
    setfillstyle(SOLID_FILL,GREEN);
    for(int j=0; j<n; j++) {
	for(int i=0; i<n; i++) {
		  floodfill(X*i+X/2,j*Y+Y/2,GREEN);
		rectangle(i*X,j*Y,i*X+X,j*Y+Y);
	}
    }
    //actual solve
    while(row<n) {
	int z=0;
	while(col<n) {
	    if(isUnproctected(&grid,row,col,n)) {
	    insert(&s,row,col);
		grid[row][col]=1;
		setcolor(14);
		circle(col*X+X/2,row*Y+Y/2,n/2);
		printqueen(col*X,row*Y,X,Y,0);
		delay(1000);
		row++;
		col=0;
		break;
	    }
	    else {
	    setcolor(10);
		circle(col*X+X/2,row*Y+Y/2,n/2);
		printqueen(col*X,row*Y,X,Y,0);
		delay(700);
		setcolor(GREEN);
		circle(col*X+X/2,row*Y+Y/2,n/2);
		printqueen(col*X,row*Y,X,Y,1);
		setcolor(14);
		col++;
	    }
	}
	while(col >= n) {
	    pop(&s,&row,&col);
	    grid[row][col]=0;
	    setcolor(GREEN);
	    circle(col*X+X/2,row*Y+Y/2,n/2);
	    setcolor(4);
	    printqueen(col*X,row*Y,X,Y,1);
	    delay(1000);
	    z=1;
	  }
	if(z) {col++;}
    }
    getch();
    cleardevice();
    return grid;
}

void end(int x,int y) {
    setcolor(14);
    rectangle(x/2-200,y/2-100,x/2+200,y/2+200);
    setcolor(13);
    outtextxy(0.9*x/2,1.1*y/2,"THANK YOU!");
    setcolor(15);
    outtextxy(0.86*x/2,1.2*y/2,"By : RAVI JAIN");
    setcolor(9);
    outtextxy(0.94*x/2,1.3*y/2,"411764");
    getch();
    cleardevice();
}

int main() {
    int gdrive=DETECT,gmode;
    initgraph(&gdrive,&gmode,"c:\\turboc3\\bgi");
    int n;
    cout << "Number of Queens: ";
    cin >> n;
    cleardevice();
    int x=getmaxx();
    int y=getmaxy();
    solveNQueen(n);
    end(x,y);
    getch();
    cleardevice();
    closegraph();
    return 0;
}



