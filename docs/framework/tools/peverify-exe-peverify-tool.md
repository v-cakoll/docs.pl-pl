---
title: "Peverify.exe (narzędzie PEVerify)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5d9adcfe701b5897c434dc1479b9692448d8b98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (narzędzie PEVerify)
Narzędzie PEVerify pomaga deweloperom, którzy generują język Microsoft intermediate language (MSIL) (na przykład twórcom kompilatorów, deweloperom aparatów skryptów itd.), w ustalaniu, czy ich kod MSIL i związane z nim metadane spełniają wymogi bezpieczeństwa typu. Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka. Jeśli jako programista używasz takiego kompilatora, możesz chcieć sprawdzić, czy nie występują zagrożenia bezpieczeństwa typów kodu. W tej sytuacji możesz uruchomić narzędzie PEVerify, aby sprawdzić MSIL i metadane plików.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*Nazwa pliku*|Przenośny plik wykonywalny (PE), który ma zostać sprawdzony pod kątem języka MSIL i metadanych.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ Podziel =** *maxErrorCount*|Przerywa weryfikacji po *maxErrorCount* błędy.<br /><br /> Ten parametr nie jest obsługiwany w .NET Framework w wersji 2.0 lub wyższej.|  
|**/Clock**|Mierzy i raportuje następujące czasy weryfikacji w milisekundach:<br /><br /> **Cykl MD Val.**<br /> Cykl sprawdzania poprawności metadanych<br /><br /> **MD Val. czysty**<br /> Czysty czas sprawdzania poprawności metadanych<br /><br /> **Cykl wersja IL**<br /> Cykli weryfikacji języka pośredniego firmy Microsoft (MSIL)<br /><br /> **Czysty Ver IL**<br /> Czysty czas weryfikacji języka MSIL<br /><br /> **Cyklu MD Val.** i **cyklu wersja IL** razy obejmuje czasu wymaganego do wykonania niezbędnych procedur uruchamiania i wyłączania. **Val. MD czysty** i **Ver IL czysty** razy uwzględnienia czasu wymagane do przeprowadzenia weryfikacji lub tylko weryfikacji.|  
|**/ Help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/HRESULT**|Wyświetla kody błędów w formacie szesnastkowym.|  
|**/ Ignoruj =** *hex.code* [, *hex.code*]|Ignoruje wymienione kody błędów.|  
|**/ Ignoruj = @** *responseFile*|Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.|  
|**/Il**|Sprawdza MSIL typu bezpieczeństwa weryfikacji dla metod zaimplementowanych w zestawie określony przez *filename*. Narzędzie zwraca szczegółowy opis każdego problemu znaleziono, chyba że zostanie **/quiet** opcji.|  
|**/ / MD**|Przeprowadza weryfikację metadanych dla zestawu określony przez *filename*. Oznacza to przejrzenie pełnej struktury metadanych w pliku i raportowanie wszystkich napotkanych problemów.|  
|**/nologo**|Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.|  
|**/nosymbols**|W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.|  
|**/quiet**|Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji. Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.|  
|`/transparent`|Weryfikuje tylko metody przezroczyste.|  
|**/ unique**|Ignoruje powtarzające się kody błędów.|  
|**/verbose**|W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji. Zazwyczaj kod, który nie jest [sprawdzalnie bezpieczny typ](http://msdn.microsoft.com/en-us/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) nie można uruchomić, chociaż można ustawić zasady zabezpieczeń, aby umożliwić wykonywanie kodu zaufane, ale niemożliwy.  
  
 Jeśli żadna **/ / MD** ani **/il** opcje są określone, Peverify.exe wykonuje obu typów kontroli. Wykonuje Peverify.exe **/ / MD** najpierw sprawdza. Jeśli nie ma żadnych błędów **/il** kontroli. Jeśli możesz określić ich obu **/ / MD** i **/il**, **/il** sprawdzane jest nawet, jeśli występują błędy w metadanych. W związku z tym, jeśli nie ma żadnych błędów metadanych **peverify** *filename* jest odpowiednikiem **peverify** *filename* **/ / MD** **/il**.  
  
 Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych. Aby uzyskać szczegółowe informacje na temat testów wykonuje Peverify.exe, zobacz specyfikację"Weryfikacja metadanych" i "MSIL instrukcji ustawić specyfikację" w folderze Narzędzia przewodnik dla deweloperów w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
 Zauważ, że .NET Framework w wersji 2.0 lub nowszej obsługuje weryfikowalny `byref` zwraca określone z poniższymi instrukcjami MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` i `unbox`.  
  
## <a name="examples"></a>Przykłady  
 Polecenie wykonuje sprawdzanie poprawności metadanych i MSIL typu bezpieczeństwa weryfikację dla metod zaimplementowanych w zestawie `myAssembly.exe`.  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 Polecenie wykonuje sprawdzanie poprawności metadanych i MSIL typu bezpieczeństwa weryfikację dla metod zaimplementowanych w zestawie `myAssembly.exe`. Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 Polecenie wykonuje sprawdzanie poprawności metadanych i MSIL typu bezpieczeństwa weryfikację dla metod zaimplementowanych w zestawie `myAssembly.exe`. Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100. Narzędzie ignoruje także wymienione kody błędów.  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Poniższe polecenie tworzy taki sam efekt co w poprzednim przykładzie powyżej, ale Określa kody błędów, aby zignorować w pliku odpowiedzi `ignoreErrors.rsp`.  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 Plik odpowiedzi może zawierać rozdzielaną przecinkami listę kodów błędów.  
  
```  
0x12345678, 0xABCD1234  
```  
  
 Można też sformatować plik odpowiedzi, podając każdy kod błędu w osobnym wierszu.  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [NIB: Sprawdzalnie bezpieczny kod zapisywania](http://msdn.microsoft.com/en-us/d18f10ef-3b48-4f47-8726-96714021547b)  
 [Typ bezpieczeństwa i zabezpieczeń](http://msdn.microsoft.com/en-us/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
