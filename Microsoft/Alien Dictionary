class Solution {
 public:
  void checkOrder(const string& a, const string& b, char& small, char& large) {
    size_t l = 0;
    small = 0;
    large = 0;
    while (l < a.size() && l < b.size()) {
      if (a[l] != b[l]) {
        small = a[l];
        large = b[l];
        return;
      }
      l++;
    }
  }

  string alienOrder(vector<string>& words) {
    set<char> alphabet;
    for(size_t i = 0;i < words.size();++i) {
        for(size_t j = 0;j < words[i].size();++j) {
            alphabet.insert(words[i][j]);
        }
    }
      
    unordered_map<char, set<char> > edges;
    char small = 0, large = 0;
    for (size_t i = 0; i < words.size(); ++i) {
      for (size_t j = i + 1; j < words.size(); ++j) {
        checkOrder(words[i], words[j], small, large);
        if (small == 0 || large == 0) {
          continue;
        } else {
          edges[small].insert(large);
        }
      }
    }

    unordered_map<char, int> incoming_degree;
    for (unordered_map<char, set<char> >::iterator it = edges.begin();
        it != edges.end(); ++it) {
      for (set<char>::iterator it2 = it->second.begin();
          it2 != it->second.end(); ++it2) {
        incoming_degree[*it2]++;
      }
    }

    queue<char> no_incoming;
    for (unordered_map<char, set<char> >::iterator it = edges.begin();
        it != edges.end(); ++it) {
      if (incoming_degree[it->first] == 0) {
        no_incoming.push(it->first);
      }
    }

    string letters;
    while (!no_incoming.empty()) {
      char front = no_incoming.front();
      no_incoming.pop();
      letters += front;

      for (set<char>::iterator it = edges[front].begin(); it != edges[front].end();
          ++it) {
        incoming_degree[*it]--;
        if (incoming_degree[*it] == 0) {
          no_incoming.push(*it);
        }
      }
    }
    
    if (edges.size() != letters.size())
      return "";
    
    for(set<char>::iterator it = alphabet.begin();it != alphabet.end();++it) {
        if(letters.find_first_of(*it) == string::npos) {
            letters += *it;
        }
    }

    return letters;
  }
};
