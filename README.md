# helloword
just another repository
//逻辑二叉树.h
struct BiNode{
	char data[10];
	BiNode * lchild;
	BiNode * rchild;
};
typedef BiNode* BiTree;
void InitBiTree(BiTree &BT)
{
	BT=NULL;
}
void DestoryBiTree(BiTree &BT)
{
	if(BT)
	{
		if(BT->lchild)
		{
			 DestoryBiTree(BT->lchild);
		}
		if(BT->rchild)
		{
			 DestoryBiTree(BT->rchild);
		}
		free(BT);
		BT=NULL;
	}	
} 
void ClearBiTree(BiTree  &BT)
{
	DestoryBiTree(BT);
}
bool BiTreeEmpty(BiTree &BT)
{
	return BT==NULL; 
}
void PreOrderTraverse(BiTree &BT,void (*visit)(char *))
{
	if(BT)
	{
		visit(BT->data);
		if(BT->lchild) PreOrderTraverse(BT->lchild,visit);
		if(BT->rchild) PreOrderTraverse(BT->rchild,visit);
	}
}
void  AfterOrderTraverse(BiTree &BT,void (*visit)(char *))
{
	if(BT)
	{
		if(BT->lchild) AfterOrderTraverse(BT->lchild,visit);
		if(BT->rchild) AfterOrderTraverse(BT->rchild,visit);
		visit(BT->data);
	}
}

