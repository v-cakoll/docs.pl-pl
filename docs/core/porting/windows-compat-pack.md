---
title: Użyj pakietu zgodności systemu Windows, aby przenieść kod do programu .NET Core
description: Dowiedz się więcej o pakiecie zgodności systemu Windows i o tym, jak można go używać do przenoszenia istniejącego kodu programu .NET Framework do platformy .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 166259ca37a2005d67f6c545e4843a940f05fb71
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228636"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Użyj pakietu zgodności systemu Windows, aby przenieść kod do programu .NET Core

Niektóre z najczęstszych problemów znalezionych podczas przenoszenia istniejącego kodu do platformy .NET Core to zależności od interfejsów API i technologii, które znajdują się tylko w programie .NET Framework. *Pakiet zgodności systemu Windows* zawiera wiele z tych technologii, dzięki czemu tworzenie aplikacji .NET Core i bibliotek .NET Standard jest znacznie łatwiejsze.

Pakiet zgodności jest logicznym [rozszerzeniem programu .NET Standard 2.0,](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) które znacznie zwiększa zestaw interfejsu API. Istniejący kod kompiluje się prawie bez żadnych modyfikacji. Aby dotrzymać obietnicy "zestaw interfejsów API, które zapewniają wszystkie implementacje platformy .NET", program .NET Standard nie zawiera technologii, które nie mogą działać na wszystkich platformach, takich jak rejestr, instrumentacja zarządzania windowsem (WMI) lub odbicie emitują interfejsy API. Pakiet zgodności systemu Windows znajduje się na szczycie programu .NET Standard i zapewnia dostęp do tych technologii dostępnych tylko dla systemu Windows. Jest to szczególnie przydatne dla klientów, którzy chcą przejść do platformy .NET Core, ale planują pozostać w systemie Windows, przynajmniej w pierwszym kroku. W tym scenariuszu możliwość korzystania z technologii tylko dla systemu Windows usuwa przeszkodę migracji.

## <a name="package-contents"></a>Zawartość pakietu

Pakiet zgodności systemu Windows jest dostarczany za pośrednictwem [pakietu Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i można do niego odwoływać się z projektów docelowych .NET Core lub .NET Standard.

Udostępnia około 20 000 interfejsów API, w tym interfejsy API tylko dla systemu Windows, a także interfejsy API z następujących obszarów technologii:

- Strony kodowe
- Codedom
- Konfigurowanie
- Usługi katalogowe
- Rysowanie
- ODBC
- Uprawnienia
- Porty
- Listy kontroli dostępu do systemu Windows (ACL)
- Windows Communication Foundation (WCF)
- Kryptografia systemu Windows
- Dziennik zdarzeń systemu Windows
- Instrumentacja zarządzania Windows (WMI)
- Liczniki wydajności systemu Windows
- Rejestr systemu Windows
- Buforowanie środowiska wykonawczego systemu Windows
- Usługi systemu Windows

Aby uzyskać więcej informacji, zobacz [specyfikację pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md).

## <a name="get-started"></a>Wprowadzenie

1. Przed przeniesieniem należy zapoznać się z [procesem przenoszenia](index.md).

2. Podczas przenoszenia istniejącego kodu do platformy .NET Core lub .NET Standard należy zainstalować [pakiet NuGet firmy Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Jeśli chcesz pozostać w systemie Windows, wszystko jest ustawione.

3. Jeśli chcesz uruchomić aplikację .NET Core lub bibliotekę .NET Standard w systemie Linux lub macOS, użyj [analizatora interfejsu API,](../../standard/analyzers/api-analyzer.md) aby znaleźć użycie interfejsów API, które nie będą działać na różnych platformach.

4. Usuń użycie tych interfejsów API, zastąp je alternatywami między platformami lub strzeż ich za pomocą kontroli platformy, takiej jak:

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

Aby uzyskać prezentację, zapoznaj się [z klipem wideo Channel 9 pakietu zgodności systemu Windows](https://channel9.msdn.com/Events/Connect/2017/T123).
