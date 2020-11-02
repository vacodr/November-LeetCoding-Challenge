## 920. Meeting Rooms
Given an array of meeting time intervals consisting of start and end times [[s1,e1],[s2,e2],...] (si < ei), determine if a person could attend all meetings.

link: https://www.lintcode.com/problem/meeting-rooms/description

Problem type: Easy

# Code
```java
/**
 * Definition of Interval:
 * public class Interval {
 *     int start, end;
 *     Interval(int start, int end) {
 *         this.start = start;
 *         this.end = end;
 *     }
 * }
 */

public class Solution {
    /**
     * @param intervals: an array of meeting time intervals
     * @return: if a person could attend all meetings
     */
    public boolean canAttendMeetings(List<Interval> intervals) {
        
        Collections.sort(intervals,(a,b)->a.start- b.start);
        int end = Integer.MIN_VALUE;
        
        for(Interval in : intervals)
        {
            if(in.start<end)
            {
                return false;
            }
            else
            {
                end = in.end;
            }
        }
        
        return true;
        
    }
}
```
