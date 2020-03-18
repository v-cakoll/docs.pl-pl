---
title: -langversion (Opcje kompilatora C#)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 007b10f6f27233c43caad4c1910e3d1158682950
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920364"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (Opcje kompilatora C#)

Powoduje, że kompilator akceptuje tylko składnię, która jest uwzględniona w wybranej specyfikacji języka Języka C#.

## <a name="syntax"></a>Składnia

```console
-langversion:option
```

## <a name="arguments"></a>Argumenty

`option`

Następujące wartości są prawidłowe:

|Opcja|Znaczenie|
|------------|-------------|
|podgląd|Kompilator akceptuje wszystkie prawidłowe składni języka z najnowszej wersji zapoznawczej, które może obsługiwać.|
|najnowsza|Kompilator akceptuje wszystkie prawidłowe składni języka z najnowszej wersji (w tym wersje pomocnicze), które może obsługiwać.|
|najnowszeMajor|Kompilator akceptuje wszystkie prawidłowe składni języka z najnowszej wersji głównej, które mogą obsługiwać.|
|8.0|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 8.0 lub niższym.|
|7.3|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.3 lub niższym.|
|7.2|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.2 lub niższym.|
|7.1|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.1 lub niższym.|
|7|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.0 lub niższym.|
|6|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 6.0 lub niższym.|
|5|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 5.0 lub niższej.|
|4|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 4.0 lub niższym.|
|3|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 3.0 lub niższym.|
|Iso-2|Kompilator akceptuje tylko składnię, która jest uwzględniona w ISO/IEC 23270:2006 C# (2.0).|
|Iso-1|Kompilator akceptuje tylko składnię, która jest uwzględniona w ISO/IEC 23270:2003 C# (1.0/1.2).|

Domyślna wersja językowa zależy od struktury docelowej dla aplikacji i zainstalowanej wersji sdk lub visual studio. Reguły te są zdefiniowane w [konfigurowaniu wersji językowej.](../configure-language-version.md#defaults)

## <a name="remarks"></a>Uwagi

Metadane, do których odwołuje się aplikacja C# nie podlega opcji kompilatora **-langversion.**

Ponieważ każda wersja kompilatora C# zawiera rozszerzenia do specyfikacji języka, **-langversion** nie daje równoważne funkcje starszej wersji kompilatora.

Ponadto podczas gdy aktualizacje wersji Języka C# zazwyczaj pokrywają się z głównych wersji .NET Framework, nowa składnia i funkcje nie muszą być powiązane z tej określonej wersji struktury. Podczas gdy nowe funkcje zdecydowanie wymagają nowej aktualizacji kompilatora, który jest również zwolniony wraz z wersją C#, każda konkretna funkcja ma swój własny minimalny interfejs API .NET lub wymagania dotyczące języka wspólnego, które mogą pozwolić na uruchamianie na downlevel frameworków, dołączając pakiety NuGet lub inne biblioteki.

Niezależnie od tego, którego ustawienia **-langversion** używasz, użyj bieżącej wersji wspólnego języka, aby utworzyć plik .exe lub .dll. Jednym z wyjątków są zestawy znajomych i [-moduleassemblyname (C# Compiler Option),](./moduleassemblyname-compiler-option.md)które działają pod **-langversion:ISO-1**.

Aby uzyskać inne sposoby określania wersji językowej Języka C#, zobacz [Wybierz c# language version](../configure-language-version.md) artykułu.

Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>opcji kompilatora, zobacz .

## <a name="c-language-specification"></a>specyfikacja języka C#

|Wersja|Link|Opis|
|-------|----|-----------|
|C# 7.0 i nowszych||nie jest obecnie dostępna|
|C# 6.0|[Link](/dotnet/csharp/language-reference/language-specification/introduction)|Specyfikacja językowa języka języka Języka C# wersja 6 — nieoficjalna wersja robocza: .NET Foundation|
|C# 5.0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standardowa edycja ECMA-334 5th Edition|
|C# 3.0|[Pobierz DOC](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# Language Specification Version 3.0: Microsoft Corporation|
|C# 2.0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standardowa ecma-334 4 edycja|
|C# 1.2|[Pobierz DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C# Language Specification Version 1.2: Microsoft Corporation|
|C# 1.0|[Pobierz DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C# Language Specification Version 1.0: Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Minimalna wersja SDK potrzebna do obsługi wszystkich funkcji językowych

W poniższej tabeli wymieniono minimalne wersje sdk z kompilatorem C# obsługującym odpowiednią wersję językową:

|Wersja języka C#|Minimalna wersja SDK|
|----------|-------------------|
|C# 8.0| Microsoft Visual Studio/Build Tools 2019, wersja 16.3 lub SDK programu .NET Core 3.0 |
|C# 7.3| Microsoft Visual Studio/Build Tools 2017, wersja 15.7 |
|C# 7.2| Microsoft Visual Studio/Build Tools 2017, wersja 15.5 |
|C# 7.1| Microsoft Visual Studio/Build Tools 2017, wersja 15.3 |
|C# 7.0| Narzędzia programu Microsoft Visual Studio/Build 2017 |
|C# 6| Microsoft Visual Studio/Build Tools 2015 |
|C# 5| Microsoft Visual Studio/Build Tools 2012 lub w pakiecie .NET Framework 4.5 kompilator |
|Język C# 4| Microsoft Visual Studio/Build Tools 2010 lub kompilator programu .NET Framework 4.0 |
|Numer 1| Microsoft Visual Studio/Build Tools 2008 lub kompilator programu .NET Framework 3.5 |
|Numer C# 2| Microsoft Visual Studio/Build Tools 2005 lub w pakiecie .NET Framework 2.0 kompilator |
|C# 1,0/1,2 | Program Microsoft Visual Studio/Build Tools .NET 2002 lub kompilator programu .NET Framework 1.0 |

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
