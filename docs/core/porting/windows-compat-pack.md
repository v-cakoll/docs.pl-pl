---
title: Używanie pakietu zgodności systemu Windows do przenoszenia kodu do programu .NET Core
description: Dowiedz się więcej o pakiecie zgodności systemu Windows i jak można go używać do przenoszenia istniejącego kodu .NET Framework do programu .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 65530987a3cded941b6a292118ed9bfdb6f5b86c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715468"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Używanie pakietu zgodności systemu Windows do przenoszenia kodu do programu .NET Core

Niektóre z najczęstszych problemów występujących podczas przenoszenia istniejącego kodu do programu .NET Core są zależnościami od interfejsów API i technologii, które są dostępne tylko w .NET Framework. *Pakiet zgodności systemu Windows* zawiera wiele z tych technologii, więc znacznie łatwiej jest tworzyć aplikacje .NET Core i biblioteki .NET Standard.

Ten pakiet jest logicznym [rozszerzeniem .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , które znacząco zwiększają zestaw interfejsów API i istniejące skompilowane kod przy niemal nie modyfikowaniu. Aby zachować obietnicę .NET Standard ("jest zestaw interfejsów API, które udostępnia wszystkie implementacje platformy .NET"), pakiet nie obejmuje technologii, które nie mogą współpracować ze wszystkimi platformami, takimi jak rejestr, Instrumentacja zarządzania Windows (WMI) lub emisja odbicia Programowania.

Pakiet zgodności systemu Windows znajduje się w oparciu o .NET Standard i zapewnia dostęp do technologii, które są przeznaczone tylko dla systemu Windows. Jest to szczególnie przydatne w przypadku klientów, którzy chcą przenieść się na platformę .NET Core, ale planujesz pozostawać w systemie Windows jako pierwszy krok. W tym scenariuszu nie można używać technologii obsługujących tylko system Windows tylko w przypadku, gdy nie ma żadnych korzyści związanych z architekturą.

## <a name="package-contents"></a>Zawartość pakietu

Pakiet zgodności systemu Windows jest dostarczany za pośrednictwem [pakietu NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i można się do niego odwoływać z projektów przeznaczonych dla platformy .NET Core lub .NET Standard.

Zawiera on około 20 000 interfejsów API, w tym Windows-only i międzyplatformowych interfejsów API, z następujących obszarów technologii:

- Strony kodowe
- CodeDom
- Konfiguracja
- Usługi katalogowe
- Rysowanie
- ODBC
- Uprawnienia
- Porty
- Listy Access Control systemu Windows (ACL)
- Windows Communication Foundation (WCF)
- Kryptografia systemu Windows
- Dziennik zdarzeń systemu Windows
- Windows Management Instrumentation (WMI)
- Liczniki wydajności systemu Windows
- Rejestr systemu Windows
- Buforowanie środowisko wykonawcze systemu Windows
- Usługi systemu Windows

Aby uzyskać więcej informacji, zobacz [specyfikację pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Wprowadzenie

1. Przed przystąpieniem do przenoszenia upewnij się, że Przyjrzyj się [procesowi przenoszenia](index.md).

2. Podczas przenoszenia istniejącego kodu do programu .NET Core lub .NET Standard zainstaluj [pakiet NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Jeśli chcesz pozostać w systemie Windows, wszystko jest gotowe.

3. Jeśli chcesz uruchomić aplikację .NET Core lub bibliotekę .NET Standard w systemie Linux lub macOS, użyj [analizatora interfejsów API](../../standard/analyzers/api-analyzer.md) , aby znaleźć użycie interfejsów API, które nie będą działać na różnych platformach.

4. Usuń użycie tych interfejsów API, zastąp je niektórymi alternatywami dla wielu platform lub zapoznaj się z nimi przy użyciu sprawdzenia platformy, takiego jak:

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

Aby zapoznać się z pokazem, zapoznaj się z [tematem wideo Channel 9 pakietu zgodności systemu Windows](https://channel9.msdn.com/Events/Connect/2017/T123).
