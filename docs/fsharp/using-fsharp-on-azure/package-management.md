---
title: Używanie Zarządzanie pakietami z F# platformą Azure
description: Zarządzanie F# zależnościami platformy Azure przy użyciu usługi Paket lub NuGet
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214228"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="1de88-103">Zarządzanie pakietami dla zależności platformy Azure w języku F#</span><span class="sxs-lookup"><span data-stu-id="1de88-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="1de88-104">Uzyskiwanie pakietów do programowania na platformie Azure jest proste w przypadku korzystania z Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="1de88-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="1de88-105">Te dwie opcje to [Paket](https://fsprojects.github.io/Paket/) i [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="1de88-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="1de88-106">Korzystanie z Paket</span><span class="sxs-lookup"><span data-stu-id="1de88-106">Using Paket</span></span>

<span data-ttu-id="1de88-107">Jeśli używasz [Paket](https://fsprojects.github.io/Paket/) jako Menedżera zależności, możesz użyć `paket.exe` narzędzia, aby dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="1de88-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="1de88-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1de88-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="1de88-109">Lub, jeśli używasz narzędzia [mono](https://www.mono-project.com/) do tworzenia aplikacji dla wielu platform .NET:</span><span class="sxs-lookup"><span data-stu-id="1de88-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="1de88-110">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietu dla projektu w bieżącym katalogu, `paket.dependencies` zmodyfikowanie pliku i pobranie pakietu.</span><span class="sxs-lookup"><span data-stu-id="1de88-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="1de88-111">Jeśli wcześniej skonfigurowano zależności lub pracujesz z projektem, w którym zależności zostały skonfigurowane przez innego dewelopera, możesz rozwiązać i zainstalować zależności lokalnie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1de88-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="1de88-112">Lub, w przypadku programowania mono:</span><span class="sxs-lookup"><span data-stu-id="1de88-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="1de88-113">Wszystkie zależności pakietu można zaktualizować do najnowszej wersji, np.:</span><span class="sxs-lookup"><span data-stu-id="1de88-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="1de88-114">Lub, w przypadku programowania mono:</span><span class="sxs-lookup"><span data-stu-id="1de88-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="1de88-115">Korzystanie z NuGet</span><span class="sxs-lookup"><span data-stu-id="1de88-115">Using Nuget</span></span>

<span data-ttu-id="1de88-116">Jeśli używasz programu [NuGet](https://www.nuget.org/) jako Menedżera zależności, możesz użyć `nuget.exe` narzędzia, aby dodać zależności platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="1de88-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="1de88-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1de88-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="1de88-118">Lub, w przypadku programowania mono:</span><span class="sxs-lookup"><span data-stu-id="1de88-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="1de88-119">Spowoduje to dodanie `WindowsAzure.Storage` do zestawu zależności pakietu dla projektu w bieżącym katalogu i pobranie pakietu.</span><span class="sxs-lookup"><span data-stu-id="1de88-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="1de88-120">Jeśli wcześniej skonfigurowano zależności lub pracujesz z projektem, w którym zależności zostały skonfigurowane przez innego dewelopera, możesz rozwiązać i zainstalować zależności lokalnie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1de88-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="1de88-121">Lub, w przypadku programowania mono:</span><span class="sxs-lookup"><span data-stu-id="1de88-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="1de88-122">Wszystkie zależności pakietu można zaktualizować do najnowszej wersji, np.:</span><span class="sxs-lookup"><span data-stu-id="1de88-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="1de88-123">Lub, w przypadku programowania mono:</span><span class="sxs-lookup"><span data-stu-id="1de88-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="1de88-124">Odwoływanie się do zestawów</span><span class="sxs-lookup"><span data-stu-id="1de88-124">Referencing Assemblies</span></span>

<span data-ttu-id="1de88-125">Aby można było używać pakietów w F# skrypcie, należy odwołać się do zestawów zawartych w pakietach przy użyciu `#r` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="1de88-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="1de88-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1de88-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="1de88-127">Jak widać, należy określić ścieżkę względną do biblioteki DLL i pełną nazwę biblioteki DLL, która może nie być dokładnie taka sama jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="1de88-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="1de88-128">Ścieżka będzie zawierać wersję platformy i prawdopodobnie numer wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="1de88-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="1de88-129">Aby znaleźć wszystkie zainstalowane zestawy, możesz użyć podobnej do tego w wierszu polecenia systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="1de88-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="1de88-130">Lub w powłoce systemu UNIX:</span><span class="sxs-lookup"><span data-stu-id="1de88-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="1de88-131">Spowoduje to udostępnienie ścieżek do zainstalowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="1de88-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="1de88-132">W tym miejscu możesz wybrać poprawną ścieżkę do wersji platformy.</span><span class="sxs-lookup"><span data-stu-id="1de88-132">From there, you can select the correct path for your framework version.</span></span>
