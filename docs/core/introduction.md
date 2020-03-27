---
title: Wprowadzenie i omówienie .NET Core
description: .NET Core to modułowa, wydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351702"
---
# <a name="introduction-to-net-core"></a>Wprowadzenie do platformy .NET Core

[.NET Core](about.md) jest platformą programową [typu open source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)ogólnego przeznaczenia prowadzoną przez firmę Microsoft i społeczność .NET w [witrynie GitHub.](https://github.com/dotnet/core) Jest wieloplatformowy (obsługujący systemy Windows, macOS i Linux) i może być używany do tworzenia urządzeń, chmury i aplikacji IoT.

## <a name="download-net-core"></a>Pobierz .NET Core

Pobierz [podstawowy sdk .NET,](https://dotnet.microsoft.com/download) aby wypróbować program .NET Core na komputerze z systemem Windows, macOS lub Linux. Jeśli wolisz używać kontenerów platformy Docker, odwiedź [centrum platformy .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

## <a name="net-core-31"></a>.NET Rdzeń 3.1

Najnowsza wersja to .NET Core 3.1. 3.1 zawiera drobne ulepszenia w stosunku do .NET Core 3.0, jednak .NET Core 3.1 jest [długoterminową wersją obsługiwaną.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) Aby uzyskać więcej informacji na temat wersji .NET Core 3.1, zobacz [Co nowego w .NET Core 3.1](./whats-new/dotnet-core-3-1.md).

Jeśli szukasz innej wersji programu .NET Core, wszystkie wersje są dostępne w [plikach do pobrania .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="create-your-first-application"></a>Tworzenie pierwszej aplikacji

Po zainstalowaniu zestawu .NET Core SDK otwórz wiersz polecenia. Wprowadź następujące `dotnet` polecenia, aby utworzyć i uruchomić aplikację języka C#:

```dotnetcli
dotnet new console
dotnet run
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```output
Hello World!
```

## <a name="support"></a>Pomoc techniczna

Program .NET Core jest [obsługiwany przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy) w systemach Windows, macOS i Linux. Jest aktualizowany pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.

Dystrybucje binarne .NET Core są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i obsługiwane tak jak każdy produkt firmy Microsoft.

[Red Hat obsługuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat buduje .NET Core ze źródła i udostępnia go w [red hat software collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft współpracują, aby zapewnić, że program .NET Core działa dobrze na RHEL.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczki .NET Core](tutorials/index.md)

> [!div class="nextstepaction"]
> [Wypróbuj program .NET Core w przeglądarce](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
