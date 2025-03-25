# 【模板】KMP By 灵茶山艾府

[灵神对KMP的讲解](https://leetcode.cn/link/?target=https%3A%2F%2Fwww.zhihu.com%2Fquestion%2F21923021%2Fanswer%2F37475572)

```C++
// 查找pattern在text中出现的所有位置
vector<int> kmp(string &text, string &pattern) {
        int m = pattern.length();
        vector<int> pi(m);
        int c = 0;
        for (int i = 1; i < m; i++) {
            char v = pattern[i];
            while (c && pattern[c] != v) {
                c = pi[c - 1];
            }
            if (pattern[c] == v) {
                c++;
            }
            pi[i] = c;
        }

        vector<int> res;
        c = 0;
        for (int i = 0; i < text.length(); i++) {
            char v = text[i];
            while (c && pattern[c] != v) {
                c = pi[c - 1];
            }
            if (pattern[c] == v) {
                c++;
            }
            if (c == m) {
                res.push_back(i - m + 1);
                c = pi[c - 1];
            }
        }
        return res;

作者：灵茶山艾府
链接：https://leetcode.cn/problems/find-beautiful-indices-in-the-given-array-i/solutions/2603716/fei-bao-li-zuo-fa-kmper-fen-cha-zhao-pyt-0o8y/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
