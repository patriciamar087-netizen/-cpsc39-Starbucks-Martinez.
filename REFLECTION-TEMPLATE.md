# Caffeine Quest reflection

Name:

## Five questions before coding

1. Purpose:The merge operation combines two already-sorted halves into one fully sorted section of the array. It compares elements from the left and right halves and places them into a temporary array in the correct order.
2. 
3. Inputs and outputs:
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
| All stores | 1 | | |
| All stores | 2 | | |
| All stores | 3 | | |
| Drive-through only | 1 |Childs & Hwy 99 - Merced |1.84 |
| Drive-through only | 2 |Bellevue & Shaffer - Atwater |7.32 |
| Drive-through only | 3 | Applegate & Hwy 99 - Atwater|7.83 |

What changed, and why would alphabetical order not answer this search?
The drive-through filter removes stores that do not have drive-through service, so the nearest results may change. Alphabetical sorting would arrange stores by name rather than distance. Since the goal is to find the closest Starbucks locations, the stores must be sorted by distance, not by store name.
## Hand trace: merge [2, 7] and [3, 5]

[2, 3, 5, 7]


## Validation

Final SortCheck output or evidence filename:

Additional test: input / expected output / actual output / reason:

Student-mode first three results for the two original searches:

How do they compare with Demo mode? Student map evidence filename:

## Investigate one feature (150-250 words)

Topic and class/method:

Short relevant code excerpt:

Explanation and concrete example:

Source consulted (title and URL or course reference):

## Customization

Feature:

Files changed and explanation:

New-feature test and result:

Default-behavior regression check:

## Algorithm explanation

1. Time complexity and reasoning:
2. Auxiliary space:
3. Stability and how my code preserves it:
4. Why Demo/Student comparison counts may differ:
5. Why a single short timing is insufficient:

## Demonstration checklist

- [ ] Student search and map
- [ ] Explain one merge comparison
- [ ] Show customization
