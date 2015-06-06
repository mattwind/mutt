# mutt
The Mutt E-Mail Client <http://www.mutt.org>

Version 1.5.23 with sidebar and trash patches. Support IMAP, POP, SMTP and header cache.

### Prerequisites
https://github.com/mattwind/tokyocabinet

### How to compile and install

    git clone https://github.com/mattwind/mutt.git
    cd ./mutt/src
    ./configure --with-homespool=/var/spool/mail \
    --sysconfdir=/etc \
    --prefix=/usr \
    --with-docdir=/usr/share/doc/mutt-1.5.23 \
    --enable-pop --enable-smtp --enable-imap \
    --with-sasl --with-ssl --with-regex \
    --enable-hcache --without-bdb --without-gdbm --with-tokyocabinet \
    CPPFLAGS=-I/usr/local/include LDFLAGS=-L/usr/local/lib &&
    make

Test before installation
  
    ./mutt

If everything looks good
  
    make install

### Configure the Mutt Mail Client

    mkdir ~/.mutt
    touch ~/.muttrc
    touch ~/.mutt/aliases
    wget -q -O ~/.mutt/aliases.sh https://raw.githubusercontent.com/mattwind/mutt/master/scripts/aliases.sh
    wget -q -O ~/.muttrc https://raw.githubusercontent.com/mattwind/mutt/master/configs/muttrc

Make sure to edit the YOUR_USERNAME, YOUR_PASSWORD and YOUR NAME placeholders. This is just an example of the .muttrc config file to get you started. 

    vi ~/.muttrc
