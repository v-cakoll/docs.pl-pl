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
ms.openlocfilehash: 0a4cb3f126a51d6bf7027edb88b8fec74c6785d2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723145"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Menedżer certyfikatów)
Narzędzie Menedżer certyfikatów (Certmgr.exe) zarządza certyfikatami, listami zaufania certyfikatów (CTL) oraz listami odwołania certyfikatów (CRL).  
  
 Menedżer certyfikatów jest instalowany automatycznie z programem Visual Studio. Aby uruchomić to narzędzie, należy użyć [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Narzędzie Menedżer certyfikatów (Certmgr.exe) jest narzędziem wiersza polecenia, natomiast narzędzie Certyfikaty (Certmgr.msc) jest przystawką programu Microsoft Management Console (MMC). Ponieważ Certmgr.msc zwykle znajduje się w katalogu systemu Windows, wprowadzając `certmgr` w wierszu polecenia może spowodować załadowanie przystawki MMC certyfikatów nawet wtedy, gdy został otwarty wiersz polecenia programu Visual Studio. Dzieje się tak, ponieważ ścieżka do przystawki ma pierwszeństwo przed ścieżką do narzędzia Menedżer certyfikatów w zmiennej środowiskowej PATH. Jeśli wystąpi ten problem, można wykonywać polecenia programu Certmgr.exe, określając ścieżkę do pliku wykonywalnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Aby uzyskać przegląd certyfikatów X.509, zobacz [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*sourceStorename*|Magazyn certyfikatów zawierający istniejące certyfikaty, listy CTL lub CRL do dodania, zapisania lub wyświetlenia. Może to być plik magazynu lub magazyn systemowy.|  
|*destinationStorename*|Wyjściowy magazyn lub plik certyfikatów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ add**|Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.|  
|**/ all**|Dodaje wszystkie wpisy, gdy jest używane z **/ add**. Usuwa wszystkie wpisy, gdy jest używane z **/del**. Wyświetla wszystkie wpisy, gdy jest używana bez **/ add** lub **/del** opcje. **/All** opcji nie można używać z **/put**.|  
|**/c**|Dodaje certyfikaty, gdy jest używany z **/ add**. Usuwa certyfikaty, gdy jest używany z **/del**. Zapisuje certyfikaty, gdy jest używane z **/put**. Wyświetla certyfikaty, gdy jest używana bez **/ add**, **/del**, lub **/put** opcji.|  
|**/ LIST CRL**|Dodaje listy CRL, gdy jest używane z **/ add**. Usuwa listy CRL, gdy jest używane z **/del**. Zapisuje listy CRL, gdy jest używane z **/put**. Wyświetla listy CRL, gdy jest używana bez **/ add**, **/del**, lub **/put** opcji.|  
|**/ CTL**|Dodaje listy CTL, gdy jest używane z **/ add**. Usuwa listy CTL, gdy jest używane z **/del**. Zapisuje listy CTL, gdy jest używane z **/put**. Wyświetla listy CTL, gdy jest używana bez **/ add**, **/del**, lub **/put** opcji.|  
|**/ del**|Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.|  
|**/e** *encodingType*|Określa typ kodowania certyfikatu. Wartość domyślna to `X509_ASN_ENCODING`.|  
|**/f** *Flagidw*|Określa flagę otwarcia magazynu. Jest to *Flagidw* parametr przekazany do **CertOpenStore**. Wartość domyślna to CERT_SYSTEM_STORE_CURRENT_USER. Ta opcja jest uwzględniana tylko wtedy, gdy **/y** jest używana opcja.|  
|**/ h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/n** *nazwa*|Określa wspólną nazwę certyfikatu do dodania, usunięcia lub zapisania. Tej opcji można używać tylko z certyfikatami; nie można używać jej z listami CTL i CRL.|  
|**/ put**|Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku. Plik jest zapisywany w formacie X.509. Możesz użyć **/7** z opcją **/put** opcję, aby zapisać plik w formacie PKCS #7. **/Put** opcji musi następować albo **/c**, **/CTL**, lub **/CRL**. **/All** opcji nie można używać z **/put**.|  
|**/r** *lokalizacji*|Określa lokalizację w rejestrze magazynu systemowego. Ta opcja jest uwzględniana tylko wtedy, gdy należy określić **/s** opcji. *Lokalizacja* musi mieć jedną z następujących czynności:<br /><br /> -   `currentUser` Wskazuje, że magazyn certyfikatów znajduje się w kluczu HKEY_CURRENT_USER. Domyślnie włączone.<br />-   `localMachine` Wskazuje, że magazyn certyfikatów znajduje się w kluczu HKEY_LOCAL_MACHINE.|  
|**/s**|Wskazuje, że magazyn certyfikatów jest magazynem systemowym. Jeśli ta opcja nie jest określona, za magazyn jest uważany za **StoreFile**.|  
|**{1** *wartośćskrótusha1*|Określa skrót SHA1 certyfikatu, listy CTL lub CRL do dodania, usunięcia lub zapisania.|  
|**/v**|Określa tryb pełny; wyświetla szczegółowe informacje dotyczące certyfikatu oraz list CTL i CRL. Tej opcji nie można używać z **/ add**, **/del**, lub **/put** opcje.|  
|**/y** *dostawcy*|Określa nazwę dostawcy magazynu.|  
|**/7**|Zapisuje magazyn docelowy jako obiekt w formacie PKCS #7.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Program Certmgr.exe wykonuje następujące podstawowe funkcje:  
  
-   Wyświetla na konsoli certyfikaty oraz listy CTL i CRL.  
  
-   Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.  
  
-   Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.  
  
-   Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.  
  
 Certmgr.exe działa z dwoma typami magazynów certyfikatów: **StoreFile** i magazynem systemowym. Nie jest konieczne określanie typu magazynu certyfikatów; program Certmgr.exe może zidentyfikować typ magazynu i wykonać odpowiednie operacje.  
  
 Uruchomienie programu Certmgr.exe bez określenia żadnej opcji spowoduje uruchomienie przystawki certmgr.msc wyposażonej w graficzny interfejs użytkownika ułatwiający wykonywanie zadań zarządzania certyfikatami, które są również dostępne w wierszu polecenia. Graficzny interfejs użytkownika dostarcza kreatora importu, który kopiuje certyfikaty oraz listy CTL i CRL z dysku do magazynu certyfikatów.  
  
 Można znaleźć nazwy magazynów X509Certificate dla `sourceStorename` i `destinationStorename` parametrów, kompilując i uruchamiając poniższy kod.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Aby uzyskać więcej informacji na temat certyfikatów, zobacz [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie wyświetla domyślny magazyn systemowy o nazwie `my` z pełnymi danymi wyjściowymi.  
  
```  
certmgr /v /s my  
```  
  
 Następujące polecenie dodaje wszystkie certyfikaty w pliku o nazwie `myFile.ext` do nowego pliku o nazwie `newFile.ext`.  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Następujące polecenie dodaje certyfikat z pliku o nazwie `testcert.cer` do `my` magazynu systemu.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 Następujące polecenie dodaje certyfikat z pliku o nazwie `TrustedCert.cer` do głównego magazynu certyfikatów.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Poniższe polecenie zapisuje certyfikat z nazwą pospolitą `myCert` w `my` magazynu systemu do pliku o nazwie `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Następujące polecenie usuwa wszystkie listy CTL z `my` magazynu systemowego i zapisuje magazyn wynikowy w pliku o nazwie `newStore.str`.  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Poniższe polecenie zapisuje certyfikat w `my` magazynu systemu w pliku `newFile`. Użytkownik jest monitowany o podanie numeru certyfikatu z `my` należy umieścić w `newFile`.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (narzędzie tworzenia certyfikatów)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
