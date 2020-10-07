# titanic 2


#include<bits/stdc++.h>
#include <ext/pb_ds/assoc_container.hpp> 
#include <ext/pb_ds/tree_policy.hpp> 
#define int              long long
#define ll               long long
#define ld               long double
#define pii              pair<int,int>
#define pb               push_back
#define all(a)           a.begin(),a.end()
#define print(a)         for(auto b:a)cout<<b<<" ";cout<<endl;
#define endl             '\n'
#define F                first
#define S                second
#define vi               vector<int>
#define sz(s)            (int)s.size()
#define rep(i,a,b)       for(int i=a;i<b;i++)
#define bs               binary_search
#define PI               3.14159265358979323844
#define input(a,n)       for(int i=0;i<n;i++)cin>>a[i];
#define lb               lower_bound
#define ub               upper_bound
#define mapi             map<int,int>
#define point            complex<int>
#define fat              998244353
#define hell             1000000007
#define N                100005
#define ios              ios_base::sync_with_stdio(false); cin.tie(0); cout.tie(0);
#define trace(...) __f(#__VA_ARGS__, __VA_ARGS__)
using namespace std;
using namespace __gnu_pbds;
template <typename Arg1>
void __f(const char* name, Arg1&& arg1){
    std::cerr << name << " : " << arg1 << endl;
}
template <typename Arg1, typename... Args>
void __f(const char* names, Arg1&& arg1, Args&&... args){
    const char* comma = strchr(names + 1, ',');std::cerr.write(names, comma - names) << " : " << arg1<<" | ";__f(comma+1, args...);
}
template<typename T, typename U> static inline void amin(T &x, U y) { 
    if (y < x) 
        x = y; 
}
template<typename T, typename U> static inline void amax(T &x, U y) { 
    if (x < y) 
        x = y; 
}


int power(int x,int y,int p) 
{ 
    int res = 1;       
    x = x % p;    
    while (y > 0) 
    { 
        if (y & 1) 
            res = (res*x) % p; 
        y = y>>1;  
        x = (x*x) % p;   
    } 
    return res; 
} 


int solution()
{
    string s;
    cin>>s;
    int n=sz(s);
    int ans=0;
    int h[N];
    h[0]=0;
    rep(i,1,n)
    {
      h[i]=h[i-1];
      h[i]+=power(10,i-1,hell)*i;
      h[i]%=hell;

    }

    rep(i,0,n)
    {
      int k=s[i]-'0';
      int m=i;
      int n1=n-i-1;

      int val=m*(m+1)/2;
      int ad=0;
      val%=hell;
      val*=power(10,n1,hell);
      val%=hell;
      val*=k;
      val%=hell;


      ad+=val;
      ad+=h[n1]*k;
      // trace(i,ad);

      ans+=ad;
      ans%=hell;

    }
    // int j1=1e6+10000;
    // j1*=(hell+10);
    // cout<<(hell-j1%hell)<<endl;
    // j1-=j2;
    // j1*=-1;
    // cout<<j1%hell;

    cout<<ans<<endl;
}
 
signed main()
{
ios
int tests=1;
//cin>>tests;
while(tests--)
{
    solution();
}
return 0;
}
