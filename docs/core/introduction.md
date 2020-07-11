---
title: Wprowadzenie do platformy .NET Core i Omówienie
description: .NET Core to modularna, wielowydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o programie .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226585"
---
# <a name="introduction-to-net-core"></a>Wprowadzenie do platformy .NET Core

[.NET Core](about.md) to platforma programistyczna [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT). Możesz tworzyć aplikacje .NET Core dla systemów Windows, macOS i Linux dla procesorów x64, x86, ARM32 i ARM64 przy użyciu wielu języków programowania. Platformy i interfejsy API są udostępniane dla [chmur](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [interfejsu użytkownika klienta](../desktop-wpf/overview/index.md)i [uczenia maszynowego](/dotnet/machine-learning/).

[Pobierz zestaw .NET Core SDK,](https://dotnet.microsoft.com/download) aby wypróbować platformę .NET Core na swojej maszynie. Najnowsza wersja to [.NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

## <a name="download-net-core"></a>Pobierz program .NET Core

Platformę .NET Core można uzyskać w następujący sposób:

* [Instalatory dla systemu Windows i macOS](https://dotnet.microsoft.com/download)
* [Pakiety systemu Linux](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Kontenery platformy Docker](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Zips i tarballs](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Zainstaluj skrypty](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Informacje o wersji](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>Tworzenie pierwszej aplikacji

Po zainstalowaniu zestaw .NET Core SDK Otwórz wiersz polecenia. Użyj następujących poleceń, aby utworzyć i uruchomić aplikację:

```dotnetcli
dotnet new console
dotnet run
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```output
Hello World!
```

## <a name="contribute"></a>Współtworzenie

.NET Core to otwarta platforma. Wszyscy to zapraszamy do wzięcia udziału.

* Problemy związane z produktem i pytania w [społeczności deweloperów](https://developercommunity.visualstudio.com/spaces/61/index.html).
* Udziały produktów należy wprowadzać na jednym z repozytoriów projektu, takich jak [dotnet/Runtime](https://github.com/dotnet/runtime), [dotnet/SDK](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn)lub [aspnetcore](https://github.com/dotnet/aspnetcore). Aby uzyskać więcej informacji, zobacz temat [repozytoria .NET Core](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Pomoc techniczna

Platforma .NET Core jest obsługiwana przez firmę Microsoft w systemach Windows, macOS i Linux oraz w systemie Red Hat na Red Hat Enterprise Linux.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczki dotyczące platformy .NET Core](tutorials/index.md)

> [!div class="nextstepaction"]
> [Wypróbuj platformę .NET Core w przeglądarce](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
