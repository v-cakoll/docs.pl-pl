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
ms.openlocfilehash: 2a9501c883fec7478932b22ea2cdcad70865e0fd
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696289"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (opcje kompilatora C#)
Powoduje, że kompilator, aby zaakceptować tylko składni, który znajduje się w wybranym specyfikacja języka C#.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Prawidłowe są następujące wartości:  
  
|Opcja|Znaczenie|  
|------------|-------------|  
|default|Kompilator akceptuje wszystkie składni języka prawidłowe z najnowszej wersji głównych, który może obsługiwać.|
|ISO-1|Kompilator akceptuje tylko składni, który znajduje się w 23270:2003 ISO/IEC C# (1.0/1.2) <sup id="TISO1"> [ISO1](#FISO1)</sup>|  
|ISO-2|Kompilator akceptuje tylko składni, który znajduje się w 23270:2006 ISO/IEC C# (2.0) <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|3|Kompilator akceptuje tylko składnię, która jest dostępna w C# 3.0 lub niższy <sup id="TCS3"> [CS3](#FCS3)</sup>|
|4|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 4.0 lub niższy <sup id="TCS4"> [CS4](#FCS4)</sup>|
|5|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 5.0 lub niższy <sup id="TCS5"> [CS5](#FCS5)</sup>|
|6|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 6.0 lub niższy <sup id="TCS6"> [CS6](#FCS6)</sup>|
|7|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 7.0 lub niższy <sup id="TCS7"> [CS7](#FCS7)</sup>|
|7.1|Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.1 lub niższy <sup id="TCS71"> [CS71](#FCS71)</sup>|
|7.2|Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.2 lub niższy <sup id="TCS72"> [CS72](#FCS72)</sup>|
|7.3|Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.3 lub niższy <sup id="TCS73"> [CS73](#FCS73)</sup>|
|najnowsze|Kompilator akceptuje wszystkie składni odpowiedni język, który może obsługiwać.|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>Uwagi  
 Metadane odwołuje się aplikacji C# nie jest warunkiem **- langversion** — opcja kompilatora.  
  
 Ponieważ każdy wersji kompilatora C# zawiera rozszerzenia w specyfikacji języka **- langversion** nie daje równoważne funkcje wcześniejszej wersji kompilatora.  
 
 Ponadto podczas aktualizacji wersji języka C# pokrywają się zazwyczaj z główne wersje .NET Framework, nowej składni i funkcje nie są zawsze związane z danej wersji określonej platformy. Podczas gdy nowe funkcje wymagają ostatecznie nową aktualizację kompilatora wydaną obok poprawki C#, każdej z funkcji ma własną minimalny interfejs API .NET lub typowe wymagania środowiska uruchomieniowego języka, które mogą zezwolenie na uruchamianie na platformach niskiego poziomu, umieszczając w niej Pakiety NuGet lub innych bibliotek.
  
 Niezależnie od tego, który **- langversion** ustawienie używanie użyjesz bieżącą wersję środowiska CLR do utworzenia .exe lub .dll. Jedynym wyjątkiem jest przyjaznych zestawów i [- moduleassemblyname (opcja kompilatora C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), która pracy w obszarze **- langversion: ISO-1**.  
 
 Aby inne sposoby Określ wersję języka C#, zobacz [wybierz wersję języka C#](../configure-language-version.md) tematu.
  
 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
    
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a>Specyfikacja języka C#

|Wersja|Łącze|Opis|
|-------|----|-----------|
|C# 1.0|[Pobieranie dokumentu](http://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|C# specyfikacji języka w wersji 1.0: Microsoft Corporation|
|C# 1.2|[Pobieranie dokumentu](http://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|C# specyfikacji języka w wersji 1.2: Microsoft Corporation|
|C# 2.0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|ECMA-334 4. w wersji Standard|
|C# 3.0|[Pobieranie dokumentu](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# specyfikacji języka w wersji 3.0: Microsoft Corporation|
|C# W WERSJI 5.0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|ECMA-334 5. w wersji Standard|
|C# W WERSJI 6.0|[Link](../language-specification/index.md)|C# specyfikacji języka w wersji 6 - nieoficjalny projektu: Foundation .NET|
|C# 7.0 lub nowszym||Nie jest obecnie dostępna|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Wersja minimalna kompilatora potrzebnych do obsługi wszystkich funkcji języka   
[↩](#TISO1)<a name="FISO1">ISO1</a>: .net programu Microsoft Visual Studio/Build Tools 2002 lub powiązane .net Framework 1.0 kompilatora     
[↩](#TISO2)<a name="FISO2">ISO2</a>: program Microsoft Visual Studio/kompilacji narzędzia 2005 lub powiązane .net Framework 2.0 kompilatora    
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/kompilacji narzędzia 2008 lub powiązane .net Framework 3.5 kompilatora    
[↩](#TCS4)<a name="FCS4">CS4</a>: programu Microsoft Visual Studio/kompilacji narzędzia 2010 lub powiązane .net Framework 4.0 kompilatora    
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/kompilacji narzędzia 2012 lub powiązane .net Framework 4.5 kompilatora    
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>: 2017 narzędzi Microsoft Visual Studio/kompilacji   
[↩](#TCS71)<a name="FCS71">CS71</a>: 2017 firmy Microsoft do narzędzi Visual Studio/kompilacji, wersji 15 ustęp 3    
[↩](#TCS72)<a name="FCS72">CS72</a>: 2017 firmy Microsoft do narzędzi Visual Studio/kompilacji, wersja 15,5 cala    
[↩](#TCS73)<a name="FCS73">CS73</a>: 2017 firmy Microsoft do narzędzi Visual Studio/kompilacji, wersja 15.7    

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
