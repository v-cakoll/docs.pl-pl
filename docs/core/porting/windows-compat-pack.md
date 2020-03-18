---
title: Użyj pakietu zgodności systemu Windows do portu kodu do .NET Core
description: Dowiedz się więcej o pakiecie zgodności systemu Windows i o tym, jak można go używać do przenoszenia istniejącego kodu .NET Framework do .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733613"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Użyj pakietu zgodności systemu Windows do portu kodu do .NET Core

Niektóre z najczęstszych problemów znalezionych podczas przenoszenia istniejącego kodu do .NET Core są zależności od interfejsów API i technologii, które znajdują się tylko w .NET Framework. *Pakiet zgodności systemu Windows* zawiera wiele z tych technologii, dlatego znacznie łatwiej jest tworzyć aplikacje .NET Core i biblioteki .NET Standard.

Pakiet zgodności jest logicznym [rozszerzeniem .NET Standard 2.0,](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) które znacznie zwiększa zestaw interfejsu API. Istniejący kod kompiluje się prawie bez żadnych modyfikacji. Aby dotrzymać obietnicy "zestawu interfejsów API, które zapewniają wszystkie implementacje .NET", .NET Standard nie zawiera technologii, które nie mogą działać na wszystkich platformach, takich jak rejestr, Instrumentacja zarządzania Windows (WMI) lub odbicie emitują interfejsy API. Pakiet zgodności systemu Windows znajduje się na platformie .NET Standard i zapewnia dostęp do tych technologii tylko dla systemu Windows. Jest to szczególnie przydatne dla klientów, którzy chcą przenieść się do .NET Core, ale planują pozostać w systemie Windows, przynajmniej w pierwszym kroku. W tym scenariuszu możliwość korzystania z technologii tylko systemu Windows usuwa przeszkodę migracji.

## <a name="package-contents"></a>Zawartość pakietu

Pakiet zgodności systemu Windows jest dostarczany za pośrednictwem [pakietu Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i można się do niego odwoływać z projektów docelowych .NET Core lub .NET Standard.

Zapewnia około 20 000 interfejsów API, w tym interfejsy API tylko dla systemu Windows, a także międzyplatformowe interfejsy API z następujących obszarów technologicznych:

- Strony kodowe
- Codedom
- Konfigurowanie
- Usługi katalogowe
- Rysowanie
- ODBC
- Uprawnienia
- Porty
- Listy kontroli dostępu systemu Windows (ACL)
- Windows Communication Foundation (WCF)
- Kryptografia systemu Windows
- Dziennik zdarzeń systemu Windows
- Instrumentacja zarządzania Windows (WMI)
- Liczniki wydajności systemu Windows
- Rejestr systemu Windows
- Buforowanie środowiska uruchomieniowe systemu Windows
- Usługi systemu Windows

Aby uzyskać więcej informacji, zobacz [specyfikację pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Rozpoczęcie pracy

1. Przed przeniesieniem należy zapoznać się z [procesem przenoszenia](index.md).

2. Podczas przenoszenia istniejącego kodu do .NET Core lub .NET Standard zainstaluj [pakiet Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Jeśli chcesz pozostać w systemie Windows, wszystko jest ustawione.

3. Jeśli chcesz uruchomić aplikację .NET Core lub bibliotekę .NET Standard w systemie Linux lub macOS, użyj [analizatora interfejsu API,](../../standard/analyzers/api-analyzer.md) aby znaleźć użycie interfejsów API, które nie będą działać między platformami.

4. Usuń użycie tych interfejsów API, zastąp je alternatywami między platformami lub stróżuj je za pomocą sprawdzania platformy, takich jak:

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

Aby zapoznać się z pokazem, obejrzyj [film wideo kanału 9 pakietu zgodności systemu Windows](https://channel9.msdn.com/Events/Connect/2017/T123).
