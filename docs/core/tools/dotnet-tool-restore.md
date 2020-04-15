---
title: Polecenie przywracanie narzędzia dotnet
description: Polecenie przywracania narzędzia dotnet instaluje na komputerze narzędzia lokalne .NET Core, które są w zakresie dla bieżącego katalogu.
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389616"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="e06dd-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="e06dd-103">dotnet tool restore</span></span>

<span data-ttu-id="e06dd-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="e06dd-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e06dd-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e06dd-105">Name</span></span>

<span data-ttu-id="e06dd-106">`dotnet tool restore`- Instaluje na komputerze narzędzia lokalne .NET Core, które są w zakresie dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="e06dd-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e06dd-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e06dd-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="e06dd-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e06dd-108">Description</span></span>

<span data-ttu-id="e06dd-109">Polecenie `dotnet tool restore` znajduje plik manifestu narzędzia, który znajduje się w zakresie bieżącego katalogu i instaluje narzędzia, które są w nim wymienione.</span><span class="sxs-lookup"><span data-stu-id="e06dd-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="e06dd-110">Aby uzyskać informacje o plikach manifestu, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool) i [Wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="e06dd-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="e06dd-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e06dd-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="e06dd-112">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="e06dd-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="e06dd-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="e06dd-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="e06dd-114">Plik konfiguracji NuGet (*nuget.config*).</span><span class="sxs-lookup"><span data-stu-id="e06dd-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="e06dd-115">Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="e06dd-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="e06dd-116">Ścieżka do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="e06dd-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="e06dd-117">Zapobiegaj przywracaniu wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="e06dd-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="e06dd-118">Traktuj błędy źródła pakietu jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="e06dd-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="e06dd-119">Nie buforuj pakietów i żądań http.</span><span class="sxs-lookup"><span data-stu-id="e06dd-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="e06dd-120">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="e06dd-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="e06dd-121">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e06dd-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e06dd-122">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="e06dd-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e06dd-123">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="e06dd-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="e06dd-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="e06dd-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="e06dd-125">Przywraca narzędzia lokalne dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="e06dd-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="e06dd-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e06dd-126">See also</span></span>

- [<span data-ttu-id="e06dd-127">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="e06dd-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="e06dd-128">Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="e06dd-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
