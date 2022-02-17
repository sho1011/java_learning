# String.format()

String str = "samples";
System.out.println(String.format("値は「%10s」です。", str));
    // 結果：値は「   samples」です。
System.out.println(String.format("値は「%-10s」です。", str));
    // 結果：値は「samples   」です。
System.out.println(String.format("値は「%.2s」です。", str));
    // 結果：値は「sa」です。
    
    
double num = 1.23456;
System.out.println(String.format("値は「%e」です。", num));
    // 結果：値は「1.234560e+00」です。
System.out.println(String.format("値は「%E」です。", num));
    // 結果：値は「1.234560E+00」です。
System.out.println(String.format("値は「%f」です。", num));
    // 結果：値は「1.234560」です。
System.out.println(String.format("値は「%.3f」です。", num));
    // 結果：値は「1.235」です。


Date c = new Date();
System.out.println(String.format("%tY年 %tm月 %td日", c, c, c));
    // 結果：2020年 01月 04日
System.out.println(String.format("%tH時 %tM分 %tS秒", c, c, c));
    // 結果：14時 23分 36秒

https://java-code.jp/173
https://techacademy.jp/magazine/19033#:~:text=%E3%80%8CString.format(%20)%E3%80%8D,%E6%95%B4%E5%BD%A2%E3%81%99%E3%82%8B%E3%80%8D%E3%81%AA%E3%81%A9%E3%81%8C%E3%81%82%E3%82%8A%E3%81%BE%E3%81%99%E3%80%82
