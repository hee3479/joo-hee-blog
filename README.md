# 산업경영알고리즘 중간고사


## 탐색 알고리즘

- 순차탐색
    - 검색할 집합이 정렬되어 있지 않은 상태 일 때
    - 처음부터 차례대로 찾아보는 것으로, 쉽지만 비효율적이다.
    - 집합의 데이터가 정렬되어 있지 않다면 이 검색 외에 특별한 방법 없음

- 이진탐색
    - 데이터가 정렬되어 있다면 이진 검색도 사용 가능
    - 순차 검색에 비해 월등히 효율적이라 데이터가 몇 천만 개 이상이어도 빠르게 찾아낼 수 있음

***
### 이진탐색 코드

    def binary_search(list, item)  ### 시작 (처음에는 배열 전체를 탐색한다)
    low = 0   ### low와 high는 전체 리스트 중에서 어떤 부분을 탐색해야하는지 알려줍니다.
    high = len(list)-1
    while low <=high ### 만약 탐색 범위를 하나로 줄이지 못했으면 계속 실행합니다.
    mid = (low + high) / 2 ### 가운데 숫자를 확인 합니다.
    guess = list[mid]
    if guess == item ----> #아이템을 찾았습니다.
        return mid
    if guess > item ----> #추측한 숫자가 너무 큽니다.
        high = mid -1
    else: ----> #추측한 숫자가 너무 작습니다.
        low = mid + 1
    return none ----> #아이템이 리스트에 없습니다.

    my_list = [1,3,5,7,9] ----> #확인해보자

    print binary_search(my_list, 3) # => 1 #잊지마세요. 리스트 번호는 0부터 시작합니다. 두 번째 상자의 번호가 1입니다
    print binary_search(my_list, -1) # => none #파이썬에서 none는 아무것도 아니라는 뜻입니다. 지정한 아이템이 없다는 것을 알려줍니다.

### 위 코드에서 틀린 것
    1. :이 없다. def binary_search(list, item):,  while low <=high:, if guess == item:, if guess > item:
    2. mid = (low + high) / 2 이부분은 int가 들어가거나 // 표시로 몫만 사용해야한다.
    3. print도 함수다. 다음과 같이 수정해야한다. print (binary_search(my_list, 3)) print (binary_search(my_list, -1))
    
### 과제 : 랜덤하게 0과 100000 사이의 정수를 1000개 생성한후 0과 100000 사이의 숫자를 랜덤하게 뽑아서 찾는 이진탐색 코드를 작성하시오. 또한 몇 번 반복해서 탐색에 성공하였는지 실패하였는지도 출력하시오

### 랜덤으로 비밀 숫자 생성
    secret_number = random.randint(0, 10000)
    low = 0
    high = 10000
    attempts = 0
    success_count = 0
    fail_count = 0

    print("컴퓨터가 0부터 10000 사이의 숫자를 맞춥니다!")

### 버튼을 누를 때마다 한 번씩 추측하도록 반복
    
    while low <= high:
    input("엔터를 눌러 컴퓨터가 추측하게 하세요...")
    attempts += 1
    guess = (low + high) // 2
    print(f"컴퓨터의 추측: {guess}")

    if guess == secret_number:
        success_count += 1
        print(f"정답입니다! 컴퓨터가 {attempts}번 만에 {secret_number}을(를) 찾았습니다.")
        print(f"성공: {success_count}번, 실패: {fail_count}번")
        break
    elif guess < secret_number:
        fail_count += 1
        low = guess + 1
    else:
        fail_count += 1
        high = guess - 1
        
***
         

- 트리탐색 (데이터가 변동이 크면 관리가 어려움)
    - 데이터 검색에는 상당히 효율적이지만 트리의 삽입, 삭제 등에는 부담

 ## 선택정렬

 - 선택정렬
 - 삽입정렬
 - 버블정렬
 - 퀵정렬

## 선택정렬 최솟값을 찾는 코드

    def findminidx(ary):
        minidx = 0
        for i in range(1, len(ary)):
            if (ary[minidx] > ary[i]):
                minidx = i
        return minidx

    testary = [55, 88, 77, 33]
    minpos = findminidx(testary)
    print('최솟값 -->', testary[minpos]) #실행결과 : 최솟값 --> 33

## 선택정렬 개선된 최솟값을 찾는 코드

    def selectionsort(ary)
        n = len(ary)
        for i in range(0,n-1) :
            minidx = i
            for k in range(i+1,n) :
                if (ary[minidx] > ary[k]) :
                    minidx = k
            tmp = ary[i]
            ary[i] = ary[minidx]
            ary[minidx] = tmp

        return ary

    dataary = [188, 162, 168, 120, 50, 150, 177, 105]  ##전역 변수 선언 부분##

    print('정렬 전 --->', dataary)
    dataary = selectionsort(dataary)
    print('정렬 후 --->', dataary)

    
## 선택정렬 배열을 정렬하는 코드                

    def findsmallest(arr):
        smallest = arr[0]
        smallest_index = 0
        for i in range(1, len(arr)):
            if arr[i] < smallest:
               smallest = arr[i]
               smallest_index = i
        retrun  smallest_index
        
    def selectionsort(arr):
        newarr = []
        for i in range(len(arr)):
            smallest = findsmallest(arr)
            newarr.append(arr.pop(smallest))
        return newarr

    print selectionsort([5,3,6,2,10])
   
            
