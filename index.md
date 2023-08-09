<html>
<head>
    <meta charset="utf-8" />
    <script src="https://js.tosspayments.com/v1/payment"></script>
</head>
<body>
    <section>
         ... 
        <span>총 주문금액</span>
        <span>15,000 원</span>
        <button id="payment-button">15,000원 결제하기</button>
    </section>
    <script>
        
        //var clientKey = 'test_ck_D5GePWvyJnrK0W0k6q8gLzN97Eoq'
        //var tossPayments = TossPayments(clientKey)
        //var button = document.getElementById('payment-button') // 결제하기 버튼
        //const myKeysValues = window.location.search;
        //console.log("k & v: ",myKeysValues);
        //const urlParams = new URLSearchParams(myKeysValues);
        //console.log(urlParams.get('amt'));
        //button.addEventListener('click', function () {
        //    tossPayments.requestPayment('카드', {
        //        //amount: 15000,
        //        amount: urlParams.get('amt'),
        //        orderId: 'jibrTspM6ITMj7kBAS3fU',
        //        orderName: '토스 티셔츠 외 2건',
        //        customerName: '박토스',
        //        successUrl: 'https://hoohoohooo.github.io/testWeb.io/backToUnity.html',
        //        failUrl: 'http://localhost:8080/fail',
        //    })
        //})
        """다운로드 받은 csv 파일을 open() 함수를 이용해서 열어보는 실습"""
import csv
f = open(
    "C:/Users/7513/Desktop/STCS_폭염일수_20230809093706.csv",
    'r')
lines = csv.reader(f)
init = 0
doRead = 0
keys = []
dataList = []
for line in lines:
    if '폭염일수' in line:
        print("start of data")
    elif '평균 폭염일수' in line:
        init = 1
    elif '가장 긴 폭염' in line:
        init = 2
    else:
        if init == 1:
            keys = line
            init = 0
            doRead = 0
        elif init == 2:
            keys = line
            init = 0
            doRead = 2
        if doRead == 1:
            if line == []:
                doRead = 0
            else:
                index = 0
                tmpDic = {}
                for i in line:
                    tmpDic[keys[index]] = i
                    index = index + 1
                dataList.append(tmpDic)
        elif doRead == 2:
            if line == []:
                doRead = 0
            else:
                index = 0
                tmpDic = {}
                for i in line:
                    tmpDic[keys[index]] = i
                    index = index + 1
                dataList.append(tmpDic)
"""dataList 에서 폭염일수가 가장 많았던 연도를 찾아내서 출력 하는 실습"""
# dataList.pop(0)
# index = 0
# maxDays = 0
# maxYear = ''
# for data in dataList:
#     if float(data['연합계']) > maxDays:
#         maxDays = float(data['연합계'])
#         maxYear = data['연도']
# print("가장 폭염일수가 많았던 연도는: ", maxYear)
# print("가장 폭염일수가 많았던 연도의 폭염 일수는: ", maxDays)
"""폭염 종료일이 가장 늦은 해를 찾아내는 실습"""
dataList.pop(0)
dataList.pop(1)
dd = 0
yy = 0
for data in dataList:
    yymmddStr = data['종료일'].split('-')
    yymmdd = []
    for i in yymmddStr:
        try:
            yymmdd.append(int(i))
        except:
            print("append error")
    if yymmdd[2] > dd:
        dd = yymmdd[2]
        yy = yymmdd[0]
print('폭염 종료일 중 가장 늦은 일자는', dd)
print('폭염 종료일이 가장 늦었던 해는', yy)
    </script>
</body>
</html>
