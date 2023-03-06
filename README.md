# RFC2231, RFC2047
日本語のファイル名をMIMEヘッダーの`Content-Disposition`向けにエンコードする例題

* [RFC2231](https://www.ietf.org/rfc/rfc2231.txt)
* [RFC2047](https://www.ietf.org/rfc/rfc2047.txt)

## 例題

```4d
$RFC:=cs.RFC2231.new()
$disposition:=$RFC.encode("ascii.日本語.日本語.日本語.日本語.日本語.🌀.🌀.🌀.🌀.file.name")
```

* 結果

```
attachment;
	filename*0=utf-8'ja'ascii.%E6%97%A5%E6%9C%AC%E8%AA%9E.%E6%97%A5%E6%9C%AC%E8%AA%9E.%E6%97%A5%E6%9C%AC%E8%AA%9E.%E6%97%A5%E6%9C%AC%E8%AA%9E.%E6%97%A5%E6%9C%AC%E8%AA;
	filename*1=%9E.%ED%BC%80.%ED%BC%80.%ED%BC%80.%ED%BC%80.file.name
```

```4d
$RFC:=cs.RFC2047.new()
$filename:=$RFC.encode("ascii.日本語.日本語.日本語.日本語.日本語.🌀.🌀.🌀.🌀.file.name")
```

* 結果

```
=?utf-8?B?YXNj?=
	=?utf-8?B?aWku5pel5pys6KqeLuaXpeacrOiqni7ml6XmnKzoqp4u5pel5pys6Kqe?=
	=?utf-8?B?LuaXpeacrOiqni7wn4yALvCfjIAu8J+MgC7wn4yALmZpbGUubmFtZQ==?=
```
