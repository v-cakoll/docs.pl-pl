---
title: -langversion (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034958b14c54540aa175a23067d47bd5d850bab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-c-compiler-options"></a>/langversion (opcje kompilatora C#)
Powoduje, że kompilator, aby zaakceptować tylko składni, który znajduje się w wybranym specyfikacja języka C#.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/langversion:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Prawidłowe są następujące wartości:  
  
|Opcja|Znaczenie|  
|------------|-------------|  
|default|Kompilator akceptuje wszystkie składni odpowiedni język, który może obsługiwać. <sup id="TDefault">[Domyślne](#FDefault)</sup>| 
|ISO-1|Kompilator akceptuje tylko składni, który znajduje się w 23270:2003 ISO/IEC C# (1.0/1.1) <sup id="TISO1"> [ISO1](#FISO1)</sup>|  
|ISO-2|Kompilator akceptuje tylko składni, który znajduje się w 23270:2006 ISO/IEC C# (2.0) <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|3|Kompilator akceptuje tylko składnię, która jest dostępna w C# 3.0 lub niższy <sup id="TCS3"> [CS3](#FCS3)</sup>|
|4|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 4.0 lub niższy <sup id="TCS4"> [CS4](#FCS4)</sup>|
|5|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 5.0 lub niższy <sup id="TCS5"> [CS5](#FCS5)</sup>|
|6|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 6.0 lub niższy <sup id="TCS6"> [CS6](#FCS6)</sup>|
|7|Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 7.0 lub niższy <sup id="TCS7"> [CS7](#FCS7)</sup>|
|najnowsze|Kompilator akceptuje wszystkie składni odpowiedni język, który może obsługiwać. <sup id="TLatest">[Najnowsze](#FLatest)</sup>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>Uwagi  
 Metadane odwołuje się aplikacji C# nie jest warunkiem **/langversion** — opcja kompilatora.  
  
 Ponieważ każdy wersji kompilatora C# zawiera rozszerzenia w specyfikacji języka **/langversion** nie daje równoważne funkcje wcześniejszej wersji kompilatora.  
 
 Ponadto podczas aktualizacji wersji języka C# zazwyczaj pokrywa się z głównych .net Framework w wersji, nowej składni i funkcje nie są zawsze związane z danej wersji określonej platformy. Nowe funkcje ostatecznie wymaga nową aktualizację kompilatora wydaną obok poprawki C#, każdej z funkcji ma własną minimalny interfejs API .net lub typowe wymagania środowiska uruchomieniowego języka, które mogą zezwolić na uruchamianie na platformach niższego poziomu przez w tym pakiety NuGet lub innych bibliotek.
  
 Niezależnie od tego, który **/langversion** ustawienie używanie użyjesz bieżącą wersję środowiska CLR do utworzenia .exe lub .dll. Jedynym wyjątkiem jest przyjaznych zestawów i [/moduleassemblyname (opcja kompilatora C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), która pracy w obszarze **/langversion:ISO-1**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **wersji językowej** właściwości.  
  
 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
    
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a>Specyfikacja języka C#
 [Dokumentacja specyfikacja języka C#](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation  
 C# 1.0/1.1 [23270:2003 ISO/IEC](https://www.iso.org/standard/36768.html) technologii informatycznych — specyfikacja języka C#: ISO katalogu  
 C# 2.0 [23270:2006 ISO/IEC](https://www.iso.org/standard/42926.html) technologii informatycznych — specyfikacja języka C#: ISO katalogu  
 C# 2.0 [c042926_ISO_IEC_23270_2006 zip (E)](http://go.microsoft.com/fwlink/?LinkId=144406) 23270:2006 ISO/IEC w formacie PDF: dostępne standardów za darmo ISO  
 C# 3.0 [Specification.doc języka CSharp](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# wersja specyfikacji języka 3.0: Microsoft Corporation  
 C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) ECMA 334 4. w wersji Standard    
 C# w wersji 5.0 [Specification.docx języka CSharp](https://www.microsoft.com/download/details.aspx?id=7029) C# wersja specyfikacji języka 5.0: Microsoft Corporation  
 C# w wersji 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# wersja specyfikacji języka 6 - nieoficjalny projekt: .NET Foundation  
 C# (nie jest aktualnie dostępna) 7.0  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Wersja minimalna kompilatora potrzebnych do obsługi wszystkich funkcji języka   
[↩](#TDefault)<a name="FDefault">domyślne</a>, <a name="FISO1">ISO1</a>: .net programu Microsoft Visual Studio/Build Tools 2002 lub powiązane .net Framework 1.0 kompilatora     
[↩](#TISO2)<a name="FISO2">ISO2</a>: program Microsoft Visual Studio/kompilacji narzędzia 2005 lub powiązane .net Framework 2.0 kompilatora    
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/kompilacji narzędzia 2008 lub powiązane .net Framework 3.5 kompilatora    
[↩](#TCS4)<a name="FCS4">CS4</a>: programu Microsoft Visual Studio/kompilacji narzędzia 2010 lub powiązane .net Framework 4.0 kompilatora    
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/kompilacji narzędzia 2012 lub powiązane .net Framework 4.5 kompilatora    
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">najnowsze</a>: 2017 narzędzi Microsoft Visual Studio/kompilacji   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
