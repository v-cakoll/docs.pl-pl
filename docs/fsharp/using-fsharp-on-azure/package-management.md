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
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="71356-103">Zarządzanie pakietami dla zależności platformy Azure w języku F#</span><span class="sxs-lookup"><span data-stu-id="71356-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="71356-104">Uzyskiwanie pakietów dla deweloperów platformy Azure jest łatwe, korzystając z Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="71356-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="71356-105">Istnieją dwie opcje [Paket](https://fsprojects.github.io/Paket/) i [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="71356-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="71356-106">Za pomocą Paket</span><span class="sxs-lookup"><span data-stu-id="71356-106">Using Paket</span></span>

<span data-ttu-id="71356-107">Jeśli używasz [Paket](https://fsprojects.github.io/Paket/) Menedżera zależności, można użyć `paket.exe` narzędzie, aby dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="71356-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="71356-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="71356-108">For example:</span></span>

```
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="71356-109">Lub, jeśli używasz [Mono](https://www.mono-project.com/) podczas tworzenia aplikacji .NET dla wielu platform:</span><span class="sxs-lookup"><span data-stu-id="71356-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="71356-110">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektów w bieżącym katalogu, należy zmodyfikować `paket.dependencies` plik i Pobierz pakiet.</span><span class="sxs-lookup"><span data-stu-id="71356-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="71356-111">Jeśli został wcześniej skonfigurowany zależności lub pracujesz z projektem gdzie zależności zostały utworzone przez innemu deweloperowi, można rozwiązać i zainstaluj zależności lokalnie w takich jak:</span><span class="sxs-lookup"><span data-stu-id="71356-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> paket install
```

<span data-ttu-id="71356-112">Lub, w przypadku tworzenia Mono:</span><span class="sxs-lookup"><span data-stu-id="71356-112">Or, for Mono development:</span></span>

```
> mono paket.exe install
```

<span data-ttu-id="71356-113">Możesz zaktualizować wszystkie zależności pakietów do najnowszej wersji, takich jak to:</span><span class="sxs-lookup"><span data-stu-id="71356-113">You can update all your package dependencies to the latest version like this:</span></span>

```
> paket update
```

<span data-ttu-id="71356-114">Lub, w przypadku tworzenia Mono:</span><span class="sxs-lookup"><span data-stu-id="71356-114">Or, for Mono development:</span></span>

```
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="71356-115">Za pomocą narzędzia Nuget</span><span class="sxs-lookup"><span data-stu-id="71356-115">Using Nuget</span></span>

<span data-ttu-id="71356-116">Jeśli używasz [NuGet](https://www.nuget.org/) Menedżera zależności, można użyć `nuget.exe` narzędzie, aby dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="71356-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="71356-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="71356-117">For example:</span></span>

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="71356-118">Lub, w przypadku tworzenia Mono:</span><span class="sxs-lookup"><span data-stu-id="71356-118">Or, for Mono development:</span></span>

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="71356-119">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietów dla projektu w bieżącym katalogu i pobieranie pakietu.</span><span class="sxs-lookup"><span data-stu-id="71356-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="71356-120">Jeśli został wcześniej skonfigurowany zależności lub pracujesz z projektem gdzie zależności zostały utworzone przez innemu deweloperowi, można rozwiązać i zainstaluj zależności lokalnie w takich jak:</span><span class="sxs-lookup"><span data-stu-id="71356-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> nuget restore
```

<span data-ttu-id="71356-121">Lub, w przypadku tworzenia Mono:</span><span class="sxs-lookup"><span data-stu-id="71356-121">Or, for Mono development:</span></span>

```
> mono nuget.exe restore
```

<span data-ttu-id="71356-122">Możesz zaktualizować wszystkie zależności pakietów do najnowszej wersji, takich jak to:</span><span class="sxs-lookup"><span data-stu-id="71356-122">You can update all your package dependencies to the latest version like this:</span></span>

```
> nuget update
```

<span data-ttu-id="71356-123">Lub, w przypadku tworzenia Mono:</span><span class="sxs-lookup"><span data-stu-id="71356-123">Or, for Mono development:</span></span>

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="71356-124">Odwoływanie się do zestawów</span><span class="sxs-lookup"><span data-stu-id="71356-124">Referencing Assemblies</span></span>

<span data-ttu-id="71356-125">Aby można było używać pakietów w swojej F# skrypt, należy odwoływać się do zestawów uwzględnione w pakietach za pomocą `#r` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="71356-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="71356-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="71356-126">For example:</span></span>

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="71356-127">Jak widać, należy określić ścieżkę względną do pliku DLL i Pełna nazwa biblioteki DLL, co może nie być dokładnie taka sama jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="71356-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="71356-128">Ścieżka będzie zawierać wersję i ewentualnie numer wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="71356-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="71356-129">Aby znaleźć zainstalowane zestawy, służy podobny do poniższego w wierszu polecenia Windows:</span><span class="sxs-lookup"><span data-stu-id="71356-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="71356-130">Lub w powłoce systemu Unix coś w rodzaju to:</span><span class="sxs-lookup"><span data-stu-id="71356-130">Or in a Unix shell, something like this:</span></span>

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="71356-131">Zapewni to ścieżki do zainstalowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="71356-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="71356-132">Z tego miejsca możesz wybrać poprawną ścieżkę dla używanej wersji framework.</span><span class="sxs-lookup"><span data-stu-id="71356-132">From there, you can select the correct path for your framework version.</span></span>
