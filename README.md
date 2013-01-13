xkcfinder
=========

kcfinder for XOOPS

kcfinder を XOOPS で利用可能にするライブラリ。

ckeditor4 等のWYSIWYGエディタと組み合わせて使用する。

サーバへの画像ファイル・アップロードとアップロードしたフォルダの閲覧・管理が可能となる。


## 使用方法

common/kcfinder/config.php

'uploadURL'はルートURLから上の部分を指定する事。デフォルトは$_SERVER["HTTP_HOST"]と同じ条件で設定してあるが、サブフォルダで動作させる時は/uploadsの前にフォルダ名を適宜編集する必要がある。

```
	'disabled' => false,
	'uploadURL' => "/uploads/kcfinder",
	'uploadDir' => dirname(dirname(dirname(__FILE__)))."/uploads/kcfinder",
```

エディタ側ckeditor4でも ckeditor4/class/Ckeditor4Utils.class の編集が必要。
以下、設定例

```
				//$finder = is_object($mObj)? $conf['xelfinder'] : '';
				$finder = is_object($mObj)? $conf['xelfinder'] : 'kcfinder';

//				$config['filebrowserBrowseUrl'] = XOOPS_URL . '/modules/' . $finder . '/manager.php?cb=ckeditor';
				$config['filebrowserBrowseUrl'] = XOOPS_URL . '/common/' . $finder . '/browse.php';
				$config['filebrowserImageUploadUrl'] = XOOPS_URL . '/common/' . $finder . '/upload.php?type=img';
```
