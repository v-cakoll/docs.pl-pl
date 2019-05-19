---
title: Za pomocą Zarządzanie pakietami za pomocą F# dla platformy Azure
description: Umożliwia zarządzanie Paket lub Nuget F# zależności platformy Azure
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: b180024e2276a2fd7786f35cb922b1aa1d91f0ad
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880021"
---
# <a name="package-management-for-f-azure-dependencies"></a>Zarządzanie pakietami dla zależności platformy Azure w języku F#

Uzyskiwanie pakietów dla deweloperów platformy Azure jest łatwe, korzystając z Menedżera pakietów. Istnieją dwie opcje [Paket](https://fsprojects.github.io/Paket/) i [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Za pomocą Paket

Jeśli używasz [Paket](https://fsprojects.github.io/Paket/) Menedżera zależności, można użyć `paket.exe` narzędzie, aby dodać zależności platformy Azure. Na przykład:

```
> paket add nuget WindowsAzure.Storage
```

Lub, jeśli używasz [Mono](https://www.mono-project.com/) podczas tworzenia aplikacji .NET dla wielu platform:

```
> mono paket.exe add nuget WindowsAzure.Storage
```

Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektów w bieżącym katalogu, należy zmodyfikować `paket.dependencies` plik i Pobierz pakiet. Jeśli został wcześniej skonfigurowany zależności lub pracujesz z projektem gdzie zależności zostały utworzone przez innemu deweloperowi, można rozwiązać i zainstaluj zależności lokalnie w takich jak:

```
> paket install
```

Lub, w przypadku tworzenia Mono:

```
> mono paket.exe install
```

Możesz zaktualizować wszystkie zależności pakietów do najnowszej wersji, takich jak to:

```
> paket update
```

Lub, w przypadku tworzenia Mono:

```
> mono paket.exe update
```

## <a name="using-nuget"></a>Za pomocą narzędzia Nuget

Jeśli używasz [NuGet](https://www.nuget.org/) Menedżera zależności, można użyć `nuget.exe` narzędzie, aby dodać zależności platformy Azure. Na przykład:

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

Lub, w przypadku tworzenia Mono:

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu i pobieranie pakietu. Jeśli został wcześniej skonfigurowany zależności lub pracujesz z projektem gdzie zależności zostały utworzone przez innemu deweloperowi, można rozwiązać i zainstaluj zależności lokalnie w takich jak:

```
> nuget restore
```

Lub, w przypadku tworzenia Mono:

```
> mono nuget.exe restore
```

Możesz zaktualizować wszystkie zależności pakietów do najnowszej wersji, takich jak to:

```
> nuget update
```

Lub, w przypadku tworzenia Mono:

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>Odwoływanie się do zestawów

Aby można było używać pakietów w swojej F# skrypt, należy odwoływać się do zestawów uwzględnione w pakietach za pomocą `#r` dyrektywy. Na przykład:

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

Jak widać, należy określić ścieżkę względną do pliku DLL i Pełna nazwa biblioteki DLL, co może nie być dokładnie taka sama jak nazwa pakietu. Ścieżka będzie zawierać wersję i ewentualnie numer wersji pakietu. Aby znaleźć zainstalowane zestawy, służy podobny do poniższego w wierszu polecenia Windows:

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

Lub w powłoce systemu Unix coś w rodzaju to:

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

Zapewni to ścieżki do zainstalowanych zestawów. Z tego miejsca możesz wybrać poprawną ścieżkę dla używanej wersji framework.
