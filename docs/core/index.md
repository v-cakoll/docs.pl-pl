---
title: Przewodnik platformy .NET Core
description: .NET Core to modułowa, wydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 6d2ce5951fa01ca3945ce0e64aa58fbadc8ab5af
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546552"
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

[.NET Core](about.md) jest platformą programową [typu open source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)ogólnego przeznaczenia prowadzoną przez firmę Microsoft i społeczność .NET w [witrynie GitHub.](https://github.com/dotnet/core) Jest wieloplatformowy (obsługujący systemy Windows, macOS i Linux) i może być używany do tworzenia urządzeń, chmury i aplikacji IoT.

Zobacz [Temat .NET Core,](about.md) aby dowiedzieć się więcej o .NET Core, w tym jego charakterystyki, obsługiwane języki i struktury oraz kluczowe interfejsy API.

Zapoznaj się z [samouczkami .NET Core,](tutorials/index.md) aby dowiedzieć się, jak utworzyć prostą aplikację .NET Core. Uruchomienie pierwszej aplikacji zajmuje tylko kilka minut. Jeśli chcesz wypróbować .NET Core w przeglądarce, spójrz na [numery w języku C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczka online.

## <a name="download-net-core"></a>Pobierz .NET Core

Pobierz [podstawowy sdk .NET,](https://dotnet.microsoft.com/download) aby wypróbować program .NET Core na komputerze z systemem Windows, macOS lub Linux. A jeśli wolisz używać kontenerów platformy Docker, odwiedź [centrum docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).

Wszystkie wersje .NET Core są dostępne w [.NET Core Downloads,](https://dotnet.microsoft.com/download/dotnet-core) jeśli szukasz innej wersji .NET Core.

## <a name="net-core-31"></a>.NET Rdzeń 3.1

Najnowsza wersja to .NET Core 3.1. 3.1 zawiera drobne ulepszenia w stosunku do .NET Core 3.0, jednak .NET Core 3.1 jest [długoterminową wersją obsługiwaną.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) Aby uzyskać więcej informacji na temat wersji .NET Core 3.1, zobacz [Co nowego w .NET Core 3.1](./whats-new/dotnet-core-3-1.md).

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

Program .NET Core jest [obsługiwany przez](https://dotnet.microsoft.com/platform/support/policy)firmę Microsoft , w systemach Windows, macOS i Linux. Jest aktualizowany pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.

Dystrybucje binarne .NET Core są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i obsługiwane tak jak każdy produkt firmy Microsoft.

[Red Hat obsługuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat buduje .NET Core ze źródła i udostępnia go w [red hat software collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft współpracują, aby zapewnić, że program .NET Core działa dobrze na RHEL.
