---
title: Przewodnik platformy .NET Core
description: .NET Core to modularna, wielowydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o programie .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740744"
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

[.NET Core](about.md) to platforma programistyczna ["Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)", która jest obsługiwana przez firmę Microsoft i społeczność programu .NET w serwisie [GitHub](https://github.com/dotnet/core). Jest to międzyplatformowe (pomocnicze systemy Windows, macOS i Linux) i mogą być używane do tworzenia aplikacji dla urządzeń, usług w chmurze i IoT.

Zobacz [Informacje o programie .NET Core](about.md) , aby dowiedzieć się więcej na temat platformy .NET Core, w tym jej cech, obsługiwanych języków i struktur oraz kluczowych interfejsów API.

Zapoznaj się z [samouczkami dotyczącymi platformy .NET Core](tutorials/index.md) , aby dowiedzieć się, jak utworzyć prostą aplikację platformy .NET Core. Rozpoczęcie pracy z pierwszą aplikacją może zająć zaledwie kilka minut. Jeśli chcesz wypróbować platformę .NET Core w przeglądarce, poszukaj [cyfr w C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczku online.

## <a name="download-net-core"></a>Pobierz program .NET Core

Pobierz [zestaw .NET Core SDK](https://www.microsoft.com/net/download) , aby wypróbować platformę .NET Core na komputerze z systemem Windows, MacOS lub Linux. Jeśli wolisz używać kontenerów platformy Docker, odwiedź stronę programu [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

Wszystkie wersje programu .NET Core są dostępne w [programie .NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core) , jeśli szukasz innej wersji platformy .NET Core.

## <a name="net-core-31"></a>.NET Core 3,1

Najnowsza wersja to .NET Core 3,1. 3,1 zawiera drobne ulepszenia w porównaniu z platformą .NET Core 3,0, jednak .NET Core 3,1 jest [długoterminową obsługiwaną wersją](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Aby uzyskać więcej informacji o wersji programu .NET Core 3,1, zobacz [co nowego w programie .net core 3,1](./whats-new/dotnet-core-3-1.md).

## <a name="create-your-first-application"></a>Utwórz swoją pierwszą aplikację

Po zainstalowaniu zestaw .NET Core SDK Otwórz wiersz polecenia. Wprowadź następujące polecenia `dotnet`, aby utworzyć i uruchomić C# aplikację:

```dotnetcli
dotnet new console
dotnet run
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```output
Hello World!
```

## <a name="support"></a>Obsługa

Platforma .NET Core jest [obsługiwana przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy), w systemach Windows, MacOS i Linux. Jest ona aktualizowana pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.

Dystrybucje binarne programu .NET Core są kompilowane i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i są obsługiwane w taki sam sposób jak każdy produkt firmy Microsoft.

[Red Hat obsługuje platformę .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat kompiluje platformę .NET Core ze źródła i udostępnia je w [kolekcjach oprogramowania Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft Współpracuj, aby upewnić się, że .NET Core działa dobrze na RHEL.
