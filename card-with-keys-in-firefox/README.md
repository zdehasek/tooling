# tooling

BTW zkousim to s tim proID a moc to nejde, jakou mas verzi linuxu ?



ubuntu bionic na jednom a na druhem to vyssi uz nevim jak se jmenuje



takze LTS a pak tu 19.10 ?



ja mam prave 19.10



a nejak tam haprujou baliky



kdyby jsi mel ten navod byl bych moc rad



jo musis si backportovat repo



mmnt najdu to



diky moc 🙂



sudo echo "deb http://security.ubuntu.com/ubuntu xenial-security main" >> /etc/apt/sources.list
sudo apt-get update
sudo apt --fix-broken install
sudo dpkg -i libproidplus-gui_2.2.2-0_amd64.deb

timhle nainstalujes ten balik



pak ve firefoxu musis do trusted autority pridat tenhle certifikat



www.csas.cz/caims2.cer



predvolby -> soukromi a zabezpeceni > zobrazit certifikaty -> autority -> importovat



a pak pridat bezpecnostni zarizeni



predvolby -> soukromi a zabezpeceni -> bezpecnostni zarizeni -> nacist a vlozit /usr/lib/x86_64-linux-gnu/libproidqcm11.so



musis mit nainstalovanej ten pcsd



a pak restart



resp i pred restartem by jsi mel videt tohle



kdyz kliknes na prihlasit bude to po tobe chtit pin



pak uz staci jen ten restart a pak vyzkouset prihlaseni pres tu url



diky moc 🙂



nejak se mi tam rozbily baliky



ale to snad vyresim 🙂



Jo kdyz se ti poprvy nenainstalovaly musis pouzit to fix-broken



Pak uz je to easy



to jsem delal



dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb (--install):
 unable to install new version of '/lib/x86_64-linux-gnu/libpng12.so.0': No such file or directory
Processing triggers for libc-bin (2.30-0ubuntu2) ...



porad mi to pise tohle



to jsi tam asi nemel co ?



https://askubuntu.com/questions/1136302/can-not-install-libpng12-so-0-on-ubuntu-19-04-for-packet-tracert-7



tak mam reseni



kdyby jsi taky nahodou potreboval 🙂
12. 2. 2020 0:29



shit



tak nevidim tak uplne vsechno



jako ty



a na pin se me to nepta



a pridal sis tam tu ctecku jo?



pcscd nainstalovany mam



jojo



a kdyz das prihlasit tak se te to nezepta na pin?



co myslis das prihlasit ?



kdyz mas ve ff ty bezpecnostni zarizeni



a kliknes na to co jsi pridal



je pak mozny kliknout na tlacitko prihlasit



jo me to prihlasit ani nejde macknout



a mas vybrane spravne zarizeni? ono tam jsou 2 vytvorene by default



no dal jsem tam tu url od tebe



musi tam byt to oznaceni PROid



jak na tom mojem screenu



ls -la /usr/lib/x86_64-linux-gnu/libproidqcm11.so
lrwxrwxrwx 1 root root 54 lis 15  2017 /usr/lib/x86_64-linux-gnu/libproidqcm11.so -> /usr/lib/x86_64-linux-gnu/libproidqcm11.so.1.2.17.1020



a je tam ten soubor nakopirovanej jo? 😀



to me ted tak napadlo 😀



jak myslis nakopirovanej?



ls -la /usr/lib/x86_64-linux-gnu/libproidqcm11.so
lrwxrwxrwx 1 root root 54 lis 15  2017 /usr/lib/x86_64-linux-gnu/libproidqcm11.so -> /usr/lib/x86_64-linux-gnu/libproidqcm11.so.1.2.17.1020
root@DELLete:~#



mam to stejny jak ty



ok takze driver tam je



a co mas teda v tech bezpecnostnich zarizenich ve ff



?



to vypada jako bys tam nemel ten driver



klikni na load



a vloz tam tu cestu



no to jsem delal predtim



a ted uz to nejde



podruhe



hh blbej dotaz 😀



mas tam strcenou kartu 😀



?



jojo



a blika



mela by svitit



kdyz jsem ji vytahnul



vypadalo to presne jak na tom tvojem screenu



jakmile ji tam strcim objevi se mi ty dalsi informace



hm...takze on na ni nevydi



vidi jen ten driver



tak mmnt jeste jedna vec na otestovani



nainstaluj si gnutls-bin



pak pust p11tool --list-tokens



root@DELLete:/home/zdehasek/Downloads# p11tool --list-tokens
Token 0:
	URL: pkcs11:model=p11-kit-trust;manufacturer=PKCS%2311%20Kit;serial=1;token=System%20Trust
	Label: System Trust
	Type: Trust module
	Flags: uPIN uninitialized
	Manufacturer: PKCS#11 Kit
	Model: p11-kit-trust
	Serial: 1
	Module: p11-kit-trust.so


Token 1:
	URL: pkcs11:model=Gemalto%20TOP%20GX4;manufacturer=Monet%2B%2Ca.s.;serial=9203801209490388;token=ProID%2B%209203801209490388
	Label: ProID+ 9203801209490388
	Type: Hardware token
	Flags: RNG, Requires login
	Manufacturer: Monet+,a.s.
	Model: Gemalto TOP GX4
	Serial: 9203801209490388
	Module: libproidcm11.so



vypada ze tam neco je



ok zkus p11tool --list-all-certs 'pkcs11:model=Gemalto%20TOP%20GX4;manufacturer=Monet%2B%2Ca.s.;serial=9203801209490388;token=ProID%2B%209203801209490388'



melo by ti to vypsat certifikaty na karte



a porad ctecka blika nebo uz jen sviti?



jop to dela



a ctecta sivit



ctecka



pokazdy kdyz se sni neco dela tak sviti



tak zkus vypnout/zapnout ff



jestli se to tam uz objevi spravne



zkosim a nic



hmm divny



jo ted me napada mozna mas mirne jinou ctecku zkus tam ten druhy driver



mmnt najdu tu adresu



/usr/lib/x86_64-linux-gnu/libproidcm11.so



vim ze jsem tam puvodne pridaval oba a ted si nejsem jisty ktery byl ten spravny



YES



uz se me to pta na pin



diky moc 🙂



kamo jsi borec