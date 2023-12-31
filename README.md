# RemoveEndOfAudio
# ●概要

このプログラムは、Vegas Pro 21.0 のスクリプトです。  
このスクリプトを使用すると、タイムラインに配置してある特定のトラックのすべてのオーディオの後ろを指定時間削除できます。



# ●背景

みてねから画像や動画をダウンロードして動画を作成したり、ブルーレイに焼いたりする際に、いくつか課題があります。
課題の一つに、特定のiPhone(Note1) （や一部のデジカメ）で撮影した動画をタイムラインに配置すると、レンダリング後にそのファイル以降の音が無音になってしまう（音量が非常に小さくなってしまう）問題があります（Note2）。

音が出なくなる動画の1つ前の動画ファイルの音声の最後には、DC のようなノイズが乗っていることが多いです。
DC が乗っているのだから HPF をかければよさそうにも思えますが、HPF をかけても、治るときと治らないときがあります(Note3)。

原因は不明ですが、対症療法として、DC の部分をカットすれば症状は治ります。
大量にある動画の DC の部分を手作業でカットするのは大変なので、トラックにあるすべてのオーディオファイルの後ろを一括して削除します。


Note1:
・iPhone13 miniで撮影した動画では発生し、iPhone11 Proで撮影した動画では（ほとんど）発生しません

Note2:
・この問題は、トラックのコンプ、リミッターをかけると発生します。トラックのコンプ、リミッターをバイパスすれば発生しません。

Note3:
・レンダリングのたびに再現性がないようにも見えます。（ちゃんと追及できていません）



# ●動画作成手順

1)みてねからファイルをダウンロードする

  https://github.com/miworky/miteneDownloader

を使用してダウンロードしてください。
  ダウンロードしたファイルは、「YYYY-MM-DDThhmmss_みてねの1つめのコメント」というファイル名になります。
  
2)ダウンロードしたファイルを Vegas Pro のメディアプールに取り込み、タイムラインに貼り付けます。

　ダウンロードしたファイル名に日付が含まれているので、これだけでみてねからダウンロードしたファイルを撮影日時順にタイムラインに配置できます。
 　画像・動画は Track 2 に追加してください。
  
3)撮影日とコメントからテロップを作成します

　https://github.com/miworky/Vegas_AddTextEventFromFilename

を使用すると自動でテロップを追加できます。テロップは Track 1 に作成されます。

4)オリジナルの高解像度のファイルに差し替えます

       https://github.com/miworky/Vegas_ReplaceMediaFiles

を使用すると、自動でオリジナルの高解像度のファイルに差し替えできます。

5)お好きな BGM を貼り付けます

   https://github.com/miworky/Vegas_AddMusic
   
   を使用すると画像の部分に自動で BGM を追加できます。

6)iPhone で撮影した動画のオーディオを別のトラックに移します

  iPhone で撮影した動画の音量は小さいので、いい感じに補正します。

7)iPhone で撮影した動画のオーディオの後ろを削除します（本プログラムを使用します）

8)動画として書き出したり、ブルーレイに焼いたりします。

9)テロップの時刻と内容をテキストファイルに書き出します

  https://github.com/miworky/Vegas_ExportTextEvent

　を使用すると自動でテロップの時刻と内容をテキストファイルに書き出せます。


# ●デプロイ方法

C:\ProgramData\VEGAS Pro\Script Menu

に以下のファイルをコピーします：

RemoveEndOfAudio.cs


# ●実行方法

1)Vegas Pro 21.0 から本スクリプトを実行します

2)ダイアログが表示されるので以下を入力します：

Music Track No(1-base): 削除したいオーディオのあるトラック番号

Time to remove(ms):     削除する時間

3)ファイル選択ダイアログが開くので、作成するログのファイル名を指定します

4)しばらく時間が経った後に、「終了しました」というポップアップが開けば終了です

