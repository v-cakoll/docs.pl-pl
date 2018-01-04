---
title: "Eksportowanie do platformy .NET Core - analizowanie zależności innych firm"
description: "Eksportowanie do platformy .NET Core - analizowanie zależności innych firm"
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a>Eksportowanie do platformy .NET Core - analizowanie zależności innych firm

Pierwszym krokiem w procesie przenoszenia jest zrozumienie zależności innych firm.  Należy sprawdzić, który z nich, jeśli istnieje, nie jeszcze Uruchom na .NET Core i opracowanie planu gotowości do tych, które nie działają na .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

W tym artykule przyjmie korzystasz z systemu Windows i programu Visual Studio i czy masz kod, który obecnie jest uruchamiana w programie .NET Framework.

## <a name="analyzing-nuget-packages"></a>Analiza pakietów NuGet

Analiza pakietów NuGet przenośności jest bardzo proste.  Pakiet NuGet jest zestaw folderów, które zawierają zestawy specyficzne dla platformy, musisz wykonać jest sprawdzenie, czy jest folder, który zawiera zestaw .NET Core.

Pakiet NuGet folderach najłatwiej z [Explorer pakietu NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) narzędzia.  Oto jak to zrobić.

1. Pobierz i Otwórz Eksploratora pakietu NuGet.
2. Kliknij przycisk "Otwórz pakiet ze strumieniowego źródła online".
3. Wyszukaj nazwę pakietu.
4. Rozwiń węzeł folderu "lib" po prawej stronie i przyjrzyj się nazwy folderów.

Możesz również sprawdzić pakietu obsługuje na [nuget.org](https://www.nuget.org/) w obszarze **zależności** sekcji strony dla tego pakietu.

W obu przypadkach należy szukać folder lub wpis [nuget.org](https://www.nuget.org/) za pomocą dowolnego z następujących nazw:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Są to docelowej Framework monikerów (TFM), które mapują do wersji [.NET Standard](../../standard/net-standard.md) i tradycyjnych profile przenośnej biblioteki klasy (PCL), które są zgodne z platformą .NET Core.  Należy pamiętać, że `netcoreapp1.0`, podczas zgodny, jest dla aplikacji i nie bibliotek.  Mimo że nie ma problem z za pomocą biblioteki, który jest `netcoreapp1.0`— na podstawie, biblioteki mogą nie być przeznaczone do wszelkich *innych* niż użycie przez inne `netcoreapp1.0` aplikacji.

Dostępne są również niektórych starszych TFMs używane w wersji wstępnych programu .NET Core, które mogą być niezgodne:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

**Gdy te prawdopodobnie będzie działać w kodzie, nie ma żadnej gwarancji zgodności**.  Pakiety z tych TFMs zostały skompilowane z pakietami .NET Core wersji wstępnej.  Zwróć uwagę, gdy (lub) pakiety takie zostaną zaktualizowane, aby być `netstandard`— na podstawie.

> [!NOTE]
> Pakiet tradycyjnych PCL lub docelowej platformy .NET Core wersji wstępnej, możesz korzystać `imports` dyrektywy w Twojej `project.json` pliku.

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co robić, jeśli zależność pakietu NuGet nie działa na .NET Core

Istnieje kilka rzeczy, które można wykonać, gdy nie można uruchomić pakietu NuGet, które zależą od platformy .NET Core.

1. Projekt jest typu open source, takie jak GitHub hostowany developer(s) może prowadzić bezpośrednio.
2. Można skontaktować się z autorem bezpośrednio na [nuget.org](https://www.nuget.org/) wyszukiwania dla pakietu, a następnie klikając polecenie "Skontaktuj się z właścicieli" po stronie lewej strony pakietu.
3. Można wyszukać inny pakiet, który działa na .NET Core, które wykonuje to samo zadanie pakietu, który był używany.
4. Możesz spróbować pisanie kodu, że pakiet wykonywanych samodzielnie.
5. Zależność od pakietu można wyeliminować, zmieniając funkcji aplikacji, co najmniej do momentu udostępnienia zgodnej wersji pakietu.

Należy pamiętać, że maintainers projekt typu open source i wydawców pakietu NuGet są często ochotników, którzy przyczyniają się, ponieważ interesujących danej domeny, należy go bezpłatnie i często mają różne zadania dziennych. Jeśli przejdziesz może rozpoczynać się od instrukcji dodatnią informacje o bibliotece przed pytaniem o obsłudze .NET Core.

Jeśli nie uda się rozwiązać problem z żadnym z powyższych, może być konieczne port .NET Core w późniejszym terminie.

Zespół .NET chcesz dowiedzieć się, które biblioteki są najważniejsze obsługuje next z platformą .NET Core. Możesz również wysłać nam poczty na dotnet@microsoft.com o bibliotekach chcesz użyć.

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a>Analizowanie zależności, które nie są pakietów NuGet

Może mieć zależności, która nie jest pakietem NuGet, takich jak biblioteki DLL w systemie plików.  Jedynym sposobem, aby określić przenośność Zależność ta jest uruchomienie [narzędzie ApiPort](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).

## <a name="next-steps"></a>Następne kroki

Jeśli w przypadku przenoszenia biblioteki, zapoznaj się [eksportowanie bibliotek](libraries.md).
