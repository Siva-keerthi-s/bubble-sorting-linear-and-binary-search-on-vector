// let's do bubble sort, linear and binary search
# include <iostream>
# include <vector>
using std::cout;
using std::cin;
using std::endl;
using std::vector;
void bubble_sort(vector <int> &vec);
int linear_search(const vector <int> &vec, int number);
int binary_search(const vector <int> &vec, int number);
int main(){
  int number;
  vector <int> vec={-1,5,4,9,5,7,8,3,4};
  bubble_sort(vec);
  for(int i : vec) cout << i << " ";
  cout << endl;
  cout << "Enter the element you want to search(int)" << endl;
  cin >> number;
  int linear = linear_search(vec,number);
  int binary = binary_search(vec,number);
  if(linear != -1) cout << "Element is fund at the index " << linear << endl;
  else cout << "Element not found" << endl;
  if(binary != -1) cout << "Element is found at the index " << binary << endl;
  else cout << "Element not found" << endl; 
  return 0;
}
void bubble_sort(vector <int> &vec){
  for(int i = 0; i < vec.size(); i++){
    bool check = false;
    for(int j = 0; j < vec.size() - 1; j++){
      if(vec[j] > vec[j+1]){
        int temp = vec[j+1];
        vec[j+1] = vec[j];
        vec[j] = temp;        
        check = true;
      }
    }
    if(check == false) break;
  }
} 
int linear_search(const vector <int> &vec, int number){
 for(int  i = 0; i < vec.size(); i++){
  if(number == vec[i]) return i;
 }
 return -1;
}
int binary_search(const vector <int> &vec, int number){
  int st = 0,end,n = vec.size(), mid;
  end = n-1; 
  while(st <= end){
    mid = (st + end) / 2;
    if(vec[mid] == number) return mid;
    else if (vec[mid] > number) end = mid - 1;
    else st = mid + 1;
  }
  return -1;
}
