# Sorting-Algorithms
import random
import time

maxvalue = 1000

def merge(left, right):
    result = []
    left_idx, right_idx = 0, 0
    while left_idx < len(left) and right_idx < len(right):
        # to change direction of sort, change direction of comparison
        if left[left_idx] <= right[right_idx]:
            result.append(left[left_idx])
            left_idx += 1
        else:
            result.append(right[right_idx])
            right_idx += 1
    if left:
        result.extend(left[left_idx:])
    if right:
        result.extend(right[right_idx:])
    return result

def merge_sort(m):
    if len(m) <= 1:
        return m

    middle = len(m) // 2
    left = m[:middle]
    right = m[middle:]

    left = merge_sort(left)
    right = merge_sort(right)
    return list(merge(left, right))

def insertion_sort(array):
    for slot in range(1, len(array)):
        value = array[slot]
        test_slot = slot - 1
        while test_slot > -1 and array[test_slot] > value:
            array[test_slot + 1] = array[test_slot]
            test_slot = test_slot - 1
        array[test_slot + 1] = value
    return array

def bubble_sort(array):
    index = len(array) - 1
    while index >= 0:
        for j in range(index):
            if array[j] > array[j + 1]:
                array[j], array[j + 1] = array[j + 1], array[j]
        index -= 1
    return array

def main():
    #ADD CODE to compare the three list-sorting functions
    #  See Canvas assignment for details.
    speedlist1 = [random.randint(1,maxvalue) for i in range(maxvalue)]
    time1 = time.time()
    merge_sort(speedlist1)
    time2 = time.time()
    print("merge sort elapsed time: ",time2 - time1)

    speedlist2 = [random.randint(1,maxvalue) for i in range(maxvalue)]
    time1 = time.time()
    insertion_sort(speedlist1)
    time2 = time.time()
    print("insertion sort elapsed time: ",time2- time1)

    speedlist3 = [random.randint(1,maxvalue) for i in range(maxvalue)]
    time1 = time.time()
    bubble_sort(speedlist1)
    time2 = time.time()
    print("bubble sort elapsed time: ",time2 - time1)

main()
