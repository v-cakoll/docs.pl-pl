---
title: Przewodnik platformy .NET Core
description: .NET Core to modularna, wielowydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i Mac. Dowiedz się więcej o programie .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 09/23/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 95f18ca09852ce139a4b99ed7aef4802d4883e13
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216217"
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

[.NET Core](about.md) to platforma programistyczna ["Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)", która jest obsługiwana przez firmę Microsoft i społeczność programu .NET w serwisie [GitHub](https://github.com/dotnet/core). Jest to międzyplatformowe (pomocnicze systemy Windows, macOS i Linux) i mogą być używane do tworzenia aplikacji dla urządzeń, usług w chmurze i IoT.

Zobacz [Informacje o programie .NET Core](about.md) , aby dowiedzieć się więcej na temat platformy .NET Core, w tym jej cech, obsługiwanych języków i struktur oraz kluczowych interfejsów API.

Zapoznaj się z [samouczkami dotyczącymi platformy .NET Core](tutorials/index.md) , aby dowiedzieć się, jak utworzyć prostą aplikację platformy .NET Core. Rozpoczęcie pracy z pierwszą aplikacją może zająć zaledwie kilka minut. Jeśli chcesz wypróbować platformę .NET Core w przeglądarce, poszukaj [cyfr w C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczku online.

## <a name="download-net-core"></a>Pobierz program .NET Core

Pobierz [zestaw .NET Core SDK](https://www.microsoft.com/net/download) , aby wypróbować platformę .NET Core na komputerze z systemem Windows, MacOS lub Linux. Jeśli wolisz używać kontenerów platformy Docker, odwiedź stronę programu [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

Wszystkie wersje programu .NET Core są dostępne w [programie .NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core) , jeśli szukasz innej wersji platformy .NET Core.

## <a name="net-core-30"></a>.NET Core 3.0

Najnowsza wersja to .NET Core 3,0. Nowe funkcje obejmują obsługę pulpitu systemu Windows z Windows Presentation Foundation (WPF) i Windows Forms, tworzenie C# aplikacji sieci Web w pełnym stosie przy użyciu usługi Blazor, nowe udoskonalenia funkcji sygnalizujących i usługa Azure Signal, nowe C# funkcje języka: C# 8 i wiele innych. Aby zapoznać się z pełną listą nowych funkcji w programie .NET Core 3,0, zobacz [co nowego w programie .net core 3,0](./whats-new/dotnet-core-3-0.md).

## <a name="create-your-first-application"></a>Tworzenie pierwszej aplikacji

Po zainstalowaniu zestaw .NET Core SDK Otwórz wiersz polecenia. Wpisz następujące `dotnet` polecenia, aby utworzyć i uruchomić C# aplikację:

```dotnetcli
dotnet new console
dotnet run
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```output
Hello World!
```

## <a name="support"></a>Pomoc techniczna

Platforma .NET Core jest [obsługiwana przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy), w systemach Windows, MacOS i Linux. Jest ona aktualizowana pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.

Dystrybucje binarne programu .NET Core są kompilowane i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i są obsługiwane w taki sam sposób jak każdy produkt firmy Microsoft.

[Red Hat obsługuje platformę .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat kompiluje platformę .NET Core ze źródła i udostępnia je w [kolekcjach oprogramowania Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft Współpracuj, aby upewnić się, że .NET Core działa dobrze na RHEL.
