---
title: Certmgr.exe (Menedżer certyfikatów)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
ms.openlocfilehash: 06fe3a78d0b19720d4f83111980b88806312205f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129878"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Menedżer certyfikatów)
Narzędzie Menedżer certyfikatów (Certmgr.exe) zarządza certyfikatami, listami zaufania certyfikatów (CTL) oraz listami odwołania certyfikatów (CRL).  
  
 Menedżer certyfikatów jest instalowany automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj [wierszy polecenia](developer-command-prompt-for-vs.md).  
  
> [!NOTE]
> Narzędzie Menedżer certyfikatów (Certmgr.exe) jest narzędziem wiersza polecenia, natomiast narzędzie Certyfikaty (Certmgr.msc) jest przystawką programu Microsoft Management Console (MMC). Ponieważ plik Certmgr.msc zwykle znajduje się w `certmgr` katalogu systemu Windows, wprowadzenie w wierszu polecenia może załadować przystawkę Programu MMC certyfikaty, nawet jeśli otwarto wiersz polecenia dewelopera dla programu Visual Studio. Dzieje się tak, ponieważ ścieżka do przystawki ma pierwszeństwo przed ścieżką do narzędzia Menedżer certyfikatów w zmiennej środowiskowej PATH. Jeśli wystąpi ten problem, można wykonywać polecenia programu Certmgr.exe, określając ścieżkę do pliku wykonywalnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 Aby zapoznać się z omówieniem certyfikatów X.509, zobacz [Praca z certyfikatami](../wcf/feature-details/working-with-certificates.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*źródłoSklepname*|Magazyn certyfikatów zawierający istniejące certyfikaty, listy CTL lub CRL do dodania, zapisania lub wyświetlenia. Może to być plik magazynu lub magazyn systemowy.|  
|*miejsce doceloweSklepname*|Wyjściowy magazyn lub plik certyfikatów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/add**|Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.|  
|**/wszystkie**|Dodaje wszystkie wpisy używane z **/add**. Usuwa wszystkie wpisy używane z **/del**. Wyświetla wszystkie wpisy używane bez opcji **/add** lub **/del.** Opcji **/all** nie można używać z **/put**.|  
|**/c**|Dodaje certyfikaty używane z **/add**. Usuwa certyfikaty używane z **/del**. Zapisuje certyfikaty używane z **/put**. Wyświetla certyfikaty używane bez opcji **/add**, **/del**lub **/put.**|  
|**/CRL**|Dodaje listy CRL używane z **/add**. Usuwa listy CRL używane z **/del**. Zapisuje listy CRL używane z **/put**. Wyświetla listy CRL, gdy są używane bez opcji **/add**, **/del**lub **/put.**|  
|**/CTL**|Dodaje listy CTL używane z **/add**. Usuwa listy CTL używane z **/del**. Zapisuje listy CTL używane z **/put**. Wyświetla listy CTL używane bez opcji **/add**, **/del**lub **/put.**|  
|**/del**|Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.|  
|**/e** *kodowanieTyp*|Określa typ kodowania certyfikatu. Wartość domyślna to `X509_ASN_ENCODING`.|  
|**/f** *wilki*|Określa flagę otwarcia magazynu. Jest to parametr *dwFlags* przekazany do **CertOpenStore**. Wartość domyślna to CERT_SYSTEM_STORE_CURRENT_USER. Ta opcja jest brana pod uwagę tylko wtedy, gdy używana jest opcja **/y.**|  
|**/h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/n** *nam*|Określa wspólną nazwę certyfikatu do dodania, usunięcia lub zapisania. Tej opcji można używać tylko z certyfikatami; nie można używać jej z listami CTL i CRL.|  
|**/put**|Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku. Plik jest zapisywany w formacie X.509. Możesz użyć opcji **/7** z opcją **/put,** aby zapisać plik w formacie PKCS #7. Po **/put** musi następować opcja **/c**, **/CTL**lub **/CRL**. Opcji **/all** nie można używać z **/put**.|  
|**/r** *lokalizacja*|Określa lokalizację w rejestrze magazynu systemowego. Ta opcja jest brana pod uwagę tylko w przypadku określenia opcji **/s.** *lokalizacja* musi być jedną z następujących czynności:<br /><br /> -   `currentUser`wskazuje, że magazyn certyfikatów znajduje się pod kluczem HKEY_CURRENT_USER. Domyślnie włączone.<br />-   `localMachine`wskazuje, że magazyn certyfikatów znajduje się pod kluczem HKEY_LOCAL_MACHINE.|  
|**/s**|Wskazuje, że magazyn certyfikatów jest magazynem systemowym. Jeśli ta opcja nie zostanie określona, magazyn jest uważany za **StoreFile**.|  
|**/sha1** *sha1Hash*|Określa skrót SHA1 certyfikatu, listy CTL lub CRL do dodania, usunięcia lub zapisania.|  
|**/v**|Określa tryb pełny; wyświetla szczegółowe informacje dotyczące certyfikatu oraz list CTL i CRL. Tej opcji nie można używać z opcjami **/add**, **/del**lub **/put.**|  
|**/y** *dostawca*|Określa nazwę dostawcy magazynu.|  
|**/7**|Zapisuje magazyn docelowy jako obiekt w formacie PKCS #7.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Program Certmgr.exe wykonuje następujące podstawowe funkcje:  
  
- Wyświetla na konsoli certyfikaty oraz listy CTL i CRL.  
  
- Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.  
  
- Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.  
  
- Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.  
  
 Program Certmgr.exe współpracuje z dwoma typami magazynów certyfikatów: **StoreFile** i magazynem systemowym. Nie jest konieczne określanie typu magazynu certyfikatów; program Certmgr.exe może zidentyfikować typ magazynu i wykonać odpowiednie operacje.  
  
 Uruchomienie programu Certmgr.exe bez określenia żadnej opcji spowoduje uruchomienie przystawki certmgr.msc wyposażonej w graficzny interfejs użytkownika ułatwiający wykonywanie zadań zarządzania certyfikatami, które są również dostępne w wierszu polecenia. Graficzny interfejs użytkownika dostarcza kreatora importu, który kopiuje certyfikaty oraz listy CTL i CRL z dysku do magazynu certyfikatów.  
  
 Nazwy magazynów X509Certificate można `sourceStorename` znaleźć, `destinationStorename` kompilując i uruchamiając następujący kod.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie wyświetla domyślny `my` magazyn systemowy wywoływany z pełnymi wydrukami.  
  
```console  
certmgr /v /s my  
```  
  
 Następujące polecenie dodaje wszystkie certyfikaty `myFile.ext` w pliku wywoływanym do nowego pliku o nazwie `newFile.ext`.  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Następujące polecenie dodaje certyfikat w `testcert.cer` pliku `my` o nazwie do magazynu systemowego.  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 Następujące polecenie dodaje certyfikat w `TrustedCert.cer` pliku o nazwie do głównego magazynu certyfikatów.  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Następujące polecenie zapisuje certyfikat o `myCert` wspólnej `my` nazwie w magazynie `newCert.cer`systemowym do pliku o nazwie .  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Poniższe polecenie usuwa wszystkie listy `my` CTL w magazynie systemowym i `newStore.str`zapisuje wynikowy magazyn w pliku o nazwie .  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Następujące polecenie zapisuje certyfikat `my` w magazynie systemowym w pliku `newFile`. Zostanie wyświetlony monit o wprowadzenie numeru `my` certyfikatu `newFile`od wprowadzenia .  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Plik Makecert.exe (narzędzie do tworzenia certyfikatów)](/windows/desktop/SecCrypto/makecert)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
