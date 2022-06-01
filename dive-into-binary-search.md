# dive into binary search

二分：查找

启发式信息：用中点缩短查询区间，中点代表某一区间的性质，如果不符合，就把一大段空间去掉

最后定位到一个单点：符合不符合某个性质的分界点

关键：边界处理问题

## boundary

Template:

**[first,last)**

~~~c++
int binary_search(int a[],value){
	int l=0,r=a.size();
	while(l<r){
	int mid=l+(r-l)/2;//mid to right
  if（check(mid)) r=mid;
  else l=mid+1;
	}
  return l;
}
~~~

Mid:右区间的一个边界点

最后：[first,first+1)->mid=first

本质：找右区间端点（下界），找上界：-1

适用：找某个性质的下界，右边界点

mid是否满足区间性质

[l,r)

目标：找到r（最后l向前到r）

r即为满足某个性质的最前点

在整个过程中：r可以不断往后退，但不能退的太多，以防退出边界外

l不断往前追，每次保证有进度（+1）

如果一直没有找到满足性质的位置：l跳入r，即到达nums.size()

则可以进行特判