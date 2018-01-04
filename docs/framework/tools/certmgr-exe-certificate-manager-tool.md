---
title: "Certmgr.exe (Menedżer certyfikatów)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c303a9d91d12305bd8be4e111aaa8d6ac13eb77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Menedżer certyfikatów)
Narzędzie Menedżer certyfikatów (Certmgr.exe) zarządza certyfikatami, listami zaufania certyfikatów (CTL) oraz listami odwołania certyfikatów (CRL).  
  
 Menedżer certyfikatów jest instalowany automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Narzędzie Menedżer certyfikatów (Certmgr.exe) jest narzędziem wiersza polecenia, natomiast narzędzie Certyfikaty (Certmgr.msc) jest przystawką programu Microsoft Management Console (MMC). Ponieważ Certmgr.msc zazwyczaj znajduje się w katalogu systemu Windows, wprowadzając `certmgr` w wierszu polecenia może załadować przystawki certyfikatów konsoli MMC nawet, jeśli został otwarty wiersz polecenia programu Visual Studio. Dzieje się tak, ponieważ ścieżka do przystawki ma pierwszeństwo przed ścieżką do narzędzia Menedżer certyfikatów w zmiennej środowiskowej PATH. Jeśli wystąpi ten problem, można wykonywać polecenia programu Certmgr.exe, określając ścieżkę do pliku wykonywalnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Omówienie certyfikatów X.509, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
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
|**/ all**|Dodaje wszystkie wpisy z **/ add**. Usuwa wszystkie wpisy z **/del**. Wyświetla wszystkie wpisy użyte bez **/ add** lub **/del** opcje. **/All** nie można użyć opcji **/put**.|  
|**/c**|Dodaje certyfikatów, gdy jest używany z **/ add**. Usuwa certyfikatów, gdy jest używany z **/del**. Zapisuje certyfikatów, gdy jest używany z **/put**. Wyświetla certyfikaty używane bez **/ add**, **/del**, lub **/put** opcji.|  
|**/ LIST CRL**|Dodaje list CRL w przypadku użycia z **/ add**. Usuwa listy CRL w przypadku użycia z **/del**. Zapisuje list CRL w przypadku użycia z **/put**. Wyświetla list CRL, gdy jest używany bez **/ add**, **/del**, lub **/put** opcji.|  
|**/ LIST CTL**|Dodaje listy CTL, gdy jest używany z **/ add**. Usuwa listy CTL, gdy jest używany z **/del**. Zapisuje listy CTL, gdy jest używany z **/put**. Wyświetla listy CTL, gdy jest używany bez **/ add**, **/del**, lub **/put** opcji.|  
|**/ del**|Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.|  
|**/e** *encodingType*|Określa typ kodowania certyfikatu. Wartość domyślna to `X509_ASN_ENCODING`.|  
|**/f** *wartość elementu dwFlags*|Określa flagę otwarcia magazynu. Jest to *wartość elementu dwFlags* parametr przekazany do **wywołanie funkcji CertOpenStore**. Wartość domyślna to CERT_SYSTEM_STORE_CURRENT_USER. Ta opcja jest uznawany za tylko wtedy, gdy **/y** jest używana opcja.|  
|**/h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/n***nam*|Określa wspólną nazwę certyfikatu do dodania, usunięcia lub zapisania. Tej opcji można używać tylko z certyfikatami; nie można używać jej z listami CTL i CRL.|  
|**/ put**|Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku. Plik jest zapisywany w formacie X.509. Można użyć **/7** opcję z **/put** opcję, aby zapisać plik w formacie PKCS #7. **/Put** opcja musi następować albo **/c**, **/CTL**, lub **/CRL**. **/All** nie można użyć opcji **/put**.|  
|**/r** *lokalizacji*|Określa lokalizację w rejestrze magazynu systemowego. Ta opcja jest uznawany za tylko w przypadku określenia **/s** opcji. *Lokalizacja* musi mieć jedną z następujących czynności:<br /><br /> -   `currentUser`Wskazuje, że magazyn certyfikatów jest w kluczu HKEY_CURRENT_USER. Domyślnie włączone.<br />-   `localMachine`Wskazuje, że magazyn certyfikatów jest w kluczu HKEY_LOCAL_MACHINE.|  
|**/ s**|Wskazuje, że magazyn certyfikatów jest magazynem systemowym. Jeśli ta opcja nie zostanie określony, magazynie jest uważany za **StoreFile**.|  
|**/SHA1** *sha1Hash*|Określa skrót SHA1 certyfikatu, listy CTL lub CRL do dodania, usunięcia lub zapisania.|  
|**/v**|Określa tryb pełny; wyświetla szczegółowe informacje dotyczące certyfikatu oraz list CTL i CRL. Nie można użyć tej opcji z **/ add**, **/del**, lub **/put** opcje.|  
|**/y** *dostawcy*|Określa nazwę dostawcy magazynu.|  
|**/7**|Zapisuje magazyn docelowy jako obiekt w formacie PKCS #7.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Program Certmgr.exe wykonuje następujące podstawowe funkcje:  
  
-   Wyświetla na konsoli certyfikaty oraz listy CTL i CRL.  
  
-   Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.  
  
-   Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.  
  
-   Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.  
  
 Certmgr.exe współpracuje z dwóch typów magazynów certyfikatów: **StoreFile** i magazynu systemu. Nie jest konieczne określanie typu magazynu certyfikatów; program Certmgr.exe może zidentyfikować typ magazynu i wykonać odpowiednie operacje.  
  
 Uruchomienie programu Certmgr.exe bez określenia żadnej opcji spowoduje uruchomienie przystawki certmgr.msc wyposażonej w graficzny interfejs użytkownika ułatwiający wykonywanie zadań zarządzania certyfikatami, które są również dostępne w wierszu polecenia. Graficzny interfejs użytkownika dostarcza kreatora importu, który kopiuje certyfikaty oraz listy CTL i CRL z dysku do magazynu certyfikatów.  
  
 Można znaleźć nazw magazynów w certyfikacie x 509 dla `sourceStorename` i `destinationStorename` parametrów, kompilowania i uruchamiając poniższy kod.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie wyświetla domyślny magazyn systemu o nazwie `my` z pełnymi danymi wyjściowymi.  
  
```  
certmgr /v /s my  
```  
  
 Polecenie dodaje wszystkie certyfikaty w pliku o nazwie `myFile.ext` do nowego pliku o nazwie `newFile.ext`.  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Polecenie dodaje certyfikat w pliku o nazwie `testcert.cer` do `my` magazynu systemu.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 Polecenie dodaje certyfikat w pliku o nazwie `TrustedCert.cer` do katalogu głównego magazynu certyfikatów.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Poniższe polecenie zapisuje certyfikat z nazwą pospolitą `myCert` w `my` magazynu systemu do pliku o nazwie `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Następujące polecenie usuwa wszystkie listy CTL w `my` magazynu systemu i zapisuje wynikowy magazynu w pliku o nazwie `newStore.str`.  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Poniższe polecenie zapisuje certyfikat w `my` magazynu systemu w pliku `newFile`. Pojawi się monit o wprowadzenie numeru certyfikatu z `my` mają zostać umieszczone w `newFile`.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (narzędzie tworzenia certyfikatów)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
