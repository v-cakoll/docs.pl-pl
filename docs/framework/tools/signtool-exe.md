---
title: SignTool.exe (Narzędzie podpisu)
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
ms.openlocfilehash: 8ce31b1399700906d6d6e2a369dcfc4b61fe9646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180327"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (Narzędzie podpisu)
Narzędzie podpisywania to narzędzie wiersza polecenia, które cyfrowo podpisuje pliki, weryfikuje podpisy w plikach i oznacza pliki znacznikami czasu.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|`command`|Jedno z czterech`catdb`poleceń `Timestamp`( `Verify`, `sign`, , lub ), które określa operację do wykonania na pliku. Aby zapoznać się z opisem każdego polecenia, zobacz następną tabelę.|  
|`options`|Opcja, która modyfikuje polecenie. Oprócz opcji `/q` globalnych `/v` i opcji każde polecenie obsługuje unikatowy zestaw opcji.|  
|`file_name`|Ścieżka do pliku, który ma zostać podpisany.|  
  
 Poniższe polecenia są obsługiwane przez narzędzie podpisywania. Każde polecenie jest używane z odrębnym zestawem opcji, które wymieniono w odpowiednich sekcjach.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|`catdb`|Dodaje plik wykazu do bazy danych wykazów lub usuwa go z niej. Bazy danych wykazów służą do automatycznego wyszukiwania plików wykazu i są identyfikowane przez identyfikator GUID. Aby uzyskać listę opcji obsługiwanych `catdb` przez polecenie, zobacz [opcje polecenia catdb](signtool-exe.md#catdb).|  
|`sign`|Cyfrowo podpisuje pliki. Podpisy cyfrowe chronią pliki przed ingerencją osób niepowołanych i umożliwiają użytkownikom weryfikację podpisującego na podstawie certyfikatu podpisywania. Aby uzyskać listę opcji obsługiwanych `sign` przez polecenie, zobacz [Podpisz opcje polecenia](signtool-exe.md#sign).|  
|`Timestamp`|Oznacza pliki znacznikami czasu. Aby uzyskać listę opcji obsługiwanych `TimeStamp` przez polecenie, zobacz [Opcje polecenia sygnatury czasowej](signtool-exe.md#TimeStamp).|  
|`Verify`|Weryfikuje podpis cyfrowy plików, ustalając, czy certyfikat podpisywania został wystawiony przez zaufany urząd, czy certyfikat podpisywania został odwołany i, opcjonalnie, czy certyfikat podpisywania jest ważny dla określonych zasad. Aby uzyskać listę opcji obsługiwanych `Verify` przez polecenie, zobacz [Weryfikowanie opcji polecenia](signtool-exe.md#Verify).|  
  
 Poniższe opcje są stosowane do wszystkich poleceń narzędzia podpisywania.  
  
|Opcja globalna|Opis|  
|-------------------|-----------------|  
|**/q**|Nie wyświetla danych wyjściowych, jeśli działanie polecenia zakończy się pomyślnie, i wyświetla minimalne dane wyjściowe, jeśli działanie polecenia zakończy się niepowodzeniem.|  
|**/v**|Wyświetla pełne dane wyjściowe bez względu na to, czy polecenie zostanie wykonane pomyślnie, czy jego działanie zakończy się niepowodzeniem, a ponadto wyświetla komunikaty ostrzegawcze.|  
|**/debug**|Wyświetla informacje debugowania.|  
  
<a name="catdb"></a>
## <a name="catdb-command-options"></a>Opcje polecenia catdb  
 W poniższej tabeli wymieniono opcje, których można używać z poleceniem. `catdb`  
  
|Opcja polecenia Catdb|Opis|  
|------------------|-----------------|  
|`/d`|Określa, że domyślna baza danych wykazów jest aktualizowana. Jeśli nie `/d` jest `/g` używana żadna opcja, narzędzie podpisywanie aktualizuje komponent systemowy i bazę danych sterowników.|  
|`/g`*Identyfikator GUID*|Określa, że baza danych katalogu identyfikowana przez unikatowy identyfikator globalny *identyfikator jest* aktualizowana.|  
|`/r`|Usuwa określone wykazy z bazy danych wykazów. Jeśli ta opcja nie jest określona, narzędzie podpisywania dodaje określone wykazy do bazy danych wykazów.|  
|`/u`|Określa, że dla dodawanych plików wykazów unikatowe nazwy są generowane automatycznie. W razie potrzeby nazwy plików wykazów są zmieniane, aby zapobiec konfliktom nazw z istniejącymi plikami wykazów. Jeśli ta opcja nie jest określona, narzędzie podpisywania zastępuje wszelkie istniejące wykazy, które mają taką samą nazwę jak wykaz dodawany.|  
  
<a name="sign"></a>
## <a name="sign-command-options"></a>Podpisz opcje polecenia  
 W poniższej tabeli wymieniono opcje, których można używać z poleceniem. `sign`  
  
|Opcja polecenia Sign|Opis|  
|-------------------------|-----------------|  
|`/a`|Automatycznie wybiera najlepszy certyfikat podpisywania. Narzędzie podpisywania znajdzie wszystkie ważne certyfikaty, które spełniają wszystkie określone warunki, i wybierze ten, którego okres ważności jest najdłuższy. Jeśli ta opcja nie jest określona, narzędzie podpisywania spodziewa się znaleźć tylko jeden ważny certyfikat podpisywania.|  
|`/ac`  *Plik*|Dodaje dodatkowy certyfikat z *pliku* do bloku podpisu.|  
|`/as`|Dołącza ten podpis. Jeśli nie jest określony podpis podstawowy, ten podpis jest ustawiany jako podpis podstawowy.|  
|`/c`  *CertTemplateName*|Określa nazwę szablonu certyfikatu (rozszerzenie Microsoft) dla certyfikatu podpisywania.|  
|`/csp`  *Nazwa CSP*|Określa dostawcę usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego.|  
|`/d`  *Desc*|Określa opis podpisanej zawartości.|  
|`/du`  *Adres url*|Określa adres URL (Uniform Resource Locator) rozszerzonego opisu podpisanej zawartości.|  
|`/f`  *Plik SignCert*|Określa certyfikat podpisywania w pliku. Jeśli plik jest w formacie wymiany informacji osobistych (PFX) `/p` i jest chroniony hasłem, użyj opcji, aby określić hasło. Jeśli plik nie zawiera kluczy `/csp` prywatnych, użyj opcji i `/kc` opcji, aby określić nazwę kontenera CSP i klucza prywatnego.|  
|`/fd`|Określa algorytm tworzenia skrótu pliku na potrzeby tworzenia podpisów plików. Domyślnie jest to algorytm SHA1.|  
|`/i`  *Nazwa wystawy*|Określa nazwę wystawcy certyfikatu podpisywania. Ta wartość może być podciągiem całej nazwy wystawcy.|  
|`/kc`  *Nazwa programu PrivKeyContainer*|Określa nazwę kontenera kluczy prywatnych.|  
|`/n`  *Subjectname*|Określa nazwę podmiotu certyfikatu podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu.|  
|`/nph`|Jeśli jest obsługiwana, pomija skróty stron dla plików wykonywalnych. Wartość domyślna jest określana przez zmienną środowiskową SIGNTOOL_PAGE_HASHES i wersję pliku wintrust.dll. Ta opcja jest ignorowana dla plików innych niż PE.|  
|`/p`  *Hasło*|Określa hasło używane podczas otwierania pliku PFX. (Użyj `/f` opcji, aby określić plik PFX.|  
|`/p7`*Ścieżka*|Określa, że plik PKCS (Public Key Cryptography Standards) #7 jest generowany dla każdego określonego pliku zawartości. Pliki #7 PKCS są nazywane *path*\\*filename*.p7.|  
|`/p7ce` *Wartość*|Określa opcje dla podpisanej zawartości PKCS #7. Ustaw *wartość* na "Osadzone", aby osadzić podpisaną zawartość w pliku #7 PKCS lub "DetachedSignedData", aby utworzyć podpisaną część danych odłączony plik #7 PKCS. Jeśli `/p7ce` opcja nie jest używana, podpisana zawartość jest domyślnie osadzona.|  
|`/p7co`* \<>oid*|Określa identyfikator obiektu (OID), który identyfikuje podpisaną zawartość PKCS #7.|  
|`/ph`|Jeśli jest obsługiwana, generuje skróty stron dla plików wykonywalnych.|  
|`/r`  *Nazwa rootsubject*|Określa nazwę podmiotu certyfikatu głównego, z którym musi zostać połączony certyfikat podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu certyfikatu głównego.|  
|`/s`  *Storename*|Określa magazyn otwierany podczas wyszukiwania certyfikatu. Jeśli ta opcja nie `My` jest określona, magazyn jest otwarty.|  
|`/sha1`  *Mieszania*|Określa skrót SHA1 certyfikatu podpisywania. Skrót SHA1 jest zazwyczaj określany, jeśli wiele certyfikatów spełnia kryteria określone przez pozostałe przełączniki.|  
|`/sm`|Określa, że jest używany magazyn komputera, a nie magazyn użytkownika.|  
|`/t`  *Adres url*|Określa adres URL serwera znaczników czasu. Jeśli ta opcja `/tr`(lub) nie jest obecny, podpisany plik nie będzie oznaczony sygnaturą czasową. Jeśli oznaczanie znacznikiem czasu nie powiedzie się, jest generowane ostrzeżenie. Tej opcji nie można `/tr` używać z opcją.|  
|`/td`  *alg ( alg )*|Używany z `/tr` opcją żądania algorytmu skrótu używanego przez serwer sygnatury czasowej RFC 3161.|  
|`/tr`  *Adres url*|Określa adres URL serwera znaczników czasu RFC 3161. Jeśli ta opcja `/t`(lub) nie jest obecny, podpisany plik nie będzie oznaczony sygnaturą czasową. Jeśli oznaczanie znacznikiem czasu nie powiedzie się, jest generowane ostrzeżenie. Tej opcji nie można `/t` używać z opcją.|  
|`/u`  *Użycia*|Określa rozszerzone użycie klucza (EKU), które musi być obecne w certyfikacie podpisywania. Wartość Usage można określić za pomocą identyfikatora OID lub ciągu. Domyślna wartość Usage to „Code Signing” (1.3.6.1.5.5.7.3.3).|  
|`/uw`|Określa użycie funkcji weryfikacji składników systemu Windows (1.3.6.1.4.1.311.10.3.6).|  
  
 Aby zapoznać się z przykładami użycia, zobacz [Używanie funkcji SignTool do podpisywania pliku](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file).  
  
<a name="TimeStamp"></a>
## <a name="timestamp-command-options"></a>Opcje polecenia sygnatury czasowej  
 W poniższej tabeli wymieniono opcje, których można używać z poleceniem. `TimeStamp`  
  
|Opcja polecenia TimeStamp|Opis|  
|----------------------|-----------------|  
|`/p7`|Oznacza pliki PKCS #7 znacznikami czasu.|  
|`/t`  *Adres url*|Określa adres URL serwera znaczników czasu. Plik oznaczany znacznikiem czasu musi zostać wcześniej podpisany. Wymagana jest `/t` `/tr` opcja lub opcja.|  
|`/td`  *alg ( alg )*|Żąda algorytmu tworzenia skrótu używanego przez serwer znaczników czasu RFC 3161. `/td`jest używany `/tr` z opcją.|  
|`/tp`*indeks*|Sygnatury czasowe podpisu w *indeksie*.|  
|`/tr`  *Adres url*|Określa adres URL serwera znaczników czasu RFC 3161. Plik oznaczany znacznikiem czasu musi zostać wcześniej podpisany. Wymagana jest `/tr` `/t` opcja lub opcja.|  
  
 W przykładzie użycia zobacz [Dodawanie sygnatur czasowych do wcześniej podpisanych plików](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files).  
  
<a name="Verify"></a>
## <a name="verify-command-options"></a>Sprawdź opcje polecenia  
  
|Opcja polecenia Verify|Opis|  
|-------------------|-----------------|  
|`/a`|Określa, że w celu weryfikacji pliku można użyć wszystkich metod. Najpierw bazy danych wykazów są przeszukiwane w celu ustalenia, czy plik jest podpisany w wykazie. Jeśli plik nie jest podpisany w żadnym wykazie, narzędzie podpisywania próbuje zweryfikować podpis osadzony w pliku. Ta opcja jest zalecana w przypadku weryfikowania plików, które mogą, ale nie muszą, być podpisane w wykazie. Przykładami tych plików są pliki lub sterowniki systemu Windows.|  
|`/ad`|Znajduje wykaz przy użyciu domyślnej bazy danych wykazów.|  
|`/ag`*CatDBGUID ( CatDBGUID )*|Znajduje katalog w bazie danych katalogu, który jest identyfikowany przez *CatDBGUID*.|  
|`/all`|Weryfikuje wszystkie podpisy w pliku, który zawiera wiele podpisów.|  
|`/as`|Znajduje wykaz przy użyciu bazy danych wykazów składników systemu (sterowniki).|  
|`/c`*Plik CatFile*|Określa plik wykazu według nazwy.|  
|`/d`|Określa, że narzędzie podpisywania powinno drukować opis i adres URL opisu.|  
|`/ds`  *Indeks*|Weryfikuje podpis w określonej pozycji.|  
|`/hash`(`SHA1`&#124;`SHA256`)|Określa opcjonalny algorytm wyznaczania wartości skrótu, który ma być używany podczas wyszukiwania pliku w wykazie.|  
|`/kp`|Określa, że weryfikacja powinna być wykonywana przy użyciu zasad podpisywania sterowników trybu jądra.|  
|`/ms`|Używa wielu semantyk weryfikacji. Jest to domyślne zachowanie wywołania [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) w systemie Windows 8 lub wyższym.|  
|`/o` *Wersja*|Weryfikuje plik na podstawie wersji systemu operacyjnego. *Wersja* ma następującą *formę: PlatformID*:*VerMajor*. *VerMinor*. *BuildNumber*. *PlatformID* reprezentuje podstawową <xref:System.PlatformID> wartość elementu członkowskiego wyliczenia. **Ważne:**  Zaleca się `/o` użycie przełącznika. Jeśli `/o` nie zostanie określony, SignTool.exe może zwrócić nieoczekiwane wyniki. Na przykład jeśli przełącznik nie `/o` zostanie uwzględnione, katalogi systemowe, które poprawnie sprawdzają poprawność w starszym systemie operacyjnym, mogą nie sprawdzać poprawnie w nowszym systemie operacyjnym.|  
|`/p7`|Weryfikuje pliki PKCS #7. Żadne z istniejących zasad nie są używane do weryfikacji plików PKCS #7. Podpis jest sprawdzany i zostaje utworzony łańcuch dla certyfikatu podpisywania.|  
|`/pa`|Określa, że mają być używane domyślne zasady weryfikacji Authenticode. Jeśli `/pa` opcja nie jest określona, Narzędzie podpisywania używa zasad weryfikacji sterowników systemu Windows. Tej opcji nie można `catdb` używać z opcjami.|  
|`/pg`*PolitykaGUID*|Określa zasady weryfikacji według identyfikatora GUID. *PolicyGUID* odpowiada identyfikatorowi działania zasad weryfikacji. Tej opcji nie można `catdb` używać z opcjami.|  
|`/ph`|Określa, że narzędzie podpisywania powinno drukować i weryfikować wartości skrótu stron.|  
|`/r`*Nazwa rootsubject*|Określa nazwę podmiotu certyfikatu głównego, z którym musi zostać połączony certyfikat podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu certyfikatu głównego.|  
|`/tw`|Określa, że ma być generowane ostrzeżenie, jeśli podpis nie ma znacznika czasu.|  
  
 Aby zapoznać się z przykładami użycia, zobacz [Weryfikowanie podpisu pliku za pomocą funkcji SignTool](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature).  
  
## <a name="return-value"></a>Wartość zwracana  
 Kończąc działanie, narzędzie podpisywania zwraca jeden z poniższych kodów zakończenia.  
  
|Kod zakończenia|Opis|  
|---------------|-----------------|  
|0|Wykonywanie powiodło się.|  
|1|Wykonywanie nie powiodło się.|  
|2|Wykonanie zostało ukończone, ale zostały wygenerowane ostrzeżenia.|  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie dodaje plik wykazu MyCatalogFileName.cat do bazy danych składników systemu i sterowników. Opcja `/u` generuje unikatową nazwę, jeśli to konieczne, `MyCatalogFileName.cat`aby zapobiec zastąpieniu istniejącego pliku katalogu o nazwie .  
  
```console  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 Poniższe polecenie podpisuje plik automatycznie przy użyciu najlepszego certyfikatu.  
  
```console  
signtool sign /a MyFile.exe  
```  
  
 Poniższe polecenie podpisuje cyfrowo plik przy użyciu certyfikatu przechowywanego w chronionym hasłem pliku PFX.  
  
```console  
signtool sign /f MyCert.pfx /p MyPassword MyFile.exe  
```  
  
 Poniższe polecenie podpisuje cyfrowo plik i oznacza go sygnaturą czasową. Certyfikat użyty do podpisania pliku jest przechowywany w pliku PFX.  
  
```console  
signtool sign /f MyCert.pfx /t http://timestamp.digicert.com MyFile.exe  
```  
  
 Następujące polecenie podpisuje plik przy użyciu certyfikatu znajdującego się w `My` magazynie, który ma nazwę podmiotu `My Company Certificate`.  
  
```console  
signtool sign /n "My Company Certificate" MyFile.exe  
```  
  
 Poniższe polecenie podpisuje formant ActiveX i udostępnia informacje wyświetlane przez program Internet Explorer, gdy użytkownik jest monitowany o zainstalowanie tego formantu.  
  
```console  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html MyControl.exe  
```  
  
 Poniższe polecenie oznacza znacznikiem czasu plik, który jest już podpisany cyfrowo.  
  
```console  
signtool timestamp /t http://timestamp.digicert.com MyFile.exe  
```  
  
 Poniższe polecenie sprawdza, czy plik jest podpisany.  
  
```console  
signtool verify MyFile.exe  
```  
  
 Poniższe polecenie sprawdza plik systemowy, który może być podpisany w wykazie.  
  
```console  
signtool verify /a SystemFile.dll  
```  
  
 Następujące polecenie weryfikuje plik systemowy podpisany `MyCatalog.cat`w katalogu o nazwie .  
  
```console  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
