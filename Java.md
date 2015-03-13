The netbeans protocol (see ':help nb' from inside vim, or see http://vimdoc.sourceforge.net/htmldoc/netbeans.html) is used to communicate with a TCP socket server that is responsible for aggregating, queuing and transforming messages sent from  vim and passing these messages on to accessibility technology software running on the same machine (the phonim server host machine).

The phonim server  relies heavily on the Vimoir project (see http://vimoir.googlecode.com/) to handle communication to and from vim by handling the Netbeans protocol spesifics.

The cross platform phonemic project (see http://phonemic.sourceforge.net/) is used to handle the last phase -- communicating with the native (OS provided) or third party accessibility technology.

## Details ##