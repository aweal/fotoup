# fotoup в истории как и яндекс фото
Загрузка всех фоток из папки и перенос апрувленых фоток в другую директорию (при последующем запуске после разрывов не будет проблем что загружено что нет). Важно не указывать целевой каталог внутри источника (будут повторно загружены -см пример).


Использование:
	fotoup ИСТОЧНИК НАЗНАЧЕНИЕ

example:
	fotoup /home/aweal/foto/  /home/aweal/foto_`date +%F`

	!но не fotoup /home/aweal/foto/`date +%F` (будет загружать уже загруженные)


основано на:

https://github.com/svetlyak40wt/yafotkiuploader

и по сути это несколько строк:
cd /tmp && git clone https://github.com/svetlyak40wt/yafotkiuploader && cd /tmp/yafotkiuploader/
python2 virtualenv.py env && env/bin/pip install -r requirements.txt && . env/bin/activate
for FILENAME in `find "/home/aweal/foto/" -type f` ; do ./yaploader upload -a 75 "$FILENAME" && mv -v "$FILENAME" "/home/aweal/foto_`date +%F`" ; done
