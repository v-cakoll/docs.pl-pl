---
title: Polecenie przywracanie narzędzia dotnet
description: Polecenie przywracania narzędzia dotnet instaluje na komputerze narzędzia lokalne .NET Core, które są w zakresie dla bieżącego katalogu.
ms.date: 02/14/2020
ms.openlocfilehash: a518c2d45bbe9522bddfed4bbef61b30f1ad634b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463332"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="2b583-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="2b583-103">dotnet tool restore</span></span>

<span data-ttu-id="2b583-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="2b583-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2b583-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2b583-105">Name</span></span>

<span data-ttu-id="2b583-106">`dotnet tool restore`- Instaluje na komputerze narzędzia lokalne .NET Core, które są w zakresie dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2b583-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2b583-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2b583-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="2b583-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2b583-108">Description</span></span>

<span data-ttu-id="2b583-109">Polecenie `dotnet tool restore` znajduje plik manifestu narzędzia, który znajduje się w zakresie bieżącego katalogu i instaluje narzędzia, które są w nim wymienione.</span><span class="sxs-lookup"><span data-stu-id="2b583-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="2b583-110">Aby uzyskać informacje o plikach manifestu, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool) i [Wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="2b583-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="2b583-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2b583-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="2b583-112">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="2b583-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="2b583-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="2b583-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2b583-114">Plik konfiguracji NuGet (*nuget.config*).</span><span class="sxs-lookup"><span data-stu-id="2b583-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="2b583-115">Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="2b583-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="2b583-116">Ścieżka do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="2b583-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="2b583-117">Zapobiegaj przywracaniu wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="2b583-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="2b583-118">Traktuj błędy źródła pakietu jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="2b583-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="2b583-119">Nie buforuj pakietów i żądań http.</span><span class="sxs-lookup"><span data-stu-id="2b583-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="2b583-120">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="2b583-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="2b583-121">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2b583-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2b583-122">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="2b583-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2b583-123">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="2b583-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="2b583-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b583-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="2b583-125">Przywraca narzędzia lokalne dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2b583-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b583-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b583-126">See also</span></span>

- [<span data-ttu-id="2b583-127">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b583-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="2b583-128">Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b583-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
