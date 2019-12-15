//https://leetcode.com/problems/design-twitter/
class Twitter {
public:
    map<int, map<int, int>> user_follows;
    vector<pair<int, int>> all;

    /** Initialize your data structure here. */
    Twitter() {
        
    }
    
    /** Compose a new tweet. */
    void postTweet(int userId, int tweetId) {
        all.push_back(make_pair(userId, tweetId));
    }

    /** Retrieve the 10 most recent tweet ids in the user's news feed. Each item in the news feed must be posted by users who the user followed or by the user herself. Tweets must be ordered from most recent to least recent. */
    vector<int> getNewsFeed(int userId) {
        vector<int> res;
        for (auto& twit : all)
        {
            // run trough all twitts and add to result if it`s user`s twit or of someone he follows
            if (twit.first == userId || user_follows[userId].find(twit.first) != user_follows[userId].end())
            {
                res.push_back(twit.second);
            }
        }
        reverse(res.begin(),res.end());
        if (res.size() > 10)
            res.resize(10);
        return res;
    }
    
    /** Follower follows a followee. If the operation is invalid, it should be a no-op. */
    void follow(int followerId, int followeeId) {
        user_follows[followerId][followeeId] = 1;
    }
    
    /** Follower unfollows a followee. If the operation is invalid, it should be a no-op. */
    void unfollow(int followerId, int followeeId) {
        if (user_follows.find(followerId) != user_follows.end())
        {
            user_follows[followerId].erase(followeeId);
        }
    }
};
/**
 * Your Twitter object will be instantiated and called as such:
 * Twitter* obj = new Twitter();
 * obj->postTweet(userId,tweetId);
 * vector<int> param_2 = obj->getNewsFeed(userId);
 * obj->follow(followerId,followeeId);
 * obj->unfollow(followerId,followeeId);
 */
