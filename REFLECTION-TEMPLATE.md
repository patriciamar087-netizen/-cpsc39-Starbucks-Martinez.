# Caffeine Quest reflection

Name:

## Five questions before coding

1. Purpose:The merge operation combines two already-sorted halves into one fully sorted section of the array. It compares elements from the left and right halves and places them into a temporary array in the correct order.
2. Inputs and outputs:
The array or list being sorted.
Left index (left)
Middle index (mid)
Right index (right)

Output:

The specified section of the array becomes sorted.
Returns the number of comparisons made during merging (if required by the project).

5. Constraints:
 The left half is already sorted.
The right half is already sorted.
Must use the supplied comparator.
Must not call built-in sorting methods.
Must preserve stability.
Must only merge the two sorted halves.

7. Edge cases:
One half may become empty before the other.
Remaining elements from the non-empty half must be copied.
If two keys are equal, choose the element from the left half first to preserve stability.
Arrays with one element require no merging.
   
9. Test oracle:
 Elements appear in sorted order.
No elements are lost or duplicated.
Equal elements remain in their original relative order.
Results match Java's built-in sort for the same data set.
All 12 SortCheck tests pass.

## Explore Demo mode

Starting latitude/longitude:

| Filter | Rank | Store ID / name | Distance in miles |
|---|---:|---|---:|
| All stores | 1 | Main Place - Merced  |  0.08    |
| All stores | 2 | | 580 West Olive - Merced |1.20
| All stores | 3 | |  Childs & Hwy 99 - Merced |1.84
| Drive-through only | 1 |Childs & Hwy 99 - Merced |1.84 |
| Drive-through only | 2 |Bellevue & Shaffer - Atwater |7.32 |
| Drive-through only | 3 | Applegate & Hwy 99 - Atwater|7.83 |

What changed, and why would alphabetical order not answer this search?
The drive-through filter removes stores that do not have drive-through service, so the nearest results may change. Alphabetical sorting would arrange stores by name rather than distance. Since the goal is to find the closest Starbucks locations, the stores must be sorted by distance, not by store name.
## Hand trace: merge [2, 7] and [3, 5]

[2, 3, 5, 7]


## Validation

Final SortCheck output or evidence filename:

PASS: Empty list
PASS: One item
PASS: Two reversed items
PASS: Duplicates and negatives
PASS: Already sorted
PASS: Reverse sorted
PASS: Odd-sized random list
PASS: Stable equal-key order
PASS: Counts comparisons
PASS: All Starbucks records
PASS: Drive-through Starbucks records
PASS: Distance ties use store ID

12 passed; 0 failed.
All supplied checks passed.

Additional test: input / expected output / actual output / reason:
[5, 2, 8, 1, 9, 3]
[1, 2, 3, 5, 8, 9]
[1, 2, 3, 5, 8, 9]
This test verifies that merge sort correctly sorts an unsorted list and places all elements in ascending order.

Student-mode first three results for the two original searches:
Drive-through only
Rank	Store / Name	Distance (miles)
1	Childs & Hwy 99 - Merced	1.84
2	Bellevue & Shaffer - Atwater	7.32
3	Applegate & Hwy 99 - Atwater	7.83

How do they compare with Demo mode? Student map evidence filename:
The Student Mode results matched the Demo Mode results for the first three stores and distances. This confirms that my merge sort implementation correctly sorted the Starbucks locations by distance. The comparison counts may differ because Demo Mode uses Java's built-in sorting algorithm while Student Mode uses my merge sort implementation.
## Investigate one feature (150-250 words)

Topic and class/method:
Topic: Local web server and localhost
Class: MapPreviewServer



Short relevant code excerpt:
server = HttpServer.create(
    new InetSocketAddress("127.0.0.1", 8080), 0);
    server.createContext("/",
    exchange -> serve(exchange, mapFile.getParent()));
Explanation and concrete example:
The MapPreviewServer class creates a local web server that runs on the user's computer. The address 127.0.0.1, also called localhost, refers to the same computer that is running the Java application. The server listens on port 8080 and waits for requests from a web browser.

When the user opens http://localhost:8080/student-map.html, the browser sends a request to the local server. The serve() method receives the request, locates the generated HTML map file, and sends it back to the browser. The browser then displays the Starbucks locations and ranked search results on an interactive map.

For example, after running Student Mode in CaffeineQuest.java, the program generates student-map.html. When the browser requests this file through localhost, the preview server retrieves the file from the output folder and displays it. This allows Java-generate
Source consulted (title and URL or course reference):
Java SE Documentation: HttpServer
https://docs.oracle.com/en/java/javase/11/docs/api/jdk.httpserver/com/sun/net/httpserver/HttpServer.html
## Customization

Feature:

Files changed and explanation:

New-feature test and result:

Default-behavior regression check:
The original nearest-first sorting behavior continued to function correctly after implementing merge sort. All 12 supplied SortCheck tests passed successfully.
## Algorithm explanation

1. Time complexity and reasoning: Merge sort has a time complexity of O(n log n). The list is repeatedly divided into smaller halves until each section contains one element. The sections are then merged back together in sorted order. Because there are approximately log₂(n) levels of splitting and each level processes all n elements, the overall running time is O(n log n).
2. Auxiliary space: Merge sort requires O(n) auxiliary space because it uses a temporary buffer list to store merged elements before copying them back into the original list.


3. Stability and how my code preserves it:My merge sort is stable because when two elements compare as equal, the algorithm selects the element from the left half first: if (order.compare(items.get(left), items.get(right)) <= 0)


4. Why Demo/Student comparison counts may differ: Demo mode uses Java's built-in sorting algorithm, while Student mode uses my merge sort implementation. Different sorting algorithms can perform different numbers of comparisons even when they produce the same sorted results.
5. Why a single short timing is insufficient:A single timing measurement can be affected by factors such as CPU load, memory usage, background programs, and JVM startup overhead. Multiple runs should be performed and averaged to make a reliable comparison between algorithms.

## Demonstration checklist

- [x ] Student search and map
- [ x] Explain one merge comparison
- [ ] Show customization
