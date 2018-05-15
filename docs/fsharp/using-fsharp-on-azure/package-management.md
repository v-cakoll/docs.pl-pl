---
title: 'Przy użyciu pakietu zarządzania z F # na platformie Azure'
description: 'Umożliwia zarządzanie zależności F # Azure Paket lub Nuget'
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fd9c4a15ab0741d44d6d5cf909b7219d310affb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="99a20-103">Pakiet zarządzania zależności Azure F #</span><span class="sxs-lookup"><span data-stu-id="99a20-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="99a20-104">Uzyskiwanie pakietów dla rozwoju platformy Azure jest proste, korzystając z Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="99a20-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="99a20-105">Istnieją dwie opcje [Paket](https://fsprojects.github.io/Paket/) i [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="99a20-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="99a20-106">Przy użyciu Paket</span><span class="sxs-lookup"><span data-stu-id="99a20-106">Using Paket</span></span>

<span data-ttu-id="99a20-107">Jeśli używasz [Paket](https://fsprojects.github.io/Paket/) zależności menedżera, można użyć `paket.exe` narzędzia można dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="99a20-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="99a20-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="99a20-108">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="99a20-109">Lub, jeśli używasz [Mono](https://www.mono-project.com/) dla aplikacji dla wielu platform .NET:</span><span class="sxs-lookup"><span data-stu-id="99a20-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="99a20-110">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu, należy zmodyfikować `paket.dependencies` plików i Pobierz pakiet.</span><span class="sxs-lookup"><span data-stu-id="99a20-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="99a20-111">Jeśli został wcześniej skonfigurowany zależności lub pracy z projektem gdzie zależności zostały utworzone przez innego projektanta, można rozwiązać i zainstaluj zależności lokalnie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="99a20-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="99a20-112">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="99a20-112">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="99a20-113">Można aktualizować wszystkie zależności pakietu do najnowszej wersji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="99a20-113">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="99a20-114">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="99a20-114">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="99a20-115">Przy użyciu narzędzia Nuget</span><span class="sxs-lookup"><span data-stu-id="99a20-115">Using Nuget</span></span>

<span data-ttu-id="99a20-116">Jeśli używasz [NuGet](https://www.nuget.org/) zależności menedżera, można użyć `nuget.exe` narzędzia można dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="99a20-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="99a20-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="99a20-117">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="99a20-118">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="99a20-118">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="99a20-119">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu i pobierania pakietu.</span><span class="sxs-lookup"><span data-stu-id="99a20-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="99a20-120">Jeśli został wcześniej skonfigurowany zależności lub pracy z projektem gdzie zależności zostały utworzone przez innego projektanta, można rozwiązać i zainstaluj zależności lokalnie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="99a20-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="99a20-121">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="99a20-121">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="99a20-122">Można aktualizować wszystkie zależności pakietu do najnowszej wersji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="99a20-122">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="99a20-123">Lub, w przypadku rozwoju Mono:</span><span class="sxs-lookup"><span data-stu-id="99a20-123">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="99a20-124">Odwoływanie się do zestawów</span><span class="sxs-lookup"><span data-stu-id="99a20-124">Referencing Assemblies</span></span>

<span data-ttu-id="99a20-125">Aby można było używać pakietów w skrypcie F #, musisz odwołuje się do zestawów uwzględnione w pakietach za pomocą `#r` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="99a20-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="99a20-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="99a20-126">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="99a20-127">Jak widać, należy określić ścieżkę względną do pliku DLL i pełną nazwę biblioteki DLL, która może nie być dokładnie takie same jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="99a20-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="99a20-128">Ścieżka zawiera wersję framework i prawdopodobnie numer wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="99a20-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="99a20-129">Aby znaleźć wszystkie zainstalowane zestawy, program przypominać w wierszu polecenia systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="99a20-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="99a20-130">Lub w powłoce systemu Unix, coś podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="99a20-130">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="99a20-131">Zapewni to ścieżki do zainstalowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="99a20-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="99a20-132">Z tego miejsca można wybrać prawidłową ścieżkę dla framework w wersji.</span><span class="sxs-lookup"><span data-stu-id="99a20-132">From there, you can select the correct path for your framework version.</span></span>
