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
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="1ed1e-104">Pakiet zarządzania zależności Azure F #</span><span class="sxs-lookup"><span data-stu-id="1ed1e-104">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="1ed1e-105">Uzyskiwanie pakietów dla rozwoju platformy Azure jest proste, korzystając z Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-105">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="1ed1e-106">Istnieją dwie opcje [Paket](https://fsprojects.github.io/Paket/) i [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="1ed1e-106">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="1ed1e-107">Przy użyciu Paket</span><span class="sxs-lookup"><span data-stu-id="1ed1e-107">Using Paket</span></span>

<span data-ttu-id="1ed1e-108">Jeśli używasz [Paket](https://fsprojects.github.io/Paket/) zależności menedżera, można użyć `paket.exe` narzędzia można dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-108">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="1ed1e-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-109">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="1ed1e-110">Lub, jeśli używasz [Mono](https://www.mono-project.com/) dla aplikacji dla wielu platform .NET:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-110">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="1ed1e-111">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu, należy zmodyfikować `paket.dependencies` plików i Pobierz pakiet.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-111">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="1ed1e-112">Jeśli został wcześniej skonfigurowany zależności lub pracy z projektem gdzie zależności zostały utworzone przez innego projektanta, można rozwiązać i zainstaluj zależności lokalnie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-112">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="1ed1e-113">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-113">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="1ed1e-114">Można aktualizować wszystkie zależności pakietu do najnowszej wersji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-114">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="1ed1e-115">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-115">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="1ed1e-116">Przy użyciu narzędzia Nuget</span><span class="sxs-lookup"><span data-stu-id="1ed1e-116">Using Nuget</span></span>

<span data-ttu-id="1ed1e-117">Jeśli używasz [NuGet](https://www.nuget.org/) zależności menedżera, można użyć `nuget.exe` narzędzia można dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-117">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="1ed1e-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-118">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="1ed1e-119">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-119">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="1ed1e-120">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu i pobierania pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-120">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="1ed1e-121">Jeśli został wcześniej skonfigurowany zależności lub pracy z projektem gdzie zależności zostały utworzone przez innego projektanta, można rozwiązać i zainstaluj zależności lokalnie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-121">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="1ed1e-122">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-122">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="1ed1e-123">Można aktualizować wszystkie zależności pakietu do najnowszej wersji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-123">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="1ed1e-124">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-124">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="1ed1e-125">Odwoływanie się do zestawów</span><span class="sxs-lookup"><span data-stu-id="1ed1e-125">Referencing Assemblies</span></span>

<span data-ttu-id="1ed1e-126">Aby można było używać pakietów w skrypcie F #, musisz odwołuje się do zestawów uwzględnione w pakietach za pomocą `#r` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-126">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="1ed1e-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-127">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="1ed1e-128">Jak widać, należy określić ścieżkę względną do pliku DLL i pełną nazwę biblioteki DLL, która może nie być dokładnie takie same jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-128">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="1ed1e-129">Ścieżka zawiera wersję framework i prawdopodobnie numer wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-129">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="1ed1e-130">Aby znaleźć wszystkie zainstalowane zestawy, program przypominać w wierszu polecenia systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-130">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="1ed1e-131">Lub w powłoce systemu Unix, coś podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="1ed1e-131">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="1ed1e-132">Zapewni to ścieżki do zainstalowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-132">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="1ed1e-133">Z tego miejsca można wybrać prawidłową ścieżkę dla framework w wersji.</span><span class="sxs-lookup"><span data-stu-id="1ed1e-133">From there, you can select the correct path for your framework version.</span></span>
