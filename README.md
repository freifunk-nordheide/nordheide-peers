# Git-Hook anlegen
# ================
# um zu verhindern, dass man eine falsche fastd-key-Datei eincheckt:
# 
# wget https://raw.githubusercontent.com/freifunk-kiel/fastd-git-hook/master/git/hooks/pre-commit -O fastd-peer-keys/.git/hooks/pre-commit
# 
# und ausführbar machen:
# 
# chmod +x fastd-peer-keys/.git/hooks/pre-commit
#
#
# Fehler finden
# =============
#   mit diesem Befehl kann man sich alle Zeilen anzeigen, die nicht mit einer raute anfangen 
#   und die nicht dem standard entsprechen:
#   
#       cat * | grep -v -E "^\s*key\s+\"\w{64}\";\s*(#.*)*$" | grep -v -E "(^\s*#|^\s*remote|^$)"
#   
#   # Doppelte keys finden
#     
#     Dies sollte keine keys mehr auflisten:
#     
#       cat *|grep key|sed -e 's/#.*$//g; s/ \+/ /g; s/^ //g; s/ $//g'|sort|uniq -c|sort|tail|grep -v "1 key"
#     
#     siehe https://issues.freifunk.in-kiel.de/projects/ffki-keys/wiki
#   
#   # Grossbuchstaben in kleine umbenennen
#     
#     for f in *; do NEW="$(echo $f | tr '[A-Z]' '[a-z]')"; if [ "$f" != "$NEW" ]; then git mv -v $f $NEW; fi; done; git mv -v _readme _README

