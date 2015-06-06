# mutt
The Mutt E-Mail Client

Version 1.5.23 with sidebar and trash patches. IMAP, POP, and SMTP support with hcache enabled.

### Prerequisites
https://github.com/mattwind/tokyocabinet

### How to compile and install
git clone https://github.com/mattwind/mutt.git

    ./configure --with-homespool=/var/spool/mail /
    --sysconfdir=/etc /
    --prefix=/usr /
    --with-docdir=/usr/share/doc/mutt-1.5.23 /
    --enable-pop --enable-smtp --enable-imap /
    --with-sasl --with-ssl --with-regex /
    --enable-hcache --without-bdb --without-gdbm --with-tokyocabinet /
    CPPFLAGS=-I/usr/local/include LDFLAGS=-L/usr/local/lib /
    make

Test before installation
  
    ./mutt

If everything looks good
  
    make install

