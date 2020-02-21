---
title: polecenie Narzędzia dotnet
description: Polecenie programu dotnet narzędzie do przywracania instaluje na komputerze środowisko .NET Core Local Tools znajdujące się w zakresie dla bieżącego katalogu.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543909"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="c8fa3-103">Przywracanie narzędzia dotnet</span><span class="sxs-lookup"><span data-stu-id="c8fa3-103">dotnet tool restore</span></span>

<span data-ttu-id="c8fa3-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c8fa3-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c8fa3-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="c8fa3-105">Name</span></span>

<span data-ttu-id="c8fa3-106">`dotnet tool restore` — instaluje na komputerze lokalne narzędzia platformy .NET Core, które znajdują się w zakresie dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8fa3-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c8fa3-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="c8fa3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c8fa3-108">Description</span></span>

<span data-ttu-id="c8fa3-109">`dotnet tool restore` polecenie znajduje plik manifestu narzędzia, który znajduje się w zakresie dla bieżącego katalogu i instaluje narzędzia, które są w nim wymienione.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="c8fa3-110">Aby uzyskać informacje na temat plików manifestu, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool) i [wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="c8fa3-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="c8fa3-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c8fa3-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="c8fa3-112">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="c8fa3-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="c8fa3-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="c8fa3-114">Plik konfiguracji NuGet (*NuGet. config*) do użycia.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="c8fa3-115">Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="c8fa3-116">Ścieżka do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="c8fa3-117">Zapobiegaj równoległemu przywracaniu wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="c8fa3-118">Traktuj błędy źródłowe pakietu jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="c8fa3-119">Nie Buforuj pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="c8fa3-120">Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="c8fa3-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="c8fa3-121">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c8fa3-122">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c8fa3-123">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="c8fa3-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8fa3-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="c8fa3-125">Przywraca lokalne narzędzia dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="c8fa3-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8fa3-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8fa3-126">See also</span></span>

- [<span data-ttu-id="c8fa3-127">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="c8fa3-127">.NET Core tools</span></span>](global-tools.md)
