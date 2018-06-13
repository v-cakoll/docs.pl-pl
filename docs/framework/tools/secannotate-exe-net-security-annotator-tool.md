---
title: SecAnnotate.exe (Narzędzie adnotacji dotyczące zabezpieczeń w programach .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f4712970b2d3ebecf12cbb7b8f9b7fcdb317986
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410354"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (Narzędzie adnotacji dotyczące zabezpieczeń w programach .NET)
Narzędzie adnotacji zabezpieczeń .NET (SecAnnotate.exe) jest aplikacją wiersza polecenia, który identyfikuje `SecurityCritical` i `SecuritySafeCritical` części jeden lub więcej zestawów.  
  
 Rozszerzenia programu Visual Studio [Security Annotator](http://go.microsoft.com/fwlink/?LinkId=198007), zawiera graficzny interfejs użytkownika do SecAnnotate.exe i umożliwia uruchamianie narzędzia w programie Visual Studio.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie, gdzie *parametry* są opisane w poniższej sekcji i *zestawy* składają się z co najmniej jedną nazwę zestawu, oddzielonych puste wartości:  
  
## <a name="syntax"></a>Składnia  
  
```  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/a`<br /><br /> lub<br /><br /> `/showstatistics`|Pokazuje statystykę użycia przezroczystości w analizowanych w ten sposób zestawach.|  
|`/d:` *Katalog*<br /><br /> lub<br /><br /> `/referencedir:` *Katalog*|Określa katalog, w którym mają być wyszukiwanie zależne zestawy podczas oznaczania adnotacjami.|  
|`/i`<br /><br /> lub<br /><br /> `/includesignatures`|Umieszcza rozszerzone informacje podpisu w pliku raportu oznaczania adnotacjami.|  
|`/n`<br /><br /> lub<br /><br /> `/nogac`|Pomija wyszukiwanie zestawów, których dotyczą odwołania, w globalnej pamięci podręcznej zestawów.|  
|`/o:` *OUTPUT.XML*<br /><br /> lub<br /><br /> `/out:` *OUTPUT.XML*|Określa wyjściowy plik adnotacji.|  
|`/p:` *maxpasses*<br /><br /> lub<br /><br /> `/maximumpasses:` *maxpasses*|Określa maksymalną liczbę adnotacji, które można przekazać do zestawów przed zatrzymaniem generowania nowych adnotacji.|  
|`/q`<br /><br /> lub<br /><br /> `/quiet`|Określa tryb cichy, w którym moduł oznaczający adnotacjami nie wyświetla komunikatów o stanie, ale tylko informacje o błędach.|  
|`/r:` *Zestawu*<br /><br /> lub<br /><br /> `/referenceassembly:` *Zestawu*|Dołącza określony zestaw podczas rozpoznawania zestawów zależnych w trakcie oznaczania adnotacjami. Zestawy, do których występują odwołania, otrzymują większy priorytet niż zestawy znajdujące się w ścieżce odwołania.|  
|`/s:` *RuleName*<br /><br /> lub<br /><br /> `/suppressrule:` *RuleName*|Pomija uruchamianie określonych reguł przezroczystości w zestawach wejściowych.|  
|`/t`<br /><br /> lub<br /><br /> `/forcetransparent`|Wymusza, aby narzędzie Annotator traktowało wszystkie zestawy, które nie mają adnotacji przezroczystości, tak jakby były całkowicie przezroczyste.|  
|`/t`:*zestawu*<br /><br /> lub<br /><br /> `/forcetransparent`:*zestawu*|Wymusza przezroczystość danego zestawu, niezależnie od jego bieżących adnotacji na poziomie zestawu.|  
|||  
|`/v`<br /><br /> lub<br /><br /> `/verify`|Sprawdza tylko, czy adnotacje zestawu są poprawne; nie podejmuje próby wykonania wielu przebiegów w celu znalezienia wszystkich wymaganych adnotacji, jeśli zestaw tego nie weryfikuje.|  
|`/x`<br /><br /> lub<br /><br /> `/verbose`|Określa pełne dane wyjściowe podczas oznaczania adnotacjami.|  
|`/y:` *Katalog*<br /><br /> lub<br /><br /> `/symbolpath:` *Katalog*|Uwzględnia określony katalog podczas wyszukiwania plików symboli w trakcie oznaczania adnotacjami.|  
  
## <a name="remarks"></a>Uwagi  
 Parametry i zestawy można także podać w pliku odpowiedzi, który jest określany w wierszu polecenia i poprzedzany znakiem (@). Każdy wiersz w pliku odpowiedzi musi zawierać pojedynczy parametr lub nazwę zestawu.  
  
 Aby uzyskać więcej informacji na temat Annotator zabezpieczeń .NET, zobacz wpis [przy użyciu SecAnnotate do analizowania zestawów Your za naruszenia przezroczystość](http://go.microsoft.com/fwlink/?LinkId=187648) w blogu .NET zabezpieczeń.  
  
## <a name="examples"></a>Przykłady
