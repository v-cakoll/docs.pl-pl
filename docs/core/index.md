---
title: Przewodnik platformy .NET Core
description: .NET Core to modularna, wielowydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i Mac. Dowiedz się więcej o programie .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: a6112851a3d9b46f02c26313e6537170786df10b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117073"
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

[.NET Core](about.md) to platforma programistyczna ["Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)", która jest obsługiwana przez firmę Microsoft i społeczność programu .NET w serwisie [GitHub](https://github.com/dotnet/core). Jest to międzyplatformowe (pomocnicze systemy Windows, macOS i Linux) i mogą być używane do tworzenia aplikacji dla urządzeń, usług w chmurze i IoT.

Zobacz [Informacje o programie .NET Core](about.md) , aby dowiedzieć się więcej na temat platformy .NET Core, w tym jej cech, obsługiwanych języków i struktur oraz kluczowych interfejsów API.

Zapoznaj się z [samouczkami dotyczącymi platformy .NET Core](tutorials/index.md) , aby dowiedzieć się, jak utworzyć prostą aplikację platformy .NET Core. Rozpoczęcie pracy z pierwszą aplikacją może zająć zaledwie kilka minut. Jeśli chcesz wypróbować platformę .NET Core w przeglądarce, poszukaj [cyfr w C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczku online.

## <a name="download-net-core-22"></a>Pobierz program .NET Core 2,2

Pobierz [zestaw .net core 2,2 SDK](https://dotnet.microsoft.com/download) , aby wypróbować platformę .NET Core na komputerze z systemem Windows, MacOS lub Linux. Jeśli wolisz używać kontenerów platformy Docker, odwiedź stronę [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) .

Wszystkie wersje programu .NET Core są dostępne w [programie .NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core) , jeśli szukasz innej wersji platformy .NET Core.

## <a name="net-core-22"></a>.NET Core 2.2

Najnowsza wersja to [.NET Core 2,2](whats-new/dotnet-core-2-2.md). Nowe funkcje obejmują: wdrożenia zależne od platformy, punkty uruchomienia, uwierzytelnianie w usłudze AAD z użyciem usługi Azure SQL i obsługę systemu Windows ARM32.

## <a name="create-your-first-application"></a>Tworzenie pierwszej aplikacji

Po zainstalowaniu zestaw .NET Core SDK Otwórz wiersz polecenia. Wpisz następujące `dotnet` polecenia, aby utworzyć i uruchomić C# aplikację.

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
