---
title: Przewodnik platformy .NET Core
description: .NET Core to modułowa implementacja platformy .NET o wysokiej wydajności do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75740744"
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

[.NET Core](about.md) to platforma deweloperska [typu open source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)general-purpose prowadzona przez firmę Microsoft i społeczność .NET w [usłudze GitHub.](https://github.com/dotnet/core) Jest wieloplatformowy (obsługujący systemy Windows, macOS i Linux) i może być używany do tworzenia aplikacji urządzeń, chmury i IoT.

Zobacz [temat .NET Core,](about.md) aby dowiedzieć się więcej o .NET Core, w tym jego właściwości, obsługiwane języki i struktury oraz kluczowe interfejsy API.

Zapoznaj się z [samouczkami .NET Core,](tutorials/index.md) aby dowiedzieć się, jak utworzyć prostą aplikację .NET Core. Uruchomienie pierwszej aplikacji zajmuje tylko kilka minut. Jeśli chcesz wypróbować program .NET Core w przeglądarce, zapoznaj się z samouczkiem [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online.

## <a name="download-net-core"></a>Pobierz program .NET Core

Pobierz zestaw [.NET Core SDK,](https://www.microsoft.com/net/download) aby wypróbować program .NET Core na komputerze z systemem Windows, macOS lub Linux. A jeśli wolisz używać kontenerów platformy Docker, odwiedź [centrum docker .NET Core .](https://hub.docker.com/_/microsoft-dotnet-core/)

Wszystkie wersje .NET Core są dostępne w [plikach do pobrania .NET Core,](https://dotnet.microsoft.com/download/dotnet-core) jeśli szukasz innej wersji .NET Core.

## <a name="net-core-31"></a>.NET Core 3.1

Najnowsza wersja to .NET Core 3.1. 3.1 zawiera drobne ulepszenia w stosunku do .NET Core 3.0, jednak .NET Core 3.1 jest [długoterminową obsługiwaną wersją.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) Aby uzyskać więcej informacji na temat wersji .NET Core 3.1, zobacz [Co nowego w .NET Core 3.1](./whats-new/dotnet-core-3-1.md).

## <a name="create-your-first-application"></a>Tworzenie pierwszej aplikacji

Po zainstalowaniu sdk .NET Core otwórz wiersz polecenia. Wprowadź następujące `dotnet` polecenia, aby utworzyć i uruchomić aplikację C#:

```dotnetcli
dotnet new console
dotnet run
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```output
Hello World!
```

## <a name="support"></a>Pomoc techniczna

.NET Core jest [obsługiwany przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy), w systemach Windows, macOS i Linux. Jest aktualizowany pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.

Dystrybucje binarne .NET Core są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i obsługiwane tak jak każdy produkt firmy Microsoft.

[Red Hat obsługuje program .NET Core](http://redhatloves.net/) w systemie Red Hat Enterprise Linux (RHEL). Red Hat buduje .NET Core ze źródła i udostępnia go w [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft współpracują, aby upewnić się, że program .NET Core działa dobrze w systemie RHEL.
