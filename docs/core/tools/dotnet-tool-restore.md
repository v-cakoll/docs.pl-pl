---
title: polecenie przywracania narzędzia dotnet
description: Polecenie przywracania narzędzia dotnet instaluje na komputerze narzędzia lokalne .NET Core, które znajdują się w zakresie bieżącego katalogu.
ms.date: 02/14/2020
ms.openlocfilehash: cb46f70afb58e482b6aedfddfbf5f3a0c40674f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146440"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="fd27a-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="fd27a-103">dotnet tool restore</span></span>

<span data-ttu-id="fd27a-104">**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="fd27a-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fd27a-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fd27a-105">Name</span></span>

<span data-ttu-id="fd27a-106">`dotnet tool restore`- Instaluje na komputerze narzędzia lokalne .NET Core, które są w zakresie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd27a-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fd27a-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="fd27a-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [-interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="fd27a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="fd27a-108">Description</span></span>

<span data-ttu-id="fd27a-109">Polecenie `dotnet tool restore` znajduje plik manifestu narzędzia, który znajduje się w zakresie bieżącego katalogu i instaluje narzędzia, które są w nim wymienione.</span><span class="sxs-lookup"><span data-stu-id="fd27a-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="fd27a-110">Aby uzyskać informacje o plikach manifestu, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool) i [Wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="fd27a-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="fd27a-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fd27a-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="fd27a-112">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="fd27a-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="fd27a-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="fd27a-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="fd27a-114">Plik konfiguracji NuGet *(nuget.config)* do użycia.</span><span class="sxs-lookup"><span data-stu-id="fd27a-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="fd27a-115">Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="fd27a-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="fd27a-116">Ścieżka do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="fd27a-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="fd27a-117">Zapobiegaj przywracaniu wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="fd27a-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="fd27a-118">Traktuj błędy źródła pakietu jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="fd27a-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="fd27a-119">Nie buforuj pakietów i żądań http.</span><span class="sxs-lookup"><span data-stu-id="fd27a-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="fd27a-120">Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie).</span><span class="sxs-lookup"><span data-stu-id="fd27a-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="fd27a-121">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fd27a-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="fd27a-122">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="fd27a-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fd27a-123">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="fd27a-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="fd27a-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd27a-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="fd27a-125">Przywraca narzędzia lokalne dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd27a-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd27a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd27a-126">See also</span></span>

- [<span data-ttu-id="fd27a-127">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd27a-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="fd27a-128">Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd27a-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
