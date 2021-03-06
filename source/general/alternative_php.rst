#################################
ビューファイルでの PHP の代替構文
#################################

CodeIgniter の :doc:`テンプレートエンジン
<../libraries/parser>` を利用しない場合、ビューファイルでは純粋な PHP を使うことになります。
これらのファイルの PHP コードを最小限にするために、
そしてより簡単にコードブロックを識別できるように、 PHP の制御構造に関する代替構文と
echo の短縮構文を使用することをおすすめします。
この構文に精通していないなら、それはあなたのコードから波括弧を排除し、
「 echo 」の文を排除することができます。

自動ショートタグのサポート
==========================

.. note:: このページで説明されている構文がサーバで動作しないことがわかった場合、
	おそらく PHP の ini ファイルで「ショートタグ」が無効になっています。
	CodeIgniter では必要に応じて、オンザフライでショートタグを書き換えます。
	あなたのサーバがサポートしていない場合でも、その構文を使用することができるようにするためです。
	この機能は *config/config.php* ファイルで有効にすることができます。

この機能を使用する場合、 PHP のエラーがビューファイルで発生した場合、
エラーメッセージや行番号には正確なものは表示されませんのでご注意ください。
かわりに、すべてのエラーは
``eval()`` のエラーとして表示されます。

echoのかわりとなるもの
======================

通常、変数をエコーもしくはプリントアウトする場合、この操作を行います::

	<?php echo $variable; ?>

代替構文を使用すると、このように行うことができます::

	<?=$variable?>

代替の制御構造
==============

if 、 for 、 foreach と while といった制御構造について簡略化した形式で記述することができます。
これは ``foreach`` を使用した場合の例です::

	<ul>

	<?php foreach ($todo as $item): ?>

		<li><?=$item?></li>

	<?php endforeach; ?>

	</ul>

波括弧がないことに注意してください。そのかわりに、波括弧は
``endforeach`` に置き換えられています。上に列挙した制御構造にはそれぞれ、
同様の閉じ構文があります: ``endif`` 、 ``endfor`` 、 ``endforeach`` 、および ``endwhile``

また、各構造のうしろにはセミコロンを使用するのではなく、かわりにコロンがあることに注意してください
(ただし最後のものを除く) 。これは重要です！

``if``/``elseif``/``else`` を使用した別の例です。コロンに注意してください::

	<?php if ($username === 'sally'): ?>

		<h3>こんにちはサリー</h3>

	<?php elseif ($username === 'joe'): ?>

		<h3>こんにちはジョー</h3>

	<?php else: ?>

		<h3>こんにちは知らない人</h3>

	<?php endif; ?>
