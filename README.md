# Problem-Find-All-Subarrays-with-Zero-Sum-
given an integer array arr of size n. Your task is to find all the subarrays whose elements sum up to zero. A subarray is defined as a contiguous part of the array, and you must return the starting and ending indices of each subarray.  Input : An integer array arr of size n where n represents the number of elements in the array.
def find_zero_sum_subarrays(arr):
    n = len(arr)
    sum_indices_map = {}
    current_sum = 0
    result = []
    for i in range(n):
        current_sum += arr[i]
        if current_sum == 0:
            result.append((0, i))
        if current_sum in sum_indices_map:
            for index in sum_indices_map[current_sum]:
                result.append((index + 1, i))
            sum_indices_map[current_sum].append(i)
        else:
            sum_indices_map[current_sum] = [i]
    return result
arr = [3, 4, -7, 3, 1, 3, 1, -4, -2, -2]
print(find_zero_sum_subarrays(arr))

