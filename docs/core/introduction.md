---
title: Wprowadzenie i omówienie .NET Core
description: .NET Core to modułowa, wydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f99b446bbd38b2b814c13afa13ab34cd5c9aa086
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645525"
---
# <a name="introduction-to-net-core"></a>Wprowadzenie do platformy .NET Core

[.NET Core](about.md) jest platformą programową [typu open source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)i ogólnego przeznaczenia. Aplikacje .NET Core dla systemów Windows, macOS i Linux można tworzyć dla procesorów x64, x86, ARM32 i ARM64 w wielu językach programowania. Struktury i interfejsy API są dostarczane dla [chmury,](/aspnet/core/) [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [interfejsu użytkownika klienta](../desktop-wpf/overview/index.md)i uczenia [maszynowego.](/dotnet/machine-learning/)

[Pobierz podstawowy sdk .NET,](https://dotnet.microsoft.com/download) aby wypróbować program .NET Core na swoim komputerze. Najnowsza wersja to [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

## <a name="download-net-core"></a>Pobierz .NET Core

Program .NET Core można uzyskać w następujący sposób:

* [Instalatorzy systemów Windows i macOS](https://dotnet.microsoft.com/download)
* [Pakiety Linuksa](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Kontenerów Docker](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Zamki błyskawiczne i kulki smoły](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Instalowanie skryptów](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Informacje o wersji](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>Tworzenie pierwszej aplikacji

Po zainstalowaniu zestawu .NET Core SDK otwórz wiersz polecenia. Aby utworzyć i uruchomić aplikację, użyj następujących poleceń:

```dotnetcli
dotnet new console
dotnet run
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```output
Hello World!
```

## <a name="contribute"></a>Współtworzenie

.NET Core jest otwartą platformą. Każdy jest mile widziany.

* Problemy z produktem i pytania dotyczące produktów w [witrynie Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).
* Wkład produktu powinien być dokonywany w jednym z repozytoriów projektu, takich jak [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk,](https://github.com/dotnet/sdk) [dotnet/rosyln](https://github.com/dotnet/roslyn)lub [aspnetcore](https://github.com/dotnet/aspnetcore). Aby uzyskać więcej informacji, zobacz [.NET Core repo](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Pomoc techniczna

.NET Core jest obsługiwany przez firmę Microsoft w systemach Windows, macOS i Linux oraz przez Red Hat na Red Hat Enterprise Linux.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczki .NET Core](tutorials/index.md)

> [!div class="nextstepaction"]
> [Wypróbuj program .NET Core w przeglądarce](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
