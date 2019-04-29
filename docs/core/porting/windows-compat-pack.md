---
title: Użyj pakietu Windows zgodności do portu kodu platformy .NET Core
description: Więcej informacji na temat pakietu Windows zgodności i jak można jej używać do portu istniejącego kodu .NET Framework i .NET Core
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: c4fd888e0fbce86ab317f18fd77374af5d3ca244
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663105"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Użyj pakietu Windows zgodności do portu kodu platformy .NET Core

Niektóre z najczęściej spotykanych problemów podczas przenosisz istniejący kod do programu .NET Core są zależności o interfejsach API i technologii, które znajdują się tylko w programie .NET Framework. *Systemie Windows Compatibility Pack* zapewnie wiele z tych technologii, więc jest znacznie łatwiejsze tworzenie aplikacji .NET Core i biblioteki .NET Standard.

Ten pakiet jest wartość logiczna [rozszerzenia .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , znacznie zwiększa zestawu interfejsów API i istniejący kod kompiluje bez niemal żadnych modyfikacji. Aby zachować obietnicy .NET Standard, ale ("to zbiór interfejsów API, które zapewniają wszystkich implementacji .NET"), to nie zostały uwzględnione technologie, które nie może działać na wszystkich platformach, takich jak rejestru, Instrumentacji zarządzania Windows (WMI) lub emisji odbicia Interfejsy API.

*Systemie Windows Compatibility Pack* znajduje się na szczycie .NET Standard i zapewnia dostęp do technologii, które są tylko Windows. Jest to szczególnie przydatne w przypadku klientów, które chcesz przenieść do platformy .NET Core, ale plan pozostanie w Windows jako pierwszy krok. W tym scenariuszu nie będzie mógł korzystać z technologii Windows tylko jest tylko próg migracji wykluczający się zero zalety architektury.

## <a name="package-contents"></a>Zawartość pakietu

*Systemie Windows Compatibility Pack* znajduje się za pośrednictwem pakietu NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i mogą być przywoływane z projektów przeznaczonych dla platformy .NET Core lub .NET Standard.

Zapewnia około 20 000 interfejsów API, tylko do Windows, a także dla wielu platform interfejsów API z następujących obszarów technologii w tym:

* Strony kodowe
* CodeDom
* Konfiguracja
* Usługi katalogowe
* Rysowanie
* ODBC
* Uprawnienia
* Porty
* Listy kontroli dostępu systemu Windows (ACL)
* Windows Communication Foundation (WCF)
* Windows Cryptography
* Windows w dzienniku zdarzeń
* Instrumentacja zarządzania Windows (WMI)
* Liczniki wydajności Windows
* Windows Registry
* Buforowanie środowiska uruchomieniowego Windows
* Usługi systemu Windows

Aby uzyskać więcej informacji, zobacz [specyfikacji pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Wprowadzenie

1. Przed przenoszenie, upewnij się, że Przyjrzyj się [proces przenoszenia](index.md).

2. Jeśli przenosisz istniejący kod platformy .NET Core lub .NET Standard, należy zainstalować pakiet NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Jeśli chcesz pozostać na Windows, wszystko jest gotowe.

4. Uruchamianie aplikacji .NET Core i biblioteki .NET Standard w systemie Linux lub macOS, należy użyć [analizatora API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) można znaleźć użycia interfejsów API, które nie będą działać na różnych platformach.

5. Usuń użycia tych interfejsów API, zastąp je alternatywy dla wielu platform lub je przed nieprzewidzianymi je za pomocą wyboru platform, takich jak:

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

Pokaz, zapoznaj się z [wideo Channel 9 z pakietu zgodności Windows](https://channel9.msdn.com/Events/Connect/2017/T123).
