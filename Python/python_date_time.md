## PYTHON

###### datetime package
1. datetime class: 날짜 및 시간을 저장하는 클래스, 생성자로 년, 월, 일, 시, 분, 초를 받아 datetime 객체 생성
	- today()
	- now()
	- utcnow()
	- fromtimestamp()
	- utcfromtimestamp()
	- fromordinal()
	- combine()
	- strptime()
	- strftime()
	- date()
	- time()
	- replace()
	- timetuple()
	- weekday()
	- isoweekday()
	- isocalendar()
	- isoformat()
	- ctime()


2. date class: 날짜만 저장하는 클래스, 생성자로 년, 월, 일을 받아 date 객체 생성
	- fromtimestamp(timestamp): 타임스탬프 값을 date 객체로 반환
	- fromordinal(ordinal): ordinal 값을 date 객체로 반환(ordinal: 0001.01.01 부터 N번째 날을 의미)
	- today(): 오늘 날짜 출력 (년, 월, 일)
	- replace()
	- timetuple()
	- toordinal()
	- weekday()
	- isoweekday()
	- isoformat()
	- ctime()
	- strftime()


3. time class: 시간만 저장하는 클래스, 반드시 생성자에 인자를 넣어 time 객체 생성(주로 time zone 을 통해 객체 생성)
	- replace
	- isoformat
	- strftime


4. timedelta class: 시간 구간 정보 저장하는 클래스
	- days[일], seconds[초], microseconds[마이크로초]
	- total_seconds(): 모든 속성을 초단위로 변환
	- datetime.datetime 객체에 datetime.timedelta 객체를 연산하여 새로운 시간 구할 수 있음

