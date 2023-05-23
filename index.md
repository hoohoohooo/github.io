<!DOCTYPE html>
<html>
<head>
</head>
  <body>
      <script src="https://js.bootpay.co.kr/bootpay-4.3.1.min.js" type="application/javascript"></script>
      <script>
          BootPay.request({
              price: '3000',
              application_id: "646c3b603049c8001bf8be2f",
              name: '블링블링 마스카라',
              pg: 'nicepay',
              method: 'card',
              show_agree_window: 0,
              items: [
                  {
                      item_name: '나는 아이템',
                      qty: 1,
                      unique: '123',
                      price: 3000,
                  }
              ],
              order_id: '고유order_id_1234',
          }).error(function (data) {

              console.log(data);
          }).cancel(function (data) {

              console.log(data);
          }).close(function (data) {

              console.log(data);
          }).done(function (data) {

              console.log(data);
          });
      </script>
  </body>
</html>
