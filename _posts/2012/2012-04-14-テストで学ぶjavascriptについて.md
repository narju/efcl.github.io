---
title: テストで学ぶJavaScriptについて
author: azu
layout: post
permalink: /2012/0414/res3059/
SBM_count:
  - '00058<>1355446787<>55<>0<>2<>1<>0'
dsq_thread_id:
  - 649211688
categories:
  - javascript
tags:
  - javascript
  - test
---
[A Test-Driven JS Assessment][1] というテストを通るようなコードを書いて、JavaScriptを学ぶものが公開されていたので、それの紹介です。  
[JS Assessment][1]は最初に失敗するテストが用意されていて、そのテストコードを通るような関数などを書いていってJavaScriptの力試し、学習をするものです。

簡単にやり方を書くと、Node環境を用意した状態で

`git clone https://github.com/rmurphey/js-assessment.git`などで、リポジトリをダウンロードして、  
ダウンロードしたディレクトリ内で、 nodeを使って以下のようコマンドを実行してテストが実行できるローカルサーバを立ち上げます。

    npm install
    node bin/serve

実行した状態で <http://localhost:4444> というURLに行けば、Mochaで書かれたテストが走った結果が表示されます。

テストを通るコードの書き方は、node bin/serve を実行した時に表示されますが、

<pre>To work on the tests, open a browser and visit http://localhost:4444. Then,
edit the tests in the files in the tests/app directory, reloading your browser
to see whether the tests are passing.

Each test will look something like this:

    it("you should be able to return a truthy value", function() {
      // define a function for fn so that the following will pass
      expect(fn()).to.be.ok();
    });

In the case of the above test, you'd need to define a value for fn (by default,
fn is a function that does nothing):

    it("you should be able to return a truthy value", function() {
      // define a function for fn so that the following will pass
      fn = function() {
        return true;
      };
      expect(fn()).to.be.ok();
    });

For some tests, the instructions will be more involved; in those cases, the
inline comments should give you the details you need.</pre>

と書かれているように、tests/appにあるコードを編集して、それぞれのitの中にテストケースを通るような関数を定義したりして、  
<http://localhost:4444>にアクセスして全てのテストが通るようにするのが目的です。

e.g) [solve Arrays Test · c955516 · azu/js-assessment][2]

<img title="arrays.js - js-assessment - [~_workspace_js_js-assessment].png" src="https://efcl.info/wp-content/uploads/2012/04/arrays.js-js-assessment-_workspace_js_js-assessment.png" border="0" alt="Arrays js  js assessment   ~ workspace js js assessment" width="600" height="400" />

テストコードはNodeで動くテストフレームワークの[Mocha][3]を使って書かれています。  
expectで期待してる動作は結構そのまま分かる感じなので、itのテスト文とあわせれば、大体期待してる挙動はわかるとは思いますが、  
[Mocha][3]自体の挙動も少し知っておいたほうがいい場合もあります。

*   [ryu22eBlog : Node.jsのテスティングフレームワーク「Mocha」（前編）][4] 

用意されてるテストはArrayの機能のテストやBackboneを使ったViewのテスト、非同期のテスト等が入っています。

これで、[A Test-Driven JS Assessment][1]の紹介は終わりですが、これ見た時に[禅の公案（Koan）][5]に何か似てるなとか思った。  
JavaScriptでは

*   [liammclennan/JavaScript-Koans][6] ( [javascript-koans &#8211; Javascript learning tool. &#8211; Google Project Hosting][7] )
*   [禅の公安スタイルでCoffeeScriptを学ぶ「coffeescript-koans」 &#8211; にのせき日記][8] 

あたりが知られてそうな気がします。(他にも色々あるみたいだけど [Search · Koans Javascript][9] )   
Koanとは以下のような穴埋め用のテストがかかれていて、そのテストを正しく書いてプログラミングを学べるものです。

<pre><code lang="javasript">test("not", function() {
    not(__, 'what is a false value?');
});</code></pre>

という穴埋め問題だったら

<pre><code lang="javasript">test("not", function() {
    not(false, 'what is a false value?');
});</code></pre>

のように、穴埋めするという感じのものです。

Koanと[JS Assessment][1]を比較すると、Koanは穴埋めという要素が強くてロジックなどは用意されてる感じになっています。  
一方 、[A Test-Driven JS Assessment][1]はテストだけ書かれていて、ロジックなどを書いてそのテストを通るような関数を書くというものになっています。  
似ているところもありますが、やりたいことは逆な感じなので、[A Test-Driven JS Assessment][1]の場合は人によって答えが全然違うという事もありえて、  
実際のテストファーストなものを書くのに近い感じになっていそうです。

これを書きながら、JavaScriptを学ぶ時に、最初からテストと絡めて学習したほうが良い感じになるのかなということについて考えていました。  
実際に新人教育とかでそういう事をしている[会社][10]さん等の成果とかを聞いてみたいですね。

*   [A Baseline for Front-End Developers &#8211; Adventures in JavaScript Development][11]
*   [TestFirst.org &#8211; The Home of Test-First Teaching][12]

 [1]: https://github.com/rmurphey/js-assessment
 [2]: https://github.com/azu/js-assessment/commit/c955516d4a66de510585e50f7811253363422e8a
 [3]: http://visionmedia.github.com/mocha/
 [4]: http://blog.livedoor.jp/ryu22e/archives/65636256.html
 [5]: http://el.jibun.atmarkit.co.jp/rails/2011/01/koan-3c38.html
 [6]: https://github.com/liammclennan/JavaScript-Koans
 [7]: http://code.google.com/p/javascript-koans/
 [8]: http://d.hatena.ne.jp/ninoseki/20111023/1319369396
 [9]: https://github.com/search?langOverride=&q=Koans+Javascript&repo=&start_value=1&type=Repositories&utf8=%E2%9C%93
 [10]: http://tech.kayac.com/
 [11]: http://rmurphey.com/blog/2012/04/12/a-baseline-for-front-end-developers/
 [12]: http://testfirst.org/
