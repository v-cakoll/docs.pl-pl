---
title: Peverify.exe (narzędzie PEVerify)
description: Użyj Peverify.exe (Weryfikuj przenośny plik wykonywalny), aby pomóc w ustaleniu, czy kod języka pośredniego (MSIL) firmy Microsoft & metadane spełniają standardy bezpieczeństwa typów w programie .NET.
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
ms.openlocfilehash: 478c04a45c7f9d3ad568a6bc4a12a89fe786583a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325621"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (Narzędzie PEVerify)

Narzędzie PEVerify pomaga deweloperom, którzy generują język pośredni (MSIL) firmy Microsoft (na przykład autorzy kompilatora i deweloperzy aparatów skryptów), aby określić, czy ich kod MSIL i powiązane metadane spełniają wymagania bezpieczeństwa typu. Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka. Jeśli używasz takiego kompilatora, możesz sprawdzić, czy nie naruszono bezpieczeństwa typu kodu. Aby sprawdzić MSIL i metadane, można uruchomić narzędzie PEVerify na plikach.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).
  
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
|**/Help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/hresult**|Wyświetla kody błędów w formacie szesnastkowym.|  
|**/Ignore =** *szesnastkowy. kod* [, *szesnastkowy. Code*]|Ignoruje wymienione kody błędów.|  
|**/Ignore = @** *responseFile*|Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.|  
|**/Il**|Wykonuje weryfikację bezpieczeństwa typu MSIL dla metod zaimplementowanych w zestawie określonym przez *filename*. Narzędzie zwraca szczegółowe opisy dla każdego wykrytego problemu, chyba że zostanie określona opcja **/quiet** .|  
|**/MD**|Wykonuje sprawdzanie poprawności metadanych na zestawie określonym przez *filename*. Ta opcja przeprowadzi pełną strukturę metadanych w pliku i zgłosi wszystkie problemy z walidacją.|  
|**/nologo**|Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.|  
|**/nosymbols**|W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.|  
|**spowoduje**|Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji. Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.|  
|`/transparent`|Weryfikuje tylko metody przezroczyste.|  
|**/Unique**|Ignoruje powtarzające się kody błędów.|  
|**/verbose**|W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji. Zwykle kod, który nie jest [typu](../../standard/security/key-security-concepts.md#type-safety-and-security) "nie sprawdza się", nie może zostać uruchomiony, chociaż można ustawić zasady zabezpieczeń, aby zezwalać na wykonywanie kodu zaufanego, ale niemożliwego do zweryfikowania.  
  
 Jeśli nie określono opcji **/MD** ani **/Il** , Peverify.exe wykonuje oba typy kontroli. Peverify.exe wykonuje najpierw testy **/MD** . W przypadku braku błędów **/Il** są przeprowadzane sprawdzenia. W przypadku określenia zarówno **/MD** , jak i **/Il**testy **/Il** są wykonywane nawet wtedy, gdy w metadanych występują błędy. W takim przypadku, jeśli nie występują błędy metadanych, **PEVerify** *filename* jest równoważne **PEVerify** *filename* **/MD** **/Il**.  
  
 Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych. Aby uzyskać szczegółowe informacje na temat sprawdzanych Peverify.exe, zobacz "Specyfikacja walidacji metadanych" i "Specyfikacja zestawu instrukcji MSIL" w folderze przewodnika deweloperów narzędzi w Windows SDK.  
  
.NET Framework w wersji 2,0 lub nowszej obsługuje sprawdzone `byref` zwroty określone przy użyciu następujących instrukcji MSIL: `dup` ,,,, `ldsflda` `ldflda` `ldelema` `call` i `unbox` .  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe` .  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe` . Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.  
  
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
  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe` . Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100. Narzędzie ignoruje także wymienione kody błędów.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Poniższe polecenie daje ten sam wynik jak powyżej poprzedniego przykładu, ale określa kody błędów do zignorowania w pliku odpowiedzi `ignoreErrors.rsp` .  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Narzędzia](index.md)
- [Pisanie kodu z bezpiecznym typem](../misc/code-access-security-basics.md#typesafe_code)
- [Bezpieczeństwo i zabezpieczenia typów](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Wiersze poleceń](developer-command-prompt-for-vs.md)
