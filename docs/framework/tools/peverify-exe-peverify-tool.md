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
ms.openlocfilehash: 9d5f8c80937c36e975d42d6efb0a83295cb28be9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104980"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (narzędzie PEVerify)
Narzędzie PEVerify pomaga deweloperom, którzy generują język Microsoft intermediate language (MSIL) (na przykład twórcom kompilatorów, deweloperom aparatów skryptów itd.), w ustalaniu, czy ich kod MSIL i związane z nim metadane spełniają wymogi bezpieczeństwa typu. Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka. Jeśli jako programista używasz takiego kompilatora, możesz chcieć sprawdzić, czy nie występują zagrożenia bezpieczeństwa typów kodu. W tej sytuacji możesz uruchomić narzędzie PEVerify, aby sprawdzić MSIL i metadane plików.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*Pod nazwą*|Przenośny plik wykonywalny (PE), który ma zostać sprawdzony pod kątem języka MSIL i metadanych.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/break=** *maksymalna liczba*|Przerywa weryfikację po błędach *maxErrorCount.*<br /><br /> Ten parametr nie jest obsługiwany w .NET Framework w wersji 2.0 lub wyższej.|  
|**/zegar**|Mierzy i raportuje następujące czasy weryfikacji w milisekundach:<br /><br /> **Cykl MD Val.**<br /> Cykl sprawdzania poprawności metadanych<br /><br /> **MD Val. czysty**<br /> Czysty czas sprawdzania poprawności metadanych<br /><br /> **Cykl IL Ver.**<br /> Cykli weryfikacji języka pośredniego firmy Microsoft (MSIL)<br /><br /> **IL Ver czysty**<br /> Czysty czas weryfikacji języka MSIL<br /><br /> Cykl **MD Val.** i **czasy cyklu IL Ver.** obejmują czas wymagany do wykonania niezbędnych procedur uruchamiania i zamykania. **Md Val. pure** i **IL Ver czyste** razy odzwierciedlają czas wymagany do przeprowadzenia walidacji lub weryfikacji tylko.|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/hresult**|Wyświetla kody błędów w formacie szesnastkowym.|  
|**/ignore=** *hex.code* [, *hex.code*]|Ignoruje wymienione kody błędów.|  
|**/ignore=@** *responseFile*|Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.|  
|**/il**|Przeprowadza kontrole weryfikacji bezpieczeństwa typu MSIL dla metod zaimplementowanych w zestawie określonym przez *nazwę pliku*. Narzędzie zwraca szczegółowe opisy dla każdego znalezionego problemu, chyba że zostanie określona opcja **/quiet.**|  
|**/md**|Wykonuje sprawdzanie poprawności metadanych w zestawie określonym przez *nazwę pliku*. Oznacza to przejrzenie pełnej struktury metadanych w pliku i raportowanie wszystkich napotkanych problemów.|  
|**/nologo**|Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.|  
|**/nosymbols**|W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.|  
|**/cichy**|Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji. Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.|  
|`/transparent`|Weryfikuje tylko metody przezroczyste.|  
|**/unique**|Ignoruje powtarzające się kody błędów.|  
|**/pełne**|W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji. Zwykle nie można uruchomić kodu, który nie jest [sprawdzalny typ safe,](../../standard/security/key-security-concepts.md#type-safety-and-security) chociaż można ustawić zasady zabezpieczeń, aby umożliwić wykonanie kodu zaufanego, ale niemożliwego do zweryfikowania.  
  
 Jeśli nie określono opcji **/md** ani **/il,** program Peverify.exe wykonuje oba typy kontroli. Peverify.exe najpierw wykonuje **/md** sprawdza. Jeśli nie ma żadnych błędów, **/il** sprawdza są dokonywane. Jeśli określisz zarówno **/md,** jak i **/il**, **/il** kontrole są dokonywane, nawet jeśli w metadanych występują błędy. W związku z tym, jeśli nie ma żadnych błędów metadanych, nazwa *pliku* **peverify** jest odpowiednikiem nazwy *pliku* **peverify** **/md** **/il**.  
  
 Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych. Aby uzyskać szczegółowe informacje na temat kontroli wykonywanej przez program Peverify.exe, zobacz "Specyfikacja sprawdzania poprawności metadanych" i "Specyfikacja zestawu instrukcji MSIL" w folderze Przewodnik dla deweloperów narzędzi w zestawie Windows SDK.  
  
 Należy zauważyć, że program .NET Framework w wersji `byref` 2.0 lub nowszej obsługuje weryfikowalne zwroty określone przy `dup`użyciu następujących instrukcji MSIL: , `ldsflda`, `ldflda` `ldelema`, `call` i `unbox`.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i sprawdzanie bezpieczeństwa typu `myAssembly.exe`MSIL dla metod zaimplementowanych w zestawie .  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i sprawdzanie bezpieczeństwa typu `myAssembly.exe`MSIL dla metod zaimplementowanych w zestawie . Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.  
  
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
  
 Następujące polecenie wykonuje sprawdzanie poprawności metadanych i sprawdzanie bezpieczeństwa typu `myAssembly.exe`MSIL dla metod zaimplementowanych w zestawie . Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100. Narzędzie ignoruje także wymienione kody błędów.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Następujące polecenie daje taki sam wynik jak w powyższym poprzednim przykładzie, ale `ignoreErrors.rsp`określa kody błędów do zignorowania w pliku odpowiedzi .  
  
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

- [narzędzia](index.md)
- [Pisanie sprawdzalnie kod bezpieczny dla typu](../misc/code-access-security-basics.md#typesafe_code)
- [Bezpieczeństwo i ochrona typu](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
