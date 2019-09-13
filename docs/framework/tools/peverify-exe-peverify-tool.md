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
ms.openlocfilehash: ac0b45db0e9aebae830155cbe2469514c392921d
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894831"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (narzędzie PEVerify)
Narzędzie PEVerify pomaga deweloperom, którzy generują język Microsoft intermediate language (MSIL) (na przykład twórcom kompilatorów, deweloperom aparatów skryptów itd.), w ustalaniu, czy ich kod MSIL i związane z nim metadane spełniają wymogi bezpieczeństwa typu. Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka. Jeśli jako programista używasz takiego kompilatora, możesz chcieć sprawdzić, czy nie występują zagrożenia bezpieczeństwa typów kodu. W tej sytuacji możesz uruchomić narzędzie PEVerify, aby sprawdzić MSIL i metadane plików.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*Nazwa pliku*|Przenośny plik wykonywalny (PE), który ma zostać sprawdzony pod kątem języka MSIL i metadanych.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Break =** *maxErrorCount*|Przerywa weryfikację po błędach *maxErrorCount* .<br /><br /> Ten parametr nie jest obsługiwany w .NET Framework w wersji 2.0 lub wyższej.|  
|**/clock**|Mierzy i raportuje następujące czasy weryfikacji w milisekundach:<br /><br /> **MD Val. cykl**<br /> Cykl sprawdzania poprawności metadanych<br /><br /> **MD Val. Pure**<br /> Czysty czas sprawdzania poprawności metadanych<br /><br /> **IL Ver. Cycle**<br /> Cykli weryfikacji języka pośredniego firmy Microsoft (MSIL)<br /><br /> **Kod IL Ver**<br /> Czysty czas weryfikacji języka MSIL<br /><br /> Czasy **MD Val. Cycle** i **Il Ver. Cycle** obejmują czas wymagany do wykonania niezbędnych procedur uruchamiania i zamykania. Wartość **MD Val. Pure** i **Il Ver czyste** czasy są odzwierciedlać czas wymagany do przeprowadzenia walidacji lub weryfikacji.|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/hresult**|Wyświetla kody błędów w formacie szesnastkowym.|  
|**/Ignore =** *hex. Code* [, *hex. Code*]|Ignoruje wymienione kody błędów.|  
|**/Ignore = @** *responseFile*|Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.|  
|**/Il**|Wykonuje weryfikację bezpieczeństwa typu MSIL dla metod zaimplementowanych w zestawie określonym przez *filename*. Narzędzie zwraca szczegółowe opisy dla każdego wykrytego problemu, chyba że zostanie określona opcja **/quiet** .|  
|**/md**|Wykonuje sprawdzanie poprawności metadanych na zestawie określonym przez *filename*. Oznacza to przejrzenie pełnej struktury metadanych w pliku i raportowanie wszystkich napotkanych problemów.|  
|**/nologo**|Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.|  
|**/nosymbols**|W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.|  
|**/quiet**|Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji. Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.|  
|`/transparent`|Weryfikuje tylko metody przezroczyste.|  
|**/unique**|Ignoruje powtarzające się kody błędów.|  
|**/verbose**|W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji. Zwykle kod, który nie jest [typu](../../standard/security/key-security-concepts.md#type-safety-and-security) "nie sprawdza się", nie może zostać uruchomiony, chociaż można ustawić zasady zabezpieczeń, aby zezwalać na wykonywanie kodu zaufanego, ale niemożliwego do zweryfikowania.  
  
 Jeśli nie określono opcji **/MD** ani **/Il** , PEVerify. exe wykonuje oba typy kontroli. PEVerify. exe wykonuje najpierw testy **/MD** . W przypadku braku błędów **/Il** są przeprowadzane sprawdzenia. W przypadku określenia zarówno **/MD** , jak i **/Il**testy **/Il** są wykonywane nawet wtedy, gdy w metadanych występują błędy. W takim przypadku, jeśli nie występują błędy metadanych, **PEVerify** *filename* jest równoważne **PEVerify** *filename* **/MD** **/Il**.  
  
 Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych. Aby uzyskać szczegółowe informacje na temat sprawdzania PEVerify. exe, zobacz "Specyfikacja walidacji metadanych" i "Specyfikacja zestawu instrukcji MSIL" w folderze przewodnika deweloperów narzędzi w Windows SDK.  
  
 Należy zauważyć, że .NET Framework w wersji 2,0 lub nowszej `byref` obsługuje sprawdzone zwroty określone przy użyciu następujących instrukcji `ldsflda`MSIL `ldflda`: `ldelema` `dup`, `call` , `unbox`, i.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`.  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`. Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`. Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100. Narzędzie ignoruje także wymienione kody błędów.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Poniższe polecenie daje ten sam wynik jak powyżej poprzedniego przykładu, ale określa kody błędów do zignorowania w pliku `ignoreErrors.rsp`odpowiedzi.  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 Plik odpowiedzi może zawierać rozdzielaną przecinkami listę kodów błędów.  
  
```text
0x12345678, 0xABCD1234  
```  
  
 Można też sformatować plik odpowiedzi, podając każdy kod błędu w osobnym wierszu.  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Pisanie kodu z bezpiecznym typem](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)
- [Bezpieczeństwo i zabezpieczenia typów](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
