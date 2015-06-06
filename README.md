# mutt
The Mutt E-Mail Client <http://www.mutt.org>

Version 1.5.23 with sidebar and trash patches. Support IMAP, POP, SMTP and header cache.

### Prerequisites
DB for header cache (required) 
https://github.com/mattwind/tokyocabinet

GnuGP (optional)
http://dev.mutt.org/trac/wiki/MuttGuide/UseGPG

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
    CPPFLAGS=-I/usr/local/include LDFLAGS=-L/usr/local/lib
    make

Test before installation
  
    ./mutt

If everything looks good
  
    make install

### Configure the Mutt Mail Client

    mkdir ~/.mutt
    touch ~/.muttrc
    touch ~/.mutt/cache/headers
    touch ~/.mutt/cache/bodies
    touch ~/.mutt/certificates
    touch ~/.mutt/aliases
    wget -q -O ~/.mutt/aliases.sh https://raw.githubusercontent.com/mattwind/mutt/master/scripts/aliases.sh
    wget -q -O ~/.muttrc https://raw.githubusercontent.com/mattwind/mutt/master/configs/muttrc

Make sure to edit the YOUR_USERNAME, YOUR_PASSWORD and YOUR NAME placeholders. This is just an example of the .muttrc config file to get you started. 

    vi ~/.muttrc

### Macros

My default .muttrc config comes with some macros.

    i Star thread as important
    R Replay all to current thread
    y Archive current thread
    d Send to trash (IMAP)
    gi Goto Inbox
    ga Goto All Mail
    gs Goto Starred Mail
    gd Goto Drafts
    gl View labels
    CN Goto Next Folder in sidebar
    CP Goto Previous Folder in sidebar
    CO Open Folder in sidebar
    p Change PGP settings
    h Toggle headers while viewing thread
    
### Moving Around

    j or Down       next-entry      move to the next entry
    k or Up         previous-entry  move to the previous entry
    z or PageDn     page-down       go to the next page
    Z or PageUp     page-up         go to the previous page
    = or Home       first-entry     jump to the first entry
    * or End        last-entry      jump to the last entry
    q               quit            exit the current menu
    ?               help            list all keybindings for the current menu

### Sending Mail

The following bindings are available in the index for sending messages.

    m       compose         compose a new message
    r       reply           reply to sender
    R       group-reply     reply to all recipients
    L       list-reply      reply to mailing list address
    f       forward         forward message
    b       bounce          bounce (remail) message
    ESC k   mail-key        mail a PGP public key to someone

Once you have finished editing the body of your mail message, you are returned to the compose menu. The following options are available:

    a       attach-file             attach a file
    A       attach-message          attach message(s) to the message
    ESC k   attach-key              attach a PGP public key
    d       edit-description        edit description on attachment
    D       detach-file             detach a file
    t       edit-to                 edit the To field
    ESC f   edit-from               edit the From field
    r       edit-reply-to           edit the Reply-To field
    c       edit-cc                 edit the Cc field
    b       edit-bcc                edit the Bcc field
    y       send-message            send the message
    s       edit-subject            edit the Subject
    f       edit-fcc                specify an ``Fcc'' mailbox
    p       pgp-menu                select PGP options
    P       postpone-message        postpone this message until later
    q       quit                    quit (abort) sending the message
    w       write-fcc               write the message to a folder
    i       ispell                  check spelling (if available on your system)
    ^F      forget-passphrase       whipe PGP passphrase from memory

### Status Flags

In addition to who sent the message and the subject, a short summary of the disposition of each message is printed beside the message number.

    D message is deleted (is marked for deletion)
    d message have attachments marked for deletion
    K contains a PGP public key
    N message is new
    O message is old
    P message is PGP encrypted
    r message has been replied to
    S message is PGP signed, and the signature is succesfully verified
    s message is PGP signed
    ! message is flagged
    * message is tagged


