---
title: -langversion (C# opcje kompilatora)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 81cf336f94815dd3f2c88995eb34ae03b8220097
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179921"
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
|8.0|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 8,0 lub niższej.|
|7.3|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,3 lub niższej.|
|7.2|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,2 lub niższej.|
|7.1|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,1 lub niższej.|
|7|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,0 lub niższej.|
|6|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 6,0 lub niższej.|
|5|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 5,0 lub niższej.|
|4|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 4,0 lub niższej.|
|3|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 3,0 lub niższej.|
|ISO-2|Kompilator akceptuje tylko składnię zawartą w normie ISO/ C# IEC 23270:2006 (2,0).|
|ISO-1|Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2003 C# (1.0/1.2).|

Domyślna wersja języka zależy od platformy docelowej dla aplikacji oraz zainstalowanej wersji zestawu SDK lub programu Visual Studio. Te reguły są zdefiniowane w artykule [Konfigurowanie wersji językowej](../configure-language-version.md#defaults) .

## <a name="remarks"></a>Uwagi

Metadane przywoływane C# przez aplikację nie podlegają opcji kompilatora **langversion** .
  
Ponieważ każda wersja C# kompilatora zawiera rozszerzenia specyfikacji języka, **-langversion** nie zapewnia równoważnej funkcjonalności starszej wersji kompilatora.

Ponadto, chociaż C# aktualizacje wersji zwykle pokrywają się z głównymi wersjami .NET Framework, Nowa składnia i funkcje nie muszą być powiązane z tą określoną wersją platformy. Nowe funkcje w nieskończoność wymagają nowej aktualizacji kompilatora, która jest również wydawana C# wraz z poprawką, każda konkretna funkcja ma własne wymagania dotyczące minimalnych interfejsów API platformy .NET lub środowiska uruchomieniowego języka wspólnego, które mogą umożliwić uruchomienie go na platformach o niższych wartościach przez łącznie z pakietami NuGet lub innymi bibliotekami.

Niezależnie od tego, **które ustawienie** jest używane, użyjesz bieżącej wersji środowiska uruchomieniowego języka wspólnego, aby utworzyć plik. exe lub. dll. Jedynym wyjątkiem są zestawy zaprzyjaźnione i [-moduleassemblyname —C# (opcja kompilatora)](./moduleassemblyname-compiler-option.md), które działają w **langversion: ISO-1**.  

Aby poznać inne sposoby określania wersji C# językowej, zobacz artykuł [Wybieranie wersji C# językowej](../configure-language-version.md) .

Aby uzyskać informacje o tym, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.

## <a name="c-language-specification"></a>C#Specyfikacja języka

|Wersja|Link|Opis|
|-------|----|-----------|
|C#7,0 i nowsze||obecnie niedostępne|
|C#6,0|[Link](../language-specification/index.md)|C#Specyfikacja języka w wersji 6 — nieoficjalne wersje robocze: .NET Foundation|
|C#5,0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standardowa ECMA-334, wersja 5|
|C#3,0|[Pobierz dokument](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C#Specyfikacja języka wersja 3,0: Microsoft Corporation|
|C#2,0|[Pobierz plik PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standard ECMA-334 czwarta|
|C#1,2|[Pobierz dokument](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C#Specyfikacja języka wersja 1,2: Microsoft Corporation|
|C#1,0|[Pobierz dokument](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C#Specyfikacja języka wersja 1,0: Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Minimalna wersja zestawu SDK wymagana do obsługi wszystkich funkcji języka

W poniższej tabeli wymieniono minimalne wersje zestawu SDK z C# kompilatorem obsługującym odpowiednią wersję języka:

|C#Wersja|Minimalna wersja zestawu SDK|
|----------|-------------------|
|C#8,0| Microsoft Visual Studio/Build Tools 2019, wersja 16,3 lub .NET Core 3,0 SDK |
|C#7,3| Microsoft Visual Studio/Build Tools 2017, wersja 15,7 |
|C#7,2| Microsoft Visual Studio/Build Tools 2017, wersja 15,5 |
|C#7,1| Microsoft Visual Studio/Build Tools 2017, wersja 15,3 |
|C#7,0| Narzędzia Microsoft Visual Studio/Build Tools 2017 |
|C#ust| Narzędzia Microsoft Visual Studio/Build Tools 2015 |
|C#5000| Microsoft Visual Studio/Build Tools 2012 lub z pakietem .NET Framework 4,5 |
|C#czwart| Microsoft Visual Studio/Build Tools 2010 lub z pakietem .NET Framework 4,0 |
|C#r.3| Microsoft Visual Studio/Build Tools 2008 lub z pakietem .NET Framework 3,5 |
|C#dwóch| Microsoft Visual Studio/Build Tools 2005 lub z pakietem .NET Framework 2,0 |
|C#1.0/1.2 | Narzędzia Microsoft Visual Studio/Build Tools .NET 2002 lub w pakiecie .NET Framework 1,0 |

## <a name="see-also"></a>Zobacz także

- [C#Opcje kompilatora](index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
