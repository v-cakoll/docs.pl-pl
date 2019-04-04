---
title: Przewodnik platformy .NET Core
description: Platforma .NET core to moduły, wysokowydajnych implementacji .NET do tworzenia aplikacji Windows, Linux i Mac. Dowiedz się więcej na temat platformy .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 79a0c09074159160dd01b0c7970612f7058cc3fc
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920626"
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

[.NET core](about.md) jest [typu open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), platforma deweloperska ogólnego przeznaczenia, obsługiwane przez firmę Microsoft i społeczności platformy .NET w [GitHub](https://github.com/dotnet/core). Jest wiele platform (Obsługa Windows, macOS i Linux) i może służyć do tworzenia urządzeń, chmury i aplikacji IoT.

Zobacz [platformy .NET Core](about.md) Aby dowiedzieć się więcej na temat platformy .NET Core, w tym właściwości, języków i struktur i klucza API.

Zapoznaj się z [Samouczki programu .NET Core](tutorials/index.md) dowiesz się, jak utworzyć prostą aplikację platformy .NET Core. Trwa tylko kilka minut, aby uzyskać swoją pierwszą aplikację, działanie. Jeśli chcesz wypróbować platformy .NET Core w przeglądarce, Przyjrzyj się [liczby w elemencie C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczek online.

## <a name="download-net-core-22"></a>Pobierz program .NET Core 2.2

Pobierz [zestawu .NET Core 2.2 SDK](https://www.microsoft.com/net/download) próby platformy .NET Core na komputerze Windows, macOS lub Linux. Odwiedź stronę [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) Jeśli wolisz używać kontenerów platformy Docker.

Wszystkie wersje platformy .NET Core są dostępne pod adresem [pobierania programu .NET Core](https://www.microsoft.com/net/download/archives) interesuje Cię bliższa dla innej wersji programu .NET Core.

## <a name="net-core-22"></a>.NET Core 2.2

Najnowsza wersja to [platformy .NET Core 2.2](whats-new/dotnet-core-2-2.md). Nowe funkcje obejmują: wdrożeń zależny od struktury, punkty zaczepienia uruchamiania, uwierzytelnianie w usłudze AAD przy użyciu usługi Azure SQL i pomoc techniczna dla Windows ARM32.

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

## <a name="support"></a>Pomoc techniczna

Platforma .NET core to [obsługiwane przez firmę Microsoft](https://www.microsoft.com/net/support/policy)na Windows, macOS i Linux. Bezpieczeństwo i jakości jest aktualizowany kilka razy w roku, zazwyczaj co miesiąc.

Dystrybucje binarny platformy .NET core tworzone i testowane na serwerach utrzymywane przez Microsoft na platformie Azure i obsługiwane podobnie jak każdego produktu firmy Microsoft.

[Red Hat obsługuje platformy .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat kompilacji platformy .NET Core ze źródła i udostępnia je w [Red Hat oprogramowania kolekcje](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft współpracują, aby upewnić się, że platformy .NET Core działa dobrze w systemie RHEL.
