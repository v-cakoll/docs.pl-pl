---
title: Eksportowanie do platformy .NET Core - przy użyciu pakietu zgodności systemu Windows
description: Więcej informacji na temat pakietu zgodności systemu Windows i jak można go używać do portu istniejącego kodu .NET Framework do platformy .NET Core
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 4ef7d9c847d48ae7bbb2d553b1c05cb90a1c5a7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-the-windows-compatibility-pack"></a>Przy użyciu pakietu zgodności systemu Windows

Jednym z najbardziej typowe problemy, które deweloperzy stają przed podczas przenoszenia ich istniejącego kodu do platformy .NET Core jest ich są zależne od interfejsów API i technologie, które istnieją tylko w programie .NET Framework. *Pakiet zgodności systemu Windows* jest o wiele z tych technologii zapewnienie, że tworzenie aplikacji platformy .NET Core, a także bibliotek .NET Standard staje się bardziej mogą zostać wykorzystane do istniejącego kodu.

Ten pakiet jest logiczną [rozszerzenia .NET 2.0 standardowe](../whats-new/index.md#api-changes-and-library-support) czy znacznie zwiększa zestawu interfejsów API i istniejący kod kompiluje z prawie żadnych modyfikacji. Aby zapewnić promise .NET Standard, ale ("jest zestaw interfejsów API, które zapewniają wszystkich implementacji .NET"), to nie zostały uwzględnione technologie, które nie może działać na wszystkich platformach, takich jak rejestru Instrumentacji zarządzania Windows (WMI) lub emisja odbicia Interfejsy API.

*Pakiet zgodności systemu Windows* znajduje się na szczycie .NET Standard i zapewnia dostęp do technologii, które są tylko systemu Windows. Jest to szczególnie przydatne dla użytkowników, którzy mają zostać przeniesione do platformy .NET Core, ale planu, aby zachować zgodność z systemem Windows jako pierwszy krok. W tym scenariuszu nie będzie mógł korzystać z technologii systemu Windows jest tylko próg migracji wykluczający się o zerowej architektury korzyści.

## <a name="package-contents"></a>Zawartość pakietu

*Pakiet zgodności systemu Windows* zostaną przekazane za pośrednictwem pakietu NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i może być przywoływany w projektach przeznaczonych dla platformy .NET Core lub .NET Standard.

Zapewnia około 20 000 interfejsów API, łącznie z interfejsów API systemu Windows, jak również między platformami z następujących obszarów technologii:

* Strony kodowe
* CodeDom
* Konfiguracja
* Usługi katalogowe
* Rysowanie
* ODBC
* Uprawnienia
* Porty
* Listy kontroli dostępu do systemu Windows (ACL)
* Windows Communication Foundation (WCF)
* Kryptografia systemu Windows
* Dziennik zdarzeń systemu Windows
* Instrumentacja zarządzania Windows (WMI)
* Liczniki wydajności systemu Windows
* Rejestr systemu Windows
* Buforowanie środowiska wykonawczego systemu Windows
* Usługi systemu Windows

Aby uzyskać więcej informacji, zobacz [specyfikacji pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Wprowadzenie

1. Przed eksportowanie, upewnij się, że Przyjrzyjmy się [eksportowanie procesu](index.md).

2. Podczas przenoszenia istniejącego kodu platformy .NET Core lub .NET Standard, zainstaluj pakiet NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Jeśli chcesz zachować zgodność z systemem Windows, wszystko jest gotowe.

4. Uruchamianie aplikacji .NET Core i biblioteki .NET Standard w systemie Linux lub macOS, należy użyć [analizator interfejsu API](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) można znaleźć użycia interfejsów API, które nie będą działać na różnych platformach.

5. Usuń użycia tych interfejsów API, Zamień alternatyw i platform lub zabezpieczenia je za pomocą wyboru platform, takich jak:

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

Dla demonstrację, zapoznaj się z [wideo z witryny Channel 9 pakietu zgodności systemu Windows](https://channel9.msdn.com/Events/Connect/2017/T123).

