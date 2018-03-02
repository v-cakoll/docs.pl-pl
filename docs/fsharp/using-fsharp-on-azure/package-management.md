---
title: "Przy użyciu pakietu zarządzania z F # na platformie Azure"
description: "Umożliwia zarządzanie zależności F # Azure Paket lub Nuget"
keywords: visual f#, f#, functional programming, .NET, .NET Core, Azure
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: d1a807053f5c4c45492f206739922aacdf6d4122
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="package-management-for-f-azure-dependencies"></a>Pakiet zarządzania zależności Azure F #

Uzyskiwanie pakietów dla rozwoju platformy Azure jest proste, korzystając z Menedżera pakietów. Istnieją dwie opcje [Paket](https://fsprojects.github.io/Paket/) i [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Przy użyciu Paket

Jeśli używasz [Paket](https://fsprojects.github.io/Paket/) zależności menedżera, można użyć `paket.exe` narzędzia można dodać zależności platformy Azure. Na przykład:

    > paket add nuget WindowsAzure.Storage

Lub, jeśli używasz [Mono](https://www.mono-project.com/) dla aplikacji dla wielu platform .NET:

    > mono paket.exe add nuget WindowsAzure.Storage

Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu, należy zmodyfikować `paket.dependencies` plików i Pobierz pakiet. Jeśli został wcześniej skonfigurowany zależności lub pracy z projektem gdzie zależności zostały utworzone przez innego projektanta, można rozwiązać i zainstaluj zależności lokalnie w następujący sposób:

    > paket install

Lub, w przypadku rozwoju Mono:

    > mono paket.exe install

Można aktualizować wszystkie zależności pakietu do najnowszej wersji w następujący sposób:

    > paket update

Lub, w przypadku rozwoju Mono:

    > mono paket.exe update

## <a name="using-nuget"></a>Przy użyciu narzędzia Nuget

Jeśli używasz [NuGet](https://www.nuget.org/) zależności menedżera, można użyć `nuget.exe` narzędzia można dodać zależności platformy Azure. Na przykład:

    > nuget install WindowsAzure.Storage -ExcludeVersion

Lub, w przypadku rozwoju Mono:

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu i pobierania pakietu. Jeśli został wcześniej skonfigurowany zależności lub pracy z projektem gdzie zależności zostały utworzone przez innego projektanta, można rozwiązać i zainstaluj zależności lokalnie w następujący sposób:

    > nuget restore 

Lub, w przypadku rozwoju Mono:

    > mono nuget.exe restore

Można aktualizować wszystkie zależności pakietu do najnowszej wersji w następujący sposób:

    > nuget update

Lub, w przypadku rozwoju Mono:

    > mono nuget.exe update

## <a name="referencing-assemblies"></a>Odwoływanie się do zestawów

Aby można było używać pakietów w skrypcie F #, musisz odwołuje się do zestawów uwzględnione w pakietach za pomocą `#r` dyrektywy. Na przykład:

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

Jak widać, należy określić ścieżkę względną do pliku DLL i pełną nazwę biblioteki DLL, która może nie być dokładnie takie same jak nazwa pakietu. Ścieżka zawiera wersję framework i prawdopodobnie numer wersji pakietu. Aby znaleźć wszystkie zainstalowane zestawy, program przypominać w wierszu polecenia systemu Windows:

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

Lub w powłoce systemu Unix, coś podobnie do następującej:

    > find packages/WindowsAzure.Storage -name "*.dll"

Zapewni to ścieżki do zainstalowanych zestawów. Z tego miejsca można wybrać prawidłową ścieżkę dla framework w wersji.
