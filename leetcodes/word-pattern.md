# Word Pattern
[linker to leetcode](https://leetcode.com/problems/word-pattern/)

Descriptions:

Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Examples:
pattern = "abba", str = "dog cat cat dog"  should return true.<br/>
pattern = "abba", str = "dog cat cat fish"  should return false.<br/>
pattern = "aaaa", str = "dog cat cat dog"  should return false.<br/>
pattern = "abba", str = "dog dog dog dog"  should return false.<br/>
Notes:<br/>
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.


 * 1. how to split a string into substring array
 * 2. how to use map
 * 3. master the concept of <b> 'bijection '</b> which means two sets f, g
 >*    f(x) = y, x is an element in f , y is belong to g 
 >*    on th other hand, g(a) = b ; a is an element in set g , and b is belong to f
 >*    something you should pay attention to is that , a ,b,x ,y is unique which mean 
 >*    if there is g(a) = b , g(k) =b or g(a) = m , g(k) = m, these situations are all wrong 
 
 ##here are the steps to solve the problem:
 * i use map to help me solve the problem of bijection 
 * split the str into small sub-strings by substr provided by string
 * justify the pattern's length is equal to sub-string arrays', if lenth not match , false
 * travers the pattern 
 > for i = 0 --> pattern.size()-1<br/>
 > if there is no elemenet with key = pattern.at(i) <br/> 
 >    no element with value = sub-string.at(i) && the key of the value not match pattern(i)<br/>
 >    insert the pair<key,value> into the map
 > if there is an element with key = pattern.at(i) and the value = sub-string.at(i)<br/>
 >     just continue the loop<br/>
 > if there is an element with key = pattern.at(i) however the value not match sub-string.at(i)<br/>
 >     set the flag to false , and break the circle     
 
here is the source code:

````c++
class Solution {
public:
  
		bool wordPattern(string pattern, string str) {

		int from, to;
		string temp;
		vector<string> subArr;
		map<char, string> pairs;


		from = 0;
		to = str.find(" ", from);
		temp = str.substr(from, to - from);

		subArr.push_back(temp);

		while (to != -1) {
			from = to + 1;
			to = str.find(" ", from);

			
			temp = str.substr(from, to - from);
			subArr.push_back(temp);

		}
		 
		if (subArr.size() != pattern.size())
			return false;

		map<char, string>::iterator it;
		map<char, string>::iterator it2;

		bool flag = true;

		for (int i = 0; i < pattern.size(); i++) {

			it = pairs.find(pattern.at(i));

			if (it == pairs.end()) {
				// 当且仅当，在 pairs 的pairs 中没有 value 相同，但是 key 不同的元素存在

		

				for (it2 = pairs.begin(); it2 != pairs.end(); it2++) {
					if (it2->second == subArr.at(i) && it2->first != pattern.at(i)) {
						flag = false;
						break;
					}
				
				
				}				
				pairs.insert(make_pair(pattern.at(i), subArr.at(i)));
			}
			else {

				if (it->second.compare(subArr.at(i)) == 0) {
					continue;
				}
				else {
					flag = false;
					break;
				}

			}


		}

		return flag;
	}
} ;

````
end