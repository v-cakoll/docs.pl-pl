---
title: SignTool.exe (Narzędzie podpisu)
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
ms.openlocfilehash: cb0aca3b527c16a7abf984952795a673948775dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104646"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (Narzędzie podpisu)
Narzędzie podpisywania to narzędzie wiersza polecenia, które cyfrowo podpisuje pliki, weryfikuje podpisy w plikach i oznacza pliki znacznikami czasu.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|`command`|Jedno z czterech poleceń (`catdb`, `sign`, `Timestamp`lub `Verify`), które określa operację do wykonania na pliku. Aby zapoznać się z opisem każdego polecenia, zobacz następną tabelę.|  
|`options`|Opcja, która modyfikuje polecenie. Oprócz globalnych `/q` i `/v`, każde polecenie obsługuje unikatowy zestaw opcji.|  
|`file_name`|Ścieżka do pliku, który ma zostać podpisany.|  
  
 Poniższe polecenia są obsługiwane przez narzędzie podpisywania. Każde polecenie jest używane z odrębnym zestawem opcji, które wymieniono w odpowiednich sekcjach.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|`catdb`|Dodaje plik wykazu do bazy danych wykazów lub usuwa go z niej. Bazy danych wykazów służą do automatycznego wyszukiwania plików wykazu i są identyfikowane przez identyfikator GUID. Aby uzyskać listę opcji obsługiwanych przez polecenie `catdb`, zobacz [Opcje polecenia Catdb](signtool-exe.md#catdb).|  
|`sign`|Cyfrowo podpisuje pliki. Podpisy cyfrowe chronią pliki przed ingerencją osób niepowołanych i umożliwiają użytkownikom weryfikację podpisującego na podstawie certyfikatu podpisywania. Aby uzyskać listę opcji obsługiwanych przez polecenie `sign`, zobacz [Opcje polecenia Sign](signtool-exe.md#sign).|  
|`Timestamp`|Oznacza pliki znacznikami czasu. Aby uzyskać listę opcji obsługiwanych przez polecenie `TimeStamp`, zobacz [Opcje polecenia timestamp](signtool-exe.md#TimeStamp).|  
|`Verify`|Weryfikuje podpis cyfrowy plików, ustalając, czy certyfikat podpisywania został wystawiony przez zaufany urząd, czy certyfikat podpisywania został odwołany i, opcjonalnie, czy certyfikat podpisywania jest ważny dla określonych zasad. Aby uzyskać listę opcji obsługiwanych przez polecenie `Verify`, zobacz temat [Sprawdzanie opcji polecenia](signtool-exe.md#Verify).|  
  
 Poniższe opcje są stosowane do wszystkich poleceń narzędzia podpisywania.  
  
|Opcja globalna|Opis|  
|-------------------|-----------------|  
|**parametru**|Nie wyświetla danych wyjściowych, jeśli działanie polecenia zakończy się pomyślnie, i wyświetla minimalne dane wyjściowe, jeśli działanie polecenia zakończy się niepowodzeniem.|  
|**przełącznika**|Wyświetla pełne dane wyjściowe bez względu na to, czy polecenie zostanie wykonane pomyślnie, czy jego działanie zakończy się niepowodzeniem, a ponadto wyświetla komunikaty ostrzegawcze.|  
|**/debug**|Wyświetla informacje debugowania.|  
  
<a name="catdb"></a>   
## <a name="catdb-command-options"></a>Opcje polecenia catdb  
 Poniższa tabela zawiera listę opcji, które mogą być używane z poleceniem `catdb`.  
  
|Opcja polecenia Catdb|Opis|  
|------------------|-----------------|  
|`/d`|Określa, że domyślna baza danych wykazów jest aktualizowana. Jeśli `/d` ani opcja `/g` nie jest używana, narzędzie podpisywania aktualizuje składnik systemowy i bazę danych sterowników.|  
|*Identyfikator GUID* `/g`|Określa, że baza danych wykazu identyfikowana przez globalnie unikatowy identyfikator *GUID* jest aktualizowana.|  
|`/r`|Usuwa określone wykazy z bazy danych wykazów. Jeśli ta opcja nie jest określona, narzędzie podpisywania dodaje określone wykazy do bazy danych wykazów.|  
|`/u`|Określa, że dla dodawanych plików wykazów unikatowe nazwy są generowane automatycznie. W razie potrzeby nazwy plików wykazów są zmieniane, aby zapobiec konfliktom nazw z istniejącymi plikami wykazów. Jeśli ta opcja nie jest określona, narzędzie podpisywania zastępuje wszelkie istniejące wykazy, które mają taką samą nazwę jak wykaz dodawany.|  
  
<a name="sign"></a>   
## <a name="sign-command-options"></a>Podpisz opcje polecenia  
 Poniższa tabela zawiera listę opcji, które mogą być używane z poleceniem `sign`.  
  
|Opcja polecenia Sign|Opis|  
|-------------------------|-----------------|  
|`/a`|Automatycznie wybiera najlepszy certyfikat podpisywania. Narzędzie podpisywania znajdzie wszystkie ważne certyfikaty, które spełniają wszystkie określone warunki, i wybierze ten, którego okres ważności jest najdłuższy. Jeśli ta opcja nie jest określona, narzędzie podpisywania spodziewa się znaleźć tylko jeden ważny certyfikat podpisywania.|  
|*plik* `/ac`|Dodaje dodatkowy certyfikat z *pliku* do bloku podpisu.|  
|`/as`|Dołącza ten podpis. Jeśli nie jest określony podpis podstawowy, ten podpis jest ustawiany jako podpis podstawowy.|  
|`/c`*CertTemplateName*|Określa nazwę szablonu certyfikatu (rozszerzenie Microsoft) dla certyfikatu podpisywania.|  
|`/csp`*CSPName*|Określa dostawcę usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego.|  
|`/d`*DESC*|Określa opis podpisanej zawartości.|  
|*adres URL* `/du`|Określa adres URL (Uniform Resource Locator) rozszerzonego opisu podpisanej zawartości.|  
|`/f`*SignCertFile*|Określa certyfikat podpisywania w pliku. Jeśli plik znajduje się w formacie wymiany informacji osobistych (PFX) i jest chroniony hasłem, użyj opcji `/p`, aby określić hasło. Jeśli plik nie zawiera kluczy prywatnych, użyj opcji `/csp` i `/kc`, aby określić dostawcę CSP i nazwę kontenera klucza prywatnego.|  
|`/fd`|Określa algorytm tworzenia skrótu pliku na potrzeby tworzenia podpisów plików. Domyślnie jest to algorytm SHA1.|  
|`/i`*wystawcy*|Określa nazwę wystawcy certyfikatu podpisywania. Ta wartość może być podciągiem całej nazwy wystawcy.|  
|`/kc`*PrivKeyContainerName*|Określa nazwę kontenera kluczy prywatnych.|  
|`/n`*SubjectName*|Określa nazwę podmiotu certyfikatu podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu.|  
|`/nph`|Jeśli jest obsługiwana, pomija skróty stron dla plików wykonywalnych. Wartość domyślna jest określana przez zmienną środowiskową SIGNTOOL_PAGE_HASHES i wersję pliku wintrust.dll. Ta opcja jest ignorowana dla plików innych niż PE.|  
|`/p`*hasło*|Określa hasło używane podczas otwierania pliku PFX. (Użyj opcji `/f`, aby określić plik PFX).|  
|*ścieżka* `/p7`|Określa, że plik PKCS (Public Key Cryptography Standards) #7 jest generowany dla każdego określonego pliku zawartości. Pliki PKCS #7 są nazwanymi *ścieżkami*\\*filename*. P7.|  
|*wartość* `/p7ce`|Określa opcje dla podpisanej zawartości PKCS #7. Ustaw *wartość* "Embedded", aby osadzić podpisaną zawartość w pliku PKCS #7 lub "DetachedSignedData", aby utworzyć podpisaną część danych odłączonego pliku #7 PKCS. Jeśli opcja `/p7ce` nie jest używana, podpisana zawartość jest domyślnie osadzona.|  
|`/p7co` *\<OID >*|Określa identyfikator obiektu (OID), który identyfikuje podpisaną zawartość PKCS #7.|  
|`/ph`|Jeśli jest obsługiwana, generuje skróty stron dla plików wykonywalnych.|  
|`/r`*RootSubjectName*|Określa nazwę podmiotu certyfikatu głównego, z którym musi zostać połączony certyfikat podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu certyfikatu głównego.|  
|`/s`*StoreName*|Określa magazyn otwierany podczas wyszukiwania certyfikatu. Jeśli ta opcja nie zostanie określona, zostanie otwarty magazyn `My`.|  
|*skrót* `/sha1`|Określa skrót SHA1 certyfikatu podpisywania. Skrót SHA1 jest zazwyczaj określany, jeśli wiele certyfikatów spełnia kryteria określone przez pozostałe przełączniki.|  
|`/sm`|Określa, że jest używany magazyn komputera, a nie magazyn użytkownika.|  
|*adres URL* `/t`|Określa adres URL serwera znaczników czasu. Jeśli ta opcja (lub `/tr`) nie istnieje, podpisany plik nie będzie miał sygnatury czasowej. Jeśli oznaczanie znacznikiem czasu nie powiedzie się, jest generowane ostrzeżenie. Tej opcji nie można używać z opcją `/tr`.|  
|`/td`*alg*|Używane z opcją `/tr`, aby zażądać algorytmu podsumowania używanego przez serwer sygnatury czasowej RFC 3161.|  
|*adres URL* `/tr`|Określa adres URL serwera znaczników czasu RFC 3161. Jeśli ta opcja (lub `/t`) nie istnieje, podpisany plik nie będzie miał sygnatury czasowej. Jeśli oznaczanie znacznikiem czasu nie powiedzie się, jest generowane ostrzeżenie. Tej opcji nie można używać z opcją `/t`.|  
|*użycie* `/u`|Określa rozszerzone użycie klucza (EKU), które musi być obecne w certyfikacie podpisywania. Wartość Usage można określić za pomocą identyfikatora OID lub ciągu. Domyślna wartość Usage to „Code Signing” (1.3.6.1.5.5.7.3.3).|  
|`/uw`|Określa użycie funkcji weryfikacji składników systemu Windows (1.3.6.1.4.1.311.10.3.6).|  
  
 Aby zapoznać się z przykładami użycia, zobacz [Używanie narzędzia SignTool do podpisywania pliku](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file).  
  
<a name="TimeStamp"></a>   
## <a name="timestamp-command-options"></a>Opcje polecenia sygnatury czasowej  
 Poniższa tabela zawiera listę opcji, które mogą być używane z poleceniem `TimeStamp`.  
  
|Opcja polecenia TimeStamp|Opis|  
|----------------------|-----------------|  
|`/p7`|Oznacza pliki PKCS #7 znacznikami czasu.|  
|*adres URL* `/t`|Określa adres URL serwera znaczników czasu. Plik oznaczany znacznikiem czasu musi zostać wcześniej podpisany. Wymagana jest opcja `/t` lub `/tr`.|  
|`/td`*alg*|Żąda algorytmu tworzenia skrótu używanego przez serwer znaczników czasu RFC 3161. `/td` jest używany z opcją `/tr`.|  
|*indeks* `/tp`|Sygnatura czasowa sygnatura *.*|  
|*adres URL* `/tr`|Określa adres URL serwera znaczników czasu RFC 3161. Plik oznaczany znacznikiem czasu musi zostać wcześniej podpisany. Wymagana jest opcja `/tr` lub `/t`.|  
  
 Przykład użycia można znaleźć w temacie [Dodawanie sygnatur czasowych do wcześniej podpisanych plików](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files).  
  
<a name="Verify"></a>   
## <a name="verify-command-options"></a>Sprawdź opcje polecenia  
  
|Opcja polecenia Verify|Opis|  
|-------------------|-----------------|  
|`/a`|Określa, że w celu weryfikacji pliku można użyć wszystkich metod. Najpierw bazy danych wykazów są przeszukiwane w celu ustalenia, czy plik jest podpisany w wykazie. Jeśli plik nie jest podpisany w żadnym wykazie, narzędzie podpisywania próbuje zweryfikować podpis osadzony w pliku. Ta opcja jest zalecana w przypadku weryfikowania plików, które mogą, ale nie muszą, być podpisane w wykazie. Przykładami tych plików są pliki lub sterowniki systemu Windows.|  
|`/ad`|Znajduje wykaz przy użyciu domyślnej bazy danych wykazów.|  
|`/ag` *CatDBGUID*|Znajduje wykaz w bazie danych wykazu, który jest identyfikowany przez *CatDBGUID*.|  
|`/all`|Weryfikuje wszystkie podpisy w pliku, który zawiera wiele podpisów.|  
|`/as`|Znajduje wykaz przy użyciu bazy danych wykazów składników systemu (sterowniki).|  
|`/c` *CatFile*|Określa plik wykazu według nazwy.|  
|`/d`|Określa, że narzędzie podpisywania powinno drukować opis i adres URL opisu.|  
|*indeks* `/ds`|Weryfikuje podpis w określonej pozycji.|  
|`/hash` (`SHA1`&#124;`SHA256`)|Określa opcjonalny algorytm wyznaczania wartości skrótu, który ma być używany podczas wyszukiwania pliku w wykazie.|  
|`/kp`|Określa, że weryfikacja powinna być wykonywana przy użyciu zasad podpisywania sterowników trybu jądra.|  
|`/ms`|Używa wielu semantyk weryfikacji. Jest to domyślne zachowanie wywołania [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) dla [!INCLUDE[win8](../../../includes/win8-md.md)] i nowszych.|  
|*wersja* `/o`|Weryfikuje plik na podstawie wersji systemu operacyjnego. *Wersja* ma następującą postać: *PlatformID*:*VerMajor*. *Szkodniki*. *BuildNumber*. *PlatformID* reprezentuje podstawową wartość elementu członkowskiego wyliczenia <xref:System.PlatformID>. **Ważne:**  Zalecane jest użycie przełącznika `/o`. Jeśli nie określono `/o`, narzędzia SignTool. exe może zwrócić nieoczekiwane wyniki. Jeśli na przykład nie zostanie uwzględniony przełącznik `/o`, wykazy systemowe, które poprawnie weryfikują w starszym systemie operacyjnym, mogą nie zostać prawidłowo zweryfikowane w nowszej wersji systemu operacyjnego.|  
|`/p7`|Weryfikuje pliki PKCS #7. Żadne z istniejących zasad nie są używane do weryfikacji plików PKCS #7. Podpis jest sprawdzany i zostaje utworzony łańcuch dla certyfikatu podpisywania.|  
|`/pa`|Określa, że mają być używane domyślne zasady weryfikacji Authenticode. Jeśli opcja `/pa` nie zostanie określona, narzędzie podpisywania będzie używać zasad weryfikacji sterowników systemu Windows. Tej opcji nie można używać z opcjami `catdb`.|  
|`/pg` *PolicyGUID*|Określa zasady weryfikacji według identyfikatora GUID. *PolicyGUID* odnosi się do Identyfikator akcji zasad weryfikacji. Tej opcji nie można używać z opcjami `catdb`.|  
|`/ph`|Określa, że narzędzie podpisywania powinno drukować i weryfikować wartości skrótu stron.|  
|`/r` *RootSubjectName*|Określa nazwę podmiotu certyfikatu głównego, z którym musi zostać połączony certyfikat podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu certyfikatu głównego.|  
|`/tw`|Określa, że ma być generowane ostrzeżenie, jeśli podpis nie ma znacznika czasu.|  
  
 Aby zapoznać się z przykładami użycia, zobacz [Używanie narzędzia SignTool do weryfikowania podpisu pliku](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature).  
  
## <a name="return-value"></a>Wartość zwracana  
 Kończąc działanie, narzędzie podpisywania zwraca jeden z poniższych kodów zakończenia.  
  
|Kod zakończenia|Opis|  
|---------------|-----------------|  
|0|Wykonywanie powiodło się.|  
|1|Wykonywanie nie powiodło się.|  
|2|Wykonanie zostało ukończone, ale zostały wygenerowane ostrzeżenia.|  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie dodaje plik wykazu MyCatalogFileName.cat do bazy danych składników systemu i sterowników. Opcja `/u` w razie potrzeby generuje unikatową nazwę, aby zapobiec zastąpieniu istniejącego pliku wykazu o nazwie `MyCatalogFileName.cat`.  
  
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
  
 Następujące polecenie podpisuje plik przy użyciu certyfikatu znajdującego się w magazynie `My`, który ma nazwę podmiotu `My Company Certificate`.  
  
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
  
 Poniższe polecenie sprawdza plik systemowy, który jest podpisany w wykazie o nazwie `MyCatalog.cat`.  
  
```console  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
