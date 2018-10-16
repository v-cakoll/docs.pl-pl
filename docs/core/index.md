---
title: Przewodnik platformy .NET Core
description: Platforma .NET core to moduły, wysokowydajnych implementacji .NET do tworzenia aplikacji Windows, Linux i Mac. Dowiedz się więcej na temat platformy .NET Core, aby rozpocząć pracę.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 692d49cc940925f629e55cf5cc103522bd3cbb38
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348983"
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

[.NET core](about.md) jest [typu open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) platforma deweloperska ogólnego przeznaczenia, obsługiwane przez firmę Microsoft i społeczności platformy .NET w [GitHub](https://github.com/dotnet/core). Jest dla wielu platform, obsługi Windows, macOS i Linux i mogą być używane w urządzeń, chmury i aplikacji IoT.

Zobacz [platformy .NET Core](about.md) Aby dowiedzieć się więcej na temat platformy .NET Core, w tym właściwości, języków i struktur i klucza API.

Zapoznaj się z [Samouczki programu .NET Core](tutorials/index.md) dowiesz się, jak utworzyć prostą aplikację platformy .NET Core. Trwa tylko kilka minut, aby uzyskać swoją pierwszą aplikację, działanie. Jeśli chcesz wypróbować platformy .NET Core w przeglądarce, Przyjrzyj się [liczb w języku C#](../csharp/quick-starts/numbers-in-csharp.yml) Szybki Start.

## <a name="download-net-core-21"></a>Pobierz program .NET Core 2.1

Pobierz [zestawu SDK programu .NET Core 2.1](https://www.microsoft.com/net/download) próby platformy .NET Core na komputerze Windows, macOS lub Linux. Odwiedź stronę [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) Jeśli wolisz używać kontenerów platformy Docker.

Wszystkie wersje platformy .NET Core są dostępne pod adresem [pobierania programu .NET Core](https://www.microsoft.com/net/download/archives) interesuje Cię bliższa dla innej wersji programu .NET Core.

## <a name="net-core-21"></a>.NET core 2.1

Najnowsza wersja to [platformy .NET Core 2.1](whats-new/dotnet-core-2-1.md). Nowe funkcje obejmują: globalny narzędzi, interfejsów API o wysokiej wydajności (takie jak <xref:System.Span%601?displayProperty=nameWithType>), warstwy kompilacja JIT [kompilacji](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) i [ulepszenia wydajności w czasie wykonywania](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/)oraz obsługę Alpine i ARM32.

## <a name="create-your-first-application"></a>Tworzenie pierwszej aplikacji

Po zainstalowaniu programu .NET Core SDK, otwórz wiersz polecenia. Wpisz następujące polecenie `dotnet` polecenia, aby utworzyć i uruchomić aplikację w języku C#.

```console
dotnet new console
dotnet run
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```console
Hello World!
```

## <a name="support"></a>Obsługa

Platforma .NET core to [obsługiwane przez firmę Microsoft](https://www.microsoft.com/net/support/policy)na Windows, macOS i Linux. Bezpieczeństwo i jakości jest aktualizowany kilka razy w roku, zazwyczaj co miesiąc.

Dystrybucje binarny platformy .NET core tworzone i testowane na serwerach utrzymywane przez Microsoft na platformie Azure i obsługiwane podobnie jak każdego produktu firmy Microsoft.

[Red Hat obsługuje platformy .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat kompilacji platformy .NET Core ze źródła i udostępnia je w [Red Hat oprogramowania kolekcje](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft współpracują, aby upewnić się, że platformy .NET Core działa dobrze w systemie RHEL.
