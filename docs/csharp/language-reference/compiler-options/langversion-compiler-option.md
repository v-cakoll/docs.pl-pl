---
title: -langversion (opcje kompilatora C#)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 408b2fb1f19f872db675321601ebc1b0c921044b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802953"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (opcje kompilatora C#)

Powoduje, że kompilator akceptuje tylko składnię, która jest zawarta w wybranej specyfikacji języka C#.

## <a name="syntax"></a>Składnia

```console
-langversion:option
```

## <a name="arguments"></a>Argumenty

`option`

Następujące wartości są prawidłowe:

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

Domyślna wersja języka zależy od platformy docelowej dla aplikacji oraz zainstalowanej wersji zestawu SDK lub programu Visual Studio. Te reguły są zdefiniowane w artykule [Konfigurowanie wersji językowej](../configure-language-version.md#defaults) .

## <a name="remarks"></a>Uwagi

Metadane przywoływane przez aplikację w języku C# nie podlegają opcji kompilatora **langversion** .

Ponieważ każda wersja kompilatora C# zawiera rozszerzenia specyfikacji języka, **— langversion** nie zapewnia równoważnej funkcjonalności starszej wersji kompilatora.

Ponadto, chociaż aktualizacje wersji języka C# zwykle pokrywają się z najważniejszymi wersjami .NET Framework, Nowa składnia i funkcje nie muszą być powiązane z tą określoną wersją platformy. Nowe funkcje w nieskończoność wymagają nowej aktualizacji kompilatora, która jest również wydawana wraz z poprawką w języku C#, każda konkretna funkcja ma własne wymagania dotyczące minimalnych interfejsów API platformy .NET lub środowiska uruchomieniowego języka wspólnego, które mogą zezwalać na uruchamianie jej w ramach struktur niskiego poziomu przez uwzględnienie pakietów NuGet lub innych bibliotek.

Niezależnie od tego, **które ustawienie** jest używane, Użyj bieżącej wersji środowiska uruchomieniowego języka wspólnego, aby utworzyć plik. exe lub. dll. Jedynym wyjątkiem są zestawy zaprzyjaźnione i [-moduleassemblyname — (opcja kompilatora C#)](./moduleassemblyname-compiler-option.md), które działają w obszarze **-langversion: ISO-1**.

Aby poznać inne sposoby określania wersji języka C#, zobacz artykuł [Wybieranie języka c# w wersji](../configure-language-version.md) .

Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A> .

## <a name="c-language-specification"></a>specyfikacja języka C#

| Wersja          | Link                       | Opis                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| C# 7,0 i nowsze |                            | Obecnie niedostępne                                                 |
| C# 6,0           | [Link][csharp-6]           | Specyfikacja języka C# w wersji 6 — nieoficjalne wersje robocze: .NET Foundation |
| C# 5,0           | [Pobierz plik PDF][csharp-5]   | Standardowa ECMA-334, wersja 5                                           |
| C# 3,0           | [Pobierz dokument][csharp-3]   | Specyfikacja języka C# wersja 3,0: Microsoft Corporation            |
| C# 2,0           | [Pobierz plik PDF][csharp-2]   | Standard ECMA-334 czwarta                                           |
| C# 1,2           | [Pobierz dokument][csharp-1.2] | Specyfikacja języka C# wersja 1,2: Microsoft Corporation            |
| C# 1,0           | [Pobierz dokument][csharp-1]   | Specyfikacja języka C# wersja 1,0: Microsoft Corporation            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Minimalna wersja zestawu SDK wymagana do obsługi wszystkich funkcji języka

W poniższej tabeli wymieniono minimalne wersje zestawu SDK z kompilatorem C#, który obsługuje odpowiednią wersję językową:

| Wersja języka C# | Minimalna wersja zestawu SDK                                                                  |
|------------|--------------------------------------------------------------------------------------|
| C# 8.0     | Microsoft Visual Studio/Build Tools 2019, wersja 16,3 lub .NET Core 3,0 SDK         |
| C# 7.3     | Microsoft Visual Studio/Build Tools 2017, wersja 15,7                               |
| C# 7.2     | Microsoft Visual Studio/Build Tools 2017, wersja 15,5                               |
| C# 7.1     | Microsoft Visual Studio/Build Tools 2017, wersja 15,3                               |
| C# 7.0     | Narzędzia Microsoft Visual Studio/Build Tools 2017                                             |
| C# 6       | Narzędzia Microsoft Visual Studio/Build Tools 2015                                             |
| C# 5       | Microsoft Visual Studio/Build Tools 2012 lub z pakietem .NET Framework 4,5      |
| C# 4       | Microsoft Visual Studio/Build Tools 2010 lub z pakietem .NET Framework 4,0      |
| C# 3       | Microsoft Visual Studio/Build Tools 2008 lub z pakietem .NET Framework 3,5      |
| C# 2       | Microsoft Visual Studio/Build Tools 2005 lub z pakietem .NET Framework 2,0      |
| C# 1.0/1.2 | Narzędzia Microsoft Visual Studio/Build Tools .NET 2002 lub w pakiecie .NET Framework 1,0 |

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
