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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d13c2d2cc391e61c8ed764c26e5e5b5e7ea2a3bb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851384"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Menedżer certyfikatów)
Narzędzie Menedżer certyfikatów (Certmgr.exe) zarządza certyfikatami, listami zaufania certyfikatów (CTL) oraz listami odwołania certyfikatów (CRL).  
  
 Menedżer certyfikatów jest instalowany automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć [wiersza polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
> Narzędzie Menedżer certyfikatów (Certmgr.exe) jest narzędziem wiersza polecenia, natomiast narzędzie Certyfikaty (Certmgr.msc) jest przystawką programu Microsoft Management Console (MMC). Ponieważ certmgr. msc zwykle znajduje się w katalogu systemu Windows, wprowadzenie `certmgr` w wierszu polecenia może załadować przystawkę MMC Certyfikaty, nawet jeśli otwarto wiersz polecenia dla deweloperów dla programu Visual Studio. Dzieje się tak, ponieważ ścieżka do przystawki ma pierwszeństwo przed ścieżką do narzędzia Menedżer certyfikatów w zmiennej środowiskowej PATH. Jeśli wystąpi ten problem, można wykonywać polecenia programu Certmgr.exe, określając ścieżkę do pliku wykonywalnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Aby zapoznać się z omówieniem certyfikatów X. 509, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
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
|*sourceStorename*|Magazyn certyfikatów zawierający istniejące certyfikaty, listy CTL lub CRL do dodania, zapisania lub wyświetlenia. Może to być plik magazynu lub magazyn systemowy.|  
|*destinationStorename*|Wyjściowy magazyn lub plik certyfikatów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Add**|Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.|  
|**/All**|Dodaje wszystkie wpisy, gdy są używane z **/Add**. Usuwa wszystkie wpisy, gdy są używane z **/del**. Wyświetla wszystkie wpisy, gdy są używane bez opcji **/Add** lub **/del** . Opcja **/All** nie może być używana z **/Put**.|  
|**/c**|Dodaje certyfikaty, gdy jest używany z **/Add**. Usuwa certyfikaty, gdy są używane z **/del**. Zapisuje certyfikaty, gdy są używane z **/Put**. Wyświetla certyfikaty, gdy jest używana bez opcji **/Add**, **/del**lub **/Put** .|  
|**/CRL**|Dodaje listy CRL, gdy jest używana z opcją **/Add**. Usuwa listy CRL, gdy są używane z **/del**. Zapisuje listy CRL, gdy są używane z **/Put**. Wyświetla listę CRL, gdy jest używana bez opcji **/Add**, **/del**lub **/Put** .|  
|**/CTL**|Dodaje listy CTL, gdy jest używana z opcją **/Add**. Usuwa listy CTL, gdy jest używana z **/del**. Zapisuje listy CTL, gdy jest używana z **/Put**. Wyświetla listę CTL, gdy jest używana bez opcji **/Add**, **/del**lub **/Put** .|  
|**/del**|Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.|  
|**/e** *EncodingType*|Określa typ kodowania certyfikatu. Wartość domyślna to `X509_ASN_ENCODING`.|  
|**/f** *flagiDW*|Określa flagę otwarcia magazynu. Jest to parametr *flagiDW* przesłany do **CertOpenStore**. Wartość domyślna to CERT_SYSTEM_STORE_CURRENT_USER. Ta opcja jest uwzględniana tylko wtedy, gdy jest używana opcja **/y** .|  
|**/h** [**ELP**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/n** nazwa|Określa wspólną nazwę certyfikatu do dodania, usunięcia lub zapisania. Tej opcji można używać tylko z certyfikatami; nie można używać jej z listami CTL i CRL.|  
|**/Put**|Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku. Plik jest zapisywany w formacie X.509. Aby zapisać plik w formacie PKCS #7, można użyć opcji **/7** z opcją **/Put** . Po opcji **/Put** należy wykonać polecenie **/c**, **/CTL**lub **/CRL**. Opcja **/All** nie może być używana z **/Put**.|  
|**/r** *Lokalizacja*|Określa lokalizację w rejestrze magazynu systemowego. Ta opcja jest uwzględniana tylko wtedy, gdy określono opcję **/s** . *Lokalizacja* musi mieć jedną z następujących wartości:<br /><br /> -   `currentUser`wskazuje, że magazyn certyfikatów znajduje się w kluczu HKEY_CURRENT_USER. Domyślnie włączone.<br />-   `localMachine`wskazuje, że magazyn certyfikatów znajduje się w kluczu HKEY_LOCAL_MACHINE.|  
|**/s**|Wskazuje, że magazyn certyfikatów jest magazynem systemowym. Jeśli ta opcja nie zostanie określona, magazyn jest uznawany za **StoreFile**.|  
|**/SHA1** *sha1Hash*|Określa skrót SHA1 certyfikatu, listy CTL lub CRL do dodania, usunięcia lub zapisania.|  
|**/v**|Określa tryb pełny; wyświetla szczegółowe informacje dotyczące certyfikatu oraz list CTL i CRL. Tej opcji nie można używać z opcjami **/Add**, **/del**i **/Put** .|  
|**/y** *dostawca*|Określa nazwę dostawcy magazynu.|  
|**/7**|Zapisuje magazyn docelowy jako obiekt w formacie PKCS #7.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Program Certmgr.exe wykonuje następujące podstawowe funkcje:  
  
- Wyświetla na konsoli certyfikaty oraz listy CTL i CRL.  
  
- Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.  
  
- Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.  
  
- Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.  
  
 Certmgr. exe współpracuje z dwoma typami magazynów certyfikatów: **StoreFile** i magazyn systemowy. Nie jest konieczne określanie typu magazynu certyfikatów; program Certmgr.exe może zidentyfikować typ magazynu i wykonać odpowiednie operacje.  
  
 Uruchomienie programu Certmgr.exe bez określenia żadnej opcji spowoduje uruchomienie przystawki certmgr.msc wyposażonej w graficzny interfejs użytkownika ułatwiający wykonywanie zadań zarządzania certyfikatami, które są również dostępne w wierszu polecenia. Graficzny interfejs użytkownika dostarcza kreatora importu, który kopiuje certyfikaty oraz listy CTL i CRL z dysku do magazynu certyfikatów.  
  
 Nazwy magazynów x509 można znaleźć dla `sourceStorename` parametrów i `destinationStorename` , kompilując i uruchamiając następujący kod.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie wyświetla domyślny magazyn systemowy o nazwie `my` z pełnymi danymi wyjściowymi.  
  
```console  
certmgr /v /s my  
```  
  
 Następujące polecenie dodaje wszystkie certyfikaty w pliku o nazwie `myFile.ext` do nowego pliku o nazwie. `newFile.ext`  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Poniższe polecenie dodaje certyfikat w pliku o nazwie `testcert.cer` `my` do magazynu systemowego.  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 Poniższe polecenie dodaje certyfikat w pliku o nazwie `TrustedCert.cer` do głównego magazynu certyfikatów.  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Poniższe polecenie zapisuje certyfikat z nazwą `myCert` pospolitą `my` w magazynie systemowym do pliku o nazwie `newCert.cer`.  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Następujące polecenie usuwa wszystkie listy CTL ze `my` sklepu systemowego i zapisuje przechowywany magazyn do pliku o nazwie. `newStore.str`  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Poniższe polecenie zapisuje certyfikat w `my` magazynie systemowym w pliku. `newFile` Zostanie wyświetlony monit o wprowadzenie numeru certyfikatu z `my` , który ma zostać `newFile`umieszczony.  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [MakeCert. exe (narzędzie tworzenia certyfikatów)](/windows/desktop/SecCrypto/makecert)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
