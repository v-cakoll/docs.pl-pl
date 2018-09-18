---
title: Peverify.exe (narzędzie PEVerify)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ae36736ac7174ff7f77ae5bba45e1fd3880169c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972978"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (narzędzie PEVerify)
Narzędzie PEVerify pomaga deweloperom, którzy generują język Microsoft intermediate language (MSIL) (na przykład twórcom kompilatorów, deweloperom aparatów skryptów itd.), w ustalaniu, czy ich kod MSIL i związane z nim metadane spełniają wymogi bezpieczeństwa typu. Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka. Jeśli jako programista używasz takiego kompilatora, możesz chcieć sprawdzić, czy nie występują zagrożenia bezpieczeństwa typów kodu. W tej sytuacji możesz uruchomić narzędzie PEVerify, aby sprawdzić MSIL i metadane plików.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|**/ break =** *maxErrorCount*|Przerywa weryfikację po *maxErrorCount* błędy.<br /><br /> Ten parametr nie jest obsługiwany w .NET Framework w wersji 2.0 lub wyższej.|  
|**/Clock**|Mierzy i raportuje następujące czasy weryfikacji w milisekundach:<br /><br /> **MD Val. cycle**<br /> Cykl sprawdzania poprawności metadanych<br /><br /> **MD Val. pure**<br /> Czysty czas sprawdzania poprawności metadanych<br /><br /> **IL Ver. cycle**<br /> Cykli weryfikacji języka pośredniego firmy Microsoft (MSIL)<br /><br /> **IL Ver pure**<br /> Czysty czas weryfikacji języka MSIL<br /><br /> **; MD Val. cycle** i **IL Ver. cycle** razy obejmują czas wymagany do wykonania niezbędnych procedur uruchamiania i zamykania. **MD Val. pure** i **IL Ver pure** razy odzwierciedlają czas wymagany do wykonania tylko sprawdzenia poprawności lub tylko weryfikacji.|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/hresult**|Wyświetla kody błędów w formacie szesnastkowym.|  
|**/ ignore =** *gt;Hex.Code* [, *gt;Hex.Code*]|Ignoruje wymienione kody błędów.|  
|**/ ignore = @** *responseFile*|Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.|  
|**/Il**|Przeprowadza weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie określonym przez *filename*. Narzędzie zwraca szczegółowe opisy dla każdego znalezionego, chyba że określisz problemu **/quiet** opcji.|  
|**/md**|Wykonuje sprawdzanie poprawności metadanych w zestawie określonym przez *filename*. Oznacza to przejrzenie pełnej struktury metadanych w pliku i raportowanie wszystkich napotkanych problemów.|  
|**/nologo**|Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.|  
|**/nosymbols**|W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.|  
|**/quiet**|Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji. Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.|  
|`/transparent`|Weryfikuje tylko metody przezroczyste.|  
|**/unique**|Ignoruje powtarzające się kody błędów.|  
|**/verbose**|W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji. Normalnie, kodu, który nie jest [sprawdzalnie bezpieczny](https://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) nie można uruchomić, chociaż można ustawić zasady zabezpieczeń umożliwiające wykonanie kodu zaufanego, choć nieweryfikowalnego.  
  
 Jeśli żadna **/MD** ani **/il** opcje są określone, Peverify.exe wykonuje oba rodzaje sprawdzenia. Peverify.exe wykonuje **/MD** najpierw sprawdza. Jeśli nie ma żadnych błędów **/il** kontrole są wprowadzane. Jeśli określisz zarówno **/MD** i **/il**, **/il** kontrole są wprowadzane, nawet jeśli występują błędy w metadanych. Dlatego, jeśli nie ma żadnych błędów metadanych **peverify** *filename* jest odpowiednikiem **peverify** *filename*   **/MD** **/il**.  
  
 Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych. Aby uzyskać szczegółowe informacje dotyczące kontroli Peverify.exe wykonuje, zobacz "Specyfikacja sprawdzania poprawności metadanych" i "Specyfikacja zestawu instrukcji MSIL" w folderze Tools Developers Guide [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
 Należy pamiętać, że .NET Framework w wersji 2.0 lub nowszej obsługuje weryfikowalne `byref` zwraca określony przy użyciu następujących instrukcji MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` i `unbox`.  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`.  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 Poniższe polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`. Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.  
  
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
  
 Poniższe polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`. Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100. Narzędzie ignoruje także wymienione kody błędów.  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Następujące polecenie daje ten sam wynik, jak w poprzednim przykładzie powyżej, ale Określa kody błędów do zignorowania w pliku odpowiedzi `ignoreErrors.rsp`.  
  
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
 [NIB: Pisanie Sprawdzalnie bezpieczny kod](https://msdn.microsoft.com/library/d18f10ef-3b48-4f47-8726-96714021547b)  
 [Zabezpieczenia i ochrona typu](https://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
