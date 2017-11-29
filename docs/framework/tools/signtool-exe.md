---
title: "SignTool.exe (Narzędzie podpisu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06a8b2e41841dfa43609468cce60a3776137b720
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (Narzędzie podpisu)
Narzędzie podpisywania to narzędzie wiersza polecenia, które cyfrowo podpisuje pliki, weryfikuje podpisy w plikach i oznacza pliki znacznikami czasu.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
signtool [command] [options] [file_name | ...]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|`command`|Jedno z czterech poleceń (`catdb`, `sign`, `Timestamp`, lub `Verify`), który określa operacji do wykonania w pliku. Aby zapoznać się z opisem każdego polecenia, zobacz następną tabelę.|  
|`options`|Opcja, która modyfikuje polecenie. Oprócz globalnej `/q` i `/v` opcje, każde polecenie obsługuje unikatowy zestaw opcji.|  
|`file_name`|Ścieżka do pliku, który ma zostać podpisany.|  
  
 Poniższe polecenia są obsługiwane przez narzędzie podpisywania. Każde polecenie jest używane z odrębnym zestawem opcji, które wymieniono w odpowiednich sekcjach.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|`catdb`|Dodaje plik wykazu do bazy danych wykazów lub usuwa go z niej. Bazy danych wykazów służą do automatycznego wyszukiwania plików wykazu i są identyfikowane przez identyfikator GUID. Aby uzyskać listę opcji obsługiwanych przez `catdb` polecenia, zobacz [catdb opcji polecenia](../../../docs/framework/tools/signtool-exe.md#catdb).|  
|`sign`|Cyfrowo podpisuje pliki. Podpisy cyfrowe chronią pliki przed ingerencją osób niepowołanych i umożliwiają użytkownikom weryfikację podpisującego na podstawie certyfikatu podpisywania. Aby uzyskać listę opcji obsługiwanych przez `sign` polecenia, zobacz [zarejestrować opcji polecenia](../../../docs/framework/tools/signtool-exe.md#sign).|  
|`Timestamp`|Oznacza pliki znacznikami czasu. Aby uzyskać listę opcji obsługiwanych przez `TimeStamp` polecenia, zobacz [opcji polecenia sygnatury czasowej](../../../docs/framework/tools/signtool-exe.md#TimeStamp).|  
|`Verify`|Weryfikuje podpis cyfrowy plików, ustalając, czy certyfikat podpisywania został wystawiony przez zaufany urząd, czy certyfikat podpisywania został odwołany i, opcjonalnie, czy certyfikat podpisywania jest ważny dla określonych zasad. Aby uzyskać listę opcji obsługiwanych przez `Verify` polecenia, zobacz [Sprawdź opcje polecenia](../../../docs/framework/tools/signtool-exe.md#Verify).|  
  
 Poniższe opcje są stosowane do wszystkich poleceń narzędzia podpisywania.  
  
|Opcja globalna|Opis|  
|-------------------|-----------------|  
|**/q**|Nie wyświetla danych wyjściowych, jeśli działanie polecenia zakończy się pomyślnie, i wyświetla minimalne dane wyjściowe, jeśli działanie polecenia zakończy się niepowodzeniem.|  
|**/v**|Wyświetla pełne dane wyjściowe bez względu na to, czy polecenie zostanie wykonane pomyślnie, czy jego działanie zakończy się niepowodzeniem, a ponadto wyświetla komunikaty ostrzegawcze.|  
|**/ Debug**|Wyświetla informacje debugowania.|  
  
<a name="catdb"></a>   
## <a name="catdb-command-options"></a>Opcje polecenia catdb  
 W poniższej tabeli wymieniono opcje, które mogą być używane z `catdb` polecenia.  
  
|Opcja polecenia Catdb|Opis|  
|------------------|-----------------|  
|`/d`|Określa, że domyślna baza danych wykazów jest aktualizowana. Jeśli żadna `/d` ani `/g` jest używana opcja, narzędzie podpisu aktualizuje bazę danych systemu składników i sterowników.|  
|`/g`*IDENTYFIKATOR GUID*|Określa, że baza danych katalogu identyfikowane przez unikatowy identyfikator globalny *GUID* jest aktualizowany.|  
|`/r`|Usuwa określone wykazy z bazy danych wykazów. Jeśli ta opcja nie jest określona, narzędzie podpisywania dodaje określone wykazy do bazy danych wykazów.|  
|`/u`|Określa, że dla dodawanych plików wykazów unikatowe nazwy są generowane automatycznie. W razie potrzeby nazwy plików wykazów są zmieniane, aby zapobiec konfliktom nazw z istniejącymi plikami wykazów. Jeśli ta opcja nie jest określona, narzędzie podpisywania zastępuje wszelkie istniejące wykazy, które mają taką samą nazwę jak wykaz dodawany.|  
  
<a name="sign"></a>   
## <a name="sign-command-options"></a>Podpisz opcje polecenia  
 W poniższej tabeli wymieniono opcje, które mogą być używane z `sign` polecenia.  
  
|Opcja polecenia Sign|Opis|  
|-------------------------|-----------------|  
|`/a`|Automatycznie wybiera najlepszy certyfikat podpisywania. Narzędzie podpisywania znajdzie wszystkie ważne certyfikaty, które spełniają wszystkie określone warunki, i wybierze ten, którego okres ważności jest najdłuższy. Jeśli ta opcja nie jest określona, narzędzie podpisywania spodziewa się znaleźć tylko jeden ważny certyfikat podpisywania.|  
|`/ac`  *plik*|Dodaje dodatkowy certyfikat z *pliku* blok podpisu.|  
|`/as`|Dołącza ten podpis. Jeśli nie jest określony podpis podstawowy, ten podpis jest ustawiany jako podpis podstawowy.|  
|`/c`  *CertTemplateName*|Określa nazwę szablonu certyfikatu (rozszerzenie Microsoft) dla certyfikatu podpisywania.|  
|`/csp`  *NazwaCSP*|Określa dostawcę usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego.|  
|`/d`  *Desc*|Określa opis podpisanej zawartości.|  
|`/du`  *ADRES URL*|Określa adres URL (Uniform Resource Locator) rozszerzonego opisu podpisanej zawartości.|  
|`/f`  *SignCertFile*|Określa certyfikat podpisywania w pliku. Jeśli plik jest w formacie wymiany informacji osobistych (PFX) i chroniony hasłem, użyj `/p` opcję, aby określić hasło. Jeśli plik nie zawiera kluczy prywatnych, należy użyć `/csp` i `/kc` opcji, aby określić dostawcę usług Kryptograficznych i nazwy kontenera kluczy prywatnych.|  
|`/fd`|Określa algorytm tworzenia skrótu pliku na potrzeby tworzenia podpisów plików. Domyślnie jest to algorytm SHA1.|  
|`/i`  *IssuerName*|Określa nazwę wystawcy certyfikatu podpisywania. Ta wartość może być podciągiem całej nazwy wystawcy.|  
|`/kc`  *PrivKeyContainerName*|Określa nazwę kontenera kluczy prywatnych.|  
|`/n`  *SubjectName*|Określa nazwę podmiotu certyfikatu podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu.|  
|`/nph`|Jeśli jest obsługiwana, pomija skróty stron dla plików wykonywalnych. Wartość domyślna jest określana przez zmienną środowiskową SIGNTOOL_PAGE_HASHES i wersję pliku wintrust.dll. Ta opcja jest ignorowana dla plików innych niż PE.|  
|`/p`  *Hasło*|Określa hasło używane podczas otwierania pliku PFX. (Użyj `/f` opcję, aby określić plik PFX.)|  
|`/p7`*Ścieżki*|Określa, że plik PKCS (Public Key Cryptography Standards) #7 jest generowany dla każdego określonego pliku zawartości. Pliki PKCS #7 są nazywane *ścieżki*\\*filename*.p7.|  
|`/p7ce`*Wartość*|Określa opcje dla podpisanej zawartości PKCS #7. Ustaw *wartość* "Osadzone", aby osadzić podpisanej zawartości w pliku PKCS #7 lub "DetachedSignedData", aby wygenerować podpisane dane część odłączyć pliku PKCS #7. Jeśli `/p7ce` nie jest używana opcja, podpisanej zawartości jest osadzony domyślnie.|  
|`/p7co` *\<OID >*|Określa identyfikator obiektu (OID), który identyfikuje podpisaną zawartość PKCS #7.|  
|`/ph`|Jeśli jest obsługiwana, generuje skróty stron dla plików wykonywalnych.|  
|`/r`  *RootSubjectName*|Określa nazwę podmiotu certyfikatu głównego, z którym musi zostać połączony certyfikat podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu certyfikatu głównego.|  
|`/s`  *StoreName*|Określa magazyn otwierany podczas wyszukiwania certyfikatu. Jeśli ta opcja nie jest określona, `My` otworzyć magazynu.|  
|`/sha1`  *Wyznaczania wartości skrótu*|Określa skrót SHA1 certyfikatu podpisywania. Skrót SHA1 jest zazwyczaj określany, jeśli wiele certyfikatów spełnia kryteria określone przez pozostałe przełączniki.|  
|`/sm`|Określa, że jest używany magazyn komputera, a nie magazyn użytkownika.|  
|`/t`  *ADRES URL*|Określa adres URL serwera znaczników czasu. Jeśli ta opcja (lub `/tr`) jest nieobecna, podpisany plik nie będzie z sygnaturą czasową. Jeśli oznaczanie znacznikiem czasu nie powiedzie się, jest generowane ostrzeżenie. Nie można użyć tej opcji z `/tr` opcji.|  
|`/td`  *alg*|Używane z `/tr` opcją prośby o algorytm skrótu używany przez serwer sygnatury czasu RFC 3161.|  
|`/tr`  *ADRES URL*|Określa adres URL serwera znaczników czasu RFC 3161. Jeśli ta opcja (lub `/t`) jest nieobecna, podpisany plik nie będzie z sygnaturą czasową. Jeśli oznaczanie znacznikiem czasu nie powiedzie się, jest generowane ostrzeżenie. Nie można użyć tej opcji z `/t` opcji.|  
|`/u`  *Użycie*|Określa rozszerzone użycie klucza (EKU), które musi być obecne w certyfikacie podpisywania. Wartość Usage można określić za pomocą identyfikatora OID lub ciągu. Domyślna wartość Usage to „Code Signing” (1.3.6.1.5.5.7.3.3).|  
|`/uw`|Określa użycie funkcji weryfikacji składników systemu Windows (1.3.6.1.4.1.311.10.3.6).|  
  
 Przykłady użycia można znaleźć [przy użyciu SignTool do podpisania pliku](http://msdn.microsoft.com/library/windows/desktop/aa388170.aspx).  
  
<a name="TimeStamp"></a>   
## <a name="timestamp-command-options"></a>Opcje polecenia sygnatury czasowej  
 W poniższej tabeli wymieniono opcje, które mogą być używane z `TimeStamp` polecenia.  
  
|Opcja polecenia TimeStamp|Opis|  
|----------------------|-----------------|  
|`/p7`|Oznacza pliki PKCS #7 znacznikami czasu.|  
|`/t`  *ADRES URL*|Określa adres URL serwera znaczników czasu. Plik oznaczany znacznikiem czasu musi zostać wcześniej podpisany. Albo `/t` lub `/tr` opcja jest wymagana.|  
|`/td`  *alg*|Żąda algorytmu tworzenia skrótu używanego przez serwer znaczników czasu RFC 3161. `/td`jest używany z `/tr` opcji.|  
|`/tp`*indeksu*|Sygnatury czasowe podpisu w *indeksu*.|  
|`/tr`  *ADRES URL*|Określa adres URL serwera znaczników czasu RFC 3161. Plik oznaczany znacznikiem czasu musi zostać wcześniej podpisany. Albo `/tr` lub `/t` opcja jest wymagana.|  
  
 Na przykład użycia, zobacz [Dodawanie sygnatury czasowe wcześniej podpisane pliki](http://msdn.microsoft.com/library/windows/desktop/aa375542.aspx).  
  
<a name="Verify"></a>   
## <a name="verify-command-options"></a>Sprawdź opcje polecenia  
  
|Opcja polecenia Verify|Opis|  
|-------------------|-----------------|  
|`/a`|Określa, że w celu weryfikacji pliku można użyć wszystkich metod. Najpierw bazy danych wykazów są przeszukiwane w celu ustalenia, czy plik jest podpisany w wykazie. Jeśli plik nie jest podpisany w żadnym wykazie, narzędzie podpisywania próbuje zweryfikować podpis osadzony w pliku. Ta opcja jest zalecana w przypadku weryfikowania plików, które mogą, ale nie muszą, być podpisane w wykazie. Przykładami tych plików są pliki lub sterowniki systemu Windows.|  
|`/ad`|Znajduje wykaz przy użyciu domyślnej bazy danych wykazów.|  
|`/ag`*CatDBGUID*|Wyszukuje wykazu w katalogu bazy danych, identyfikowany przez *CatDBGUID*.|  
|`/all`|Weryfikuje wszystkie podpisy w pliku, który zawiera wiele podpisów.|  
|`/as`|Znajduje wykaz przy użyciu bazy danych wykazów składników systemu (sterowniki).|  
|`/c`*CatFile*|Określa plik wykazu według nazwy.|  
|`/d`|Określa, że narzędzie podpisywania powinno drukować opis i adres URL opisu.|  
|`/ds`  *Indeks*|Weryfikuje podpis w określonej pozycji.|  
|`/hash` (`SHA1`&#124;`SHA256`)|Określa opcjonalny algorytm wyznaczania wartości skrótu, który ma być używany podczas wyszukiwania pliku w wykazie.|  
|`/kp`|Określa, że weryfikacja powinna być wykonywana przy użyciu zasad podpisywania sterowników trybu jądra.|  
|`/ms`|Używa wielu semantyk weryfikacji. Jest to domyślne zachowanie [WinVerifyTrust](http://msdn.microsoft.com/library/windows/desktop/aa388208.aspx) wywołać [!INCLUDE[win8](../../../includes/win8-md.md)] i powyżej.|  
|`/o`*Wersji*|Weryfikuje plik na podstawie wersji systemu operacyjnego. *Wersja* ma następujący format: *PlatformID*:*VerMajor*. *VerMinor*. *BuildNumber*. *PlatformID* reprezentuje podstawową wartość <xref:System.PlatformID> element członkowski wyliczenia. **Ważne:** stosowania `/o` przełącznik jest zalecane. Jeśli `/o` nie zostanie określony, SignTool.exe może zwrócić nieoczekiwane wyniki. Na przykład, jeśli nie zostanie uwzględniony `/o` przełącznika, wykazów systemowych, które zweryfikować poprawnie w starszych systemów operacyjnych może być sprawdzany poprawnie na nowszego systemu operacyjnego.|  
|`/p7`|Weryfikuje pliki PKCS #7. Żadne z istniejących zasad nie są używane do weryfikacji plików PKCS #7. Podpis jest sprawdzany i zostaje utworzony łańcuch dla certyfikatu podpisywania.|  
|`/pa`|Określa, że mają być używane domyślne zasady weryfikacji Authenticode. Jeśli `/pa` opcji nie zostanie określony, narzędzie używane są zasady weryfikacji sterowników systemu Windows. Nie można użyć tej opcji z `catdb` opcje.|  
|`/pg`*PolicyGUID*|Określa zasady weryfikacji według identyfikatora GUID. *PolicyGUID* odpowiada ActionID zasad weryfikacji. Nie można użyć tej opcji z `catdb` opcje.|  
|`/ph`|Określa, że narzędzie podpisywania powinno drukować i weryfikować wartości skrótu stron.|  
|`/r`*RootSubjectName*|Określa nazwę podmiotu certyfikatu głównego, z którym musi zostać połączony certyfikat podpisywania. Ta wartość może być podciągiem całej nazwy podmiotu certyfikatu głównego.|  
|`/tw`|Określa, że ma być generowane ostrzeżenie, jeśli podpis nie ma znacznika czasu.|  
  
 Przykłady użycia można znaleźć [przy użyciu SignTool można zweryfikować podpisu pliku](http://msdn.microsoft.com/library/windows/desktop/aa388171.aspx).  
  
## <a name="return-value"></a>Wartość zwracana  
 Kończąc działanie, narzędzie podpisywania zwraca jeden z poniższych kodów zakończenia.  
  
|Kod zakończenia|Opis|  
|---------------|-----------------|  
|0|Wykonywanie powiodło się.|  
|1|Wykonywanie nie powiodło się.|  
|2|Wykonanie zostało ukończone, ale zostały wygenerowane ostrzeżenia.|  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie dodaje plik wykazu MyCatalogFileName.cat do bazy danych składników systemu i sterowników. `/u` Opcja generuje unikatową nazwę, jeśli to konieczne, aby uniknąć zastępowania istniejącego katalogu pliku o nazwie `MyCatalogFileName.cat`.  
  
```  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 Poniższe polecenie podpisuje plik automatycznie przy użyciu najlepszego certyfikatu.  
  
```  
signtool sign /a MyFile.exe  
```  
  
 Poniższe polecenie podpisuje cyfrowo plik przy użyciu certyfikatu przechowywanego w chronionym hasłem pliku PFX.  
  
```  
signtool sign /f MyCert.pfx /p MyPassword MyFile.exe  
```  
  
 Poniższe polecenie podpisuje cyfrowo plik i oznacza go sygnaturą czasową. Certyfikat użyty do podpisania pliku jest przechowywany w pliku PFX.  
  
```  
signtool sign /f MyCert.pfx /t  HYPERLINK "http://timestamp.verisign.com/scripts/timstamp.dll" http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 Polecenie podpisuje plik przy użyciu certyfikatu znajduje się w `My` sklepu, która ma nazwę podmiotu `My Company Certificate`.  
  
```  
signtool sign /n "My Company Certificate" MyFile.exe  
```  
  
 Poniższe polecenie podpisuje formant ActiveX i udostępnia informacje wyświetlane przez program Internet Explorer, gdy użytkownik jest monitowany o zainstalowanie tego formantu.  
  
```  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html MyControl.exe  
```  
  
 Poniższe polecenie oznacza znacznikiem czasu plik, który jest już podpisany cyfrowo.  
  
```  
signtool timestamp /t  HYPERLINK "http://timestamp.verisign.com/scripts/timstamp.dll" http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 Poniższe polecenie sprawdza, czy plik jest podpisany.  
  
```  
signtool verify MyFile.exe  
```  
  
 Poniższe polecenie sprawdza plik systemowy, który może być podpisany w wykazie.  
  
```  
signtool verify /a SystemFile.dll  
```  
  
 Polecenie sprawdza, czy plik systemowy, który jest zalogowany katalog o nazwie `MyCatalog.cat`.  
  
```  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
