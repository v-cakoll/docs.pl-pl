---
title: -langversion (opcje kompilatora C#)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: ee23c962d8ea9adecabc5146af75419c87fcc75a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516801"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (opcje kompilatora C#)

Powoduje, że kompilator, aby zaakceptować składni, który znajduje się w wybranym specyfikacja języka C#.  
  
## <a name="syntax"></a>Składnia  

```console
-langversion:option  
```

## <a name="arguments"></a>Argumenty

 `option`  
 Następujące wartości są prawidłowe:  
  
|Opcja|Znaczenie|  
|------------|-------------|  
|default|Kompilator akceptuje wszystkie składni języka prawidłowy z najnowszej wersji głównej, która może obsługiwać.|
|ISO-1|Kompilator akceptuje tylko składnię, który znajduje się w 23270:2003 ISO/IEC C# (1.0/1.2) <sup id="TISO1"> [ISO1](#FISO1)</sup>|  
|ISO-2|Kompilator akceptuje tylko w przypadku składni, która znajduje się w 23270:2006 ISO/IEC C# (2.0) <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|3|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku C# 3.0 lub niższą <sup id="TCS3"> [CS3](#FCS3)</sup>|
|4|Kompilator akceptuje tylko w przypadku składni, która jest dostępna w języku C# 4.0 lub niższy <sup id="TCS4"> [CS4](#FCS4)</sup>|
|5|Kompilator akceptuje tylko w przypadku składni, która jest dostępna w języku C# w wersji 5.0 lub niższe <sup id="TCS5"> [CS5](#FCS5)</sup>|
|6|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku C# 6.0 lub niższą <sup id="TCS6"> [CS6](#FCS6)</sup>|
|7|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku C# 7.0 lub niższą <sup id="TCS7"> [CS7](#FCS7)</sup>|
|7.1|Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku C# 7.1 lub niższą <sup id="TCS71"> [CS71](#FCS71)</sup>|
|7.2|Kompilator akceptuje składni, która jest dostępna w języku C# 7.2 lub niższą <sup id="TCS72"> [CS72](#FCS72)</sup>|
|7.3|Kompilator akceptuje tylko w przypadku składni, która jest dostępna w języku C# 7.3 lub niższy <sup id="TCS73"> [CS73](#FCS73)</sup>|
|najnowsza|Kompilator akceptuje wszystkie składni obowiązujący język, który może obsługiwać.|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

## <a name="remarks"></a>Uwagi

 Metadane odwołuje się aplikacja C# nie jest podlegają **- langversion** — opcja kompilatora.  
  
 Ponieważ każda wersja kompilatora języka C# zawiera rozszerzenia do specyfikacji języka **- langversion** nie daje równoważne funkcje starszej wersji kompilatora.  

 Ponadto podczas aktualizacji wersji języka C# zazwyczaj pokrywa się z głównymi wersjami .NET Framework, nową składnię i funkcje nie są zawsze związane z danej wersji określonym środowiskiem. Podczas gdy nowe funkcje wymagają zdecydowanie nowych aktualizacji kompilatora, która został wydany również obok wersji języka C#, każdą konkretną funkcję ma swój własny minimalny interfejs API platformy .NET lub wspólne wymagania środowiska uruchomieniowego języka, które mogą zezwolić na jego uruchomienie na struktur niskiego poziomu, umieszczając Pakiety NuGet lub inne biblioteki.
  
 Niezależnie od tego, który **- langversion** ustawienie użycia, użyjesz bieżącą wersję środowiska uruchomieniowego języka wspólnego do utworzenia Twojego .exe lub .dll. Jedynym wyjątkiem jest przyjaznych zestawów i [- moduleassemblyname (C# — opcja kompilatora)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), które działają w ramach **- langversion: ISO-1**.  

 Aby poznać inne sposoby Określ wersję języka C#, zobacz [wybierz wersję języka C#](../configure-language-version.md) tematu.
  
 Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

### <a name="c-language-specification"></a>Specyfikacja języka C#

|Wersja|Łącze|Opis|
|-------|----|-----------|
|C# 1.0|[Pobierz dokument](https://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|C#Wersja specyfikacji języka 1.0: Microsoft Corporation|
|C# 1.2|[Pobierz dokument](https://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|C#Language Specification w wersji 1.2: Microsoft Corporation|
|C# 2.0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|Standard ECMA 334 w wersji 4.|
|C# 3.0|[Pobierz dokument](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C#Wersja specyfikacji języka 3.0: Microsoft Corporation|
|C# 5.0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|Standard ECMA-334 5th Edition.|
|C# 6.0|[Link](../language-specification/index.md)|Wersja języka C# specyfikacji 6 - nieoficjalny wersja robocza: .NET Foundation|
|C# 7.0 lub nowszy||nie jest obecnie dostępna|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Wersja minimalna kompilatora potrzebnych do obsługi wszystkie funkcje językowe

[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .net 2002 lub powiązane Framework 1.0 kompilator [↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools w wersji 2005 lub powiązane .net Framework w wersji 2.0 kompilator [↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools w wersji 2008 lub powiązane .net Framework 3.5 kompilatora [↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools w wersji 2010 lub powiązane .net Framework 4.0 kompilatora [↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools w wersji 2012 lub powiązane .net Framework 4.5 kompilatora [↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015 [↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017 [↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017 w wersji 15.3 [↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017 w wersji 15.5 [↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017 wersji 15.7

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
