const int x=15;
const int y=51;
const int z=85;


int what(int l, string& s) {
    if (s[l]=='!') {
        l++;
        if (s[l]=='x') {
            return x^(255);
        }
        if (s[l]=='y') {
            return y^(255);
        }
        if (s[l]=='z') {
            return z^(255);
        }
    } else {
        if (s[l]=='x') {
            return x;
        }
        if (s[l]=='y') {
            return y;
        }
        if (s[l]=='z') {
            return z;
        }
    }
}

int findans(string& re) {
    vector < int > solve;
    for (int i(0); i<re.size(); i++) {
        if (re[i]=='&') {
            solve.pb(-1);
            continue;
        }
        if (re[i]=='|') {
            solve.pb(-2);
            continue;
        }
        if (re[i]=='(' || (re[i]=='!' && re[i+1]=='(')) {
            int l=i+1, f=0;
            string h="";
            if (re[l]=='(') {
                l++;
                f=1;
            }
            for (int j(l); j<re.size(); j++) {
                if (re[j]==')') {
                    i=j;
                    break;
                }
                h+=re[j];
            }
            if (f==1) {
                solve.pb(findans(h)^255);
            } else solve.pb(findans(h));
            continue;
        }
        solve.pb(what(i, re));
        if (re[i]=='!') {
            i++;
        }
    }
    vector < int > resolve;
    resolve.pb(solve[0]);
    for (int i(1); i<solve.size(); i++) {
        if (solve[i]==-1) {
            i++;
            resolve[resolve.size()-1]&=solve[i];
            continue;
        }
        if (solve[i]==-2) {
            continue;
        }
        resolve.pb(solve[i]);
    }
    int ans=resolve[0];
    for (int i(1); i<resolve.size(); i++) {
        ans|=resolve[i];
    }
    return ans;
    return 0;
}

bool ch(string& re, string& dv) {
    int need=0, ans=0;
    for (int i(dv.size()-1); i>=0; i--) {
        if (dv[i]=='1') need+=(1 << (dv.size()-1-i));
    }
    ans=findans(re);
    if (need==ans) {
        return true;
    } else return false;
}
