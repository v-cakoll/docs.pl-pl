---
title: -langversion (C# opcje kompilatora)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 5675099f66ec99c652ef95a5328f31c360e2dc59
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602830"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# opcje kompilatora)

Powoduje, że kompilator akceptuje tylko składnię, która jest zawarta w wybranej C# specyfikacji języka.  
  
## <a name="syntax"></a>Składnia  

```console
-langversion:option  
```

## <a name="arguments"></a>Argumenty

 `option`  
 Następujące wartości są prawidłowe:  
  
|Opcja|Znaczenie|  
|------------|-------------|  
|wersja zapoznawcza|Kompilator akceptuje wszystkie prawidłowe składnie języka od najnowszej wersji zapoznawczej, którą może obsłużyć.|
|najnowsza|Kompilator akceptuje całą poprawną składnię języka od najnowszej wersji (w tym wydań pomocniczych), którą może obsłużyć.|
|latestMajor|Kompilator akceptuje wszystkie prawidłowe składnie języka od najnowszej wersji głównej, którą może obsłużyć.|
|8.0|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 8,0 lub niższej. <sup id="TCS80">[CS80](#FCS80)</sup>|
|7.3|Kompilator akceptuje tylko składnię zawartą w C# 7,3 lub niższej <sup id="TCS73">CS73</sup>|
|7.2|Kompilator akceptuje tylko składnię zawartą w C# 7,2 lub niższej <sup id="TCS72">CS72</sup>|
|7.1|Kompilator akceptuje tylko składnię zawartą w C# 7,1 lub niższej <sup id="TCS71">CS71</sup>|
|7|Kompilator akceptuje tylko składnię zawartą w C# 7,0 lub niższej <sup id="TCS7">CS7</sup>|
|6|Kompilator akceptuje tylko składnię zawartą w C# 6,0 lub niższej <sup id="TCS6">CS6</sup>|
|5|Kompilator akceptuje tylko składnię zawartą w C# 5,0 lub niższej <sup id="TCS5">CS5</sup>|
|4|Kompilator akceptuje tylko składnię zawartą w C# 4,0 lub niższej wersji programu <sup id="TCS4">CS4</sup>|
|3|Kompilator akceptuje tylko składnię zawartą w C# 3,0 lub niższej <sup id="TCS3"></sup>|
|ISO-2|Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2006 C# (2,0) <sup id="TISO2">ISO2</sup>|
|ISO-1|Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2003 C# (1.0/1.2) <sup id="TISO1">ISO1</sup>|  

## <a name="remarks"></a>Uwagi

 Metadane przywoływane C# przez aplikację nie podlegają opcji kompilatora **langversion** .  
  
 Ponieważ każda wersja C# kompilatora zawiera rozszerzenia specyfikacji języka, **-langversion** nie zapewnia równoważnej funkcjonalności starszej wersji kompilatora.  

 Ponadto, chociaż C# aktualizacje wersji zwykle pokrywają się z głównymi wersjami .NET Framework, Nowa składnia i funkcje nie muszą być powiązane z tą określoną wersją platformy. Nowe funkcje w nieskończoność wymagają nowej aktualizacji kompilatora, która jest również wydawana C# wraz z poprawką, każda konkretna funkcja ma własne wymagania dotyczące minimalnych interfejsów API platformy .NET lub środowiska uruchomieniowego języka wspólnego, które mogą umożliwić uruchomienie go na platformach o niższych wartościach przez łącznie z pakietami NuGet lub innymi bibliotekami.
  
 Niezależnie od tego, które ustawienie jest używane, użyjesz bieżącej wersji środowiska uruchomieniowego języka wspólnego, aby utworzyć plik. exe lub. dll. Jedynym wyjątkiem są zestawy zaprzyjaźnione i [-moduleassemblyname —C# (opcja kompilatora)](./moduleassemblyname-compiler-option.md), które działają w **langversion: ISO-1**.  

 Aby poznać inne sposoby określania wersji C# językowej, zobacz temat [Wybieranie wersji C# językowej](../configure-language-version.md) .
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>tę opcję kompilatora, zobacz.  

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

### <a name="c-language-specification"></a>Specyfikacja języka C#

|Wersja|Łącze|Opis|
|-------|----|-----------|
|C#7,0 i nowsze||obecnie niedostępne|
|C#6,0|[Link](../language-specification/index.md)|C#Specyfikacja języka w wersji 6 — nieoficjalne wersje robocze: .NET Foundation|
|C#5,0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standardowa ECMA-334, wersja 5|
|C#3,0|[Pobierz dokument](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C#Specyfikacja języka wersja 3,0: Microsoft Corporation|
|C#2,0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standard ECMA-334 czwarta|
|C#1,2|[Pobierz dokument](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C#Specyfikacja języka wersja 1,2: Microsoft Corporation|
|C#1,0|[Pobierz dokument](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C#Specyfikacja języka wersja 1,0: Microsoft Corporation|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Minimalna wersja kompilatora wymagana do obsługi wszystkich funkcji języka

[↩](#TCS80)<a name="FCS80">CS80</a>: Narzędzia Microsoft Visual Studio/Build Tools 2019, wersja 16 lub .NET Core 3,0 SDK  
[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017, wersja 15,7  
[↩](#TCS72) <a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017, wersja 15,5  
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017, wersja 15,3  
[↩](#TCS7) <a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017  
[↩](#TCS6) <a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015  
[↩](#TCS5) <a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 lub z pakietem .NET Framework 4,5  
[↩](#TCS4) <a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 lub z pakietem .NET Framework 4,0  
[↩](#TCS3) <a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 lub z pakietem .NET Framework 3,5  
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 lub z pakietem .NET Framework 2,0  
[↩](#TISO1)<a name="FISO1">ISO1</a>: Narzędzia Microsoft Visual Studio/Build Tools .NET 2002 lub powiązane z pakietem. N Framework 1,0 — kompilator  
