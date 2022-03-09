# スレッドとは
スレッドとは、1つの処理の流れの単位
例えば、コンビニでは、レジが1つだと行列が席るが複数あれば対応できる
ここでいうコンビニがプログラムで、店員がスレッド

# 抽象クラスThreadを継承してthreadを生成する方法

class ThreadSample extends Thread {
    public void run() {
        System.out.println("スレッドで動いてまーす");
    }
}
スレッドを動かすには、このThreadを継承したクラスのインスタンスを生成し、startメソッドを呼び出します。これだけで、新しいスレッドが生成され、そのスレッドでrunメソッドへ記述した処理を動かせられます

# スレッドはstart メソッドを呼び出したらrunメソッドを実行する

class ThreadExecutor {
    public static void main(String[] args) {
        ThreadSample t = new ThreadSample();
        t.start();
    }
}
さっそくThreadExecutorを動かしてみると、以下のような出力になるでしょう。おめでとうございます。見事、スレッドを使えました。

実行結果

スレッドで動いてまーす
ここで、プログラム上ではThreadSampleのrunを呼び出してもいないのに、文字が表示されました。つまり、スレッドがrunメソッドを自動で呼び出してくれた、ということですね。

# Runnableインターフェイスをinplementsしてスレッドを生成する方法（現実的らしい）
・Runnableインターフェイスをinplementsしてものにはrun()メソッドを記述する
class RunnableSample implements Runnable {
    public void run() {
・スレッドを動かすコードで、Runnbaleオブジェクト生成して、スレッドオブジェクトの引数にRunnbaleを入れる
RunnableSample r = new RunnableSample();
Thread t = new Thread(r);

------
さて、実際のプログラムを見てみましょう。RunnableSampleはRunnableを実装しています。やっていることはThreadを継承した場合と同じで、runメソッドの実装があるだけです。

RunnableSample.java

class RunnableSample implements Runnable {
    public void run() {
        String threadName = Thread.currentThread().getName();
        System.out.println("スレッド" + threadName + "で動いてまーす");
    }
}
今回は、runメソッドの中で「Thread.currentThread().getName()」でスレッドの名前を取得しています。RunnableはThreadではないので、Thread.getName()を直接使えないからです。

RunnableSampleのインスタンスを生成し、Runnableを引数に取るThreadのコンストラクタへ渡してThreadのインスタンスを生成します。その後、Threadのstartメソッドを呼び出します。

ThreadExecutor.java

class ThreadExecutor {
    public static void main(String[] args) {
        RunnableSample r = new RunnableSample();
        Thread t = new Thread(r); // Runnableをスレッドに渡してインスタンスを生成する
        t.start();
    }
}
結果は、例えば以下となります。

実行結果

スレッドThread-0で動いてまーす
RunnableSample.runをプログラム上からは呼び出していませんが、実際には呼び出されています。これはThreadを継承した時と同じように、スレッドからrunメソッドが呼び出されたのです。


# 参照
https://www.bold.ne.jp/engineer-club/java-thread
