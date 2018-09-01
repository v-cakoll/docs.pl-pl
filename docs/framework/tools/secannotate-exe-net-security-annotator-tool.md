---
title: SecAnnotate.exe (Narzędzie adnotacji dotyczące zabezpieczeń w programach .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d00fb16ac5b71c8fb8f8560f68d20f1f33987d7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396889"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (Narzędzie adnotacji dotyczące zabezpieczeń w programach .NET)
Narzędzie .NET Security Annotator (SecAnnotate.exe) jest aplikacją wiersza polecenia, który identyfikuje `SecurityCritical` i `SecuritySafeCritical` części jeden lub więcej zestawów.  
  
 Rozszerzenia programu Visual Studio [Security Annotator](https://go.microsoft.com/fwlink/?LinkId=198007)zapewnia graficzny interfejs użytkownika do SecAnnotate.exe i umożliwia uruchomić narzędzie z poziomu programu Visual Studio.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie, gdzie *parametry* są opisane w poniższej sekcji i *zestawy* składają się z jednego lub więcej nazw zestawów rozdzielonych odstępami:  
  
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
|`/r:` *Zestaw*<br /><br /> lub<br /><br /> `/referenceassembly:` *Zestaw*|Dołącza określony zestaw podczas rozpoznawania zestawów zależnych w trakcie oznaczania adnotacjami. Zestawy, do których występują odwołania, otrzymują większy priorytet niż zestawy znajdujące się w ścieżce odwołania.|  
|`/s:` *RuleName*<br /><br /> lub<br /><br /> `/suppressrule:` *RuleName*|Pomija uruchamianie określonych reguł przezroczystości w zestawach wejściowych.|  
|`/t`<br /><br /> lub<br /><br /> `/forcetransparent`|Wymusza, aby narzędzie Annotator traktowało wszystkie zestawy, które nie mają adnotacji przezroczystości, tak jakby były całkowicie przezroczyste.|  
|`/t`:*zestawu*<br /><br /> lub<br /><br /> `/forcetransparent`:*zestawu*|Wymusza przezroczystość danego zestawu, niezależnie od jego bieżących adnotacji na poziomie zestawu.|  
|||  
|`/v`<br /><br /> lub<br /><br /> `/verify`|Sprawdza tylko, czy adnotacje zestawu są poprawne; nie podejmuje próby wykonania wielu przebiegów w celu znalezienia wszystkich wymaganych adnotacji, jeśli zestaw tego nie weryfikuje.|  
|`/x`<br /><br /> lub<br /><br /> `/verbose`|Określa pełne dane wyjściowe podczas oznaczania adnotacjami.|  
|`/y:` *Katalog*<br /><br /> lub<br /><br /> `/symbolpath:` *Katalog*|Uwzględnia określony katalog podczas wyszukiwania plików symboli w trakcie oznaczania adnotacjami.|  
  
## <a name="remarks"></a>Uwagi  
 Parametry i zestawy można także podać w pliku odpowiedzi, który jest określany w wierszu polecenia i poprzedzany znakiem (@). Każdy wiersz w pliku odpowiedzi musi zawierać pojedynczy parametr lub nazwę zestawu.  
  
 Aby uzyskać więcej informacji dotyczących narzędzia .NET Security Annotator, zobacz wpis [przy użyciu SecAnnotate w celu analizowania zestawów pod kątem naruszeń przezroczystości](https://go.microsoft.com/fwlink/?LinkId=187648) w blogu dotyczącym zabezpieczeń .NET.  
  
## <a name="examples"></a>Przykłady
