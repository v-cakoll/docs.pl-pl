---
title: polecenie lista narzędzi dotnet
description: Polecenie lista narzędzi dotnet zawiera listę narzędzi .NET Core zainstalowanych na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847875"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="be45e-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="be45e-103">dotnet tool list</span></span>

<span data-ttu-id="be45e-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="be45e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="be45e-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="be45e-105">Name</span></span>

<span data-ttu-id="be45e-106">`dotnet tool list`- Wyświetla listę wszystkich [narzędzi .NET Core](global-tools.md) określonego typu aktualnie zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="be45e-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="be45e-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="be45e-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="be45e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="be45e-108">Description</span></span>

<span data-ttu-id="be45e-109">Polecenie `dotnet tool list` umożliwia wyświetlenie wszystkich globalnych, ścieżkowych narzędzi lub lokalnych narzędzi zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="be45e-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="be45e-110">Polecenie zawiera nazwę pakietu, zainstalowaną wersję i polecenie narzędzia.</span><span class="sxs-lookup"><span data-stu-id="be45e-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="be45e-111">Aby użyć tego polecenia, należy określić jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="be45e-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="be45e-112">Narzędzie globalne zainstalowane w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="be45e-112">A global tool installed in the default location.</span></span> <span data-ttu-id="be45e-113">Użyj `--global` opcji</span><span class="sxs-lookup"><span data-stu-id="be45e-113">Use the `--global` option</span></span>
* <span data-ttu-id="be45e-114">Narzędzie globalne zainstalowane w lokalizacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="be45e-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="be45e-115">Użyj `--tool-path` tej opcji.</span><span class="sxs-lookup"><span data-stu-id="be45e-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="be45e-116">Narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="be45e-116">A local tool.</span></span> <span data-ttu-id="be45e-117">Pomiń `--global` `--tool-path` opcje i opcje.</span><span class="sxs-lookup"><span data-stu-id="be45e-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="be45e-118">**Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="be45e-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="be45e-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="be45e-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="be45e-120">Wyświetla listę globalnych narzędzi dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="be45e-120">Lists user-wide global tools.</span></span> <span data-ttu-id="be45e-121">Nie można połączyć z `--tool-path` tą opcją.</span><span class="sxs-lookup"><span data-stu-id="be45e-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="be45e-122">Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="be45e-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="be45e-123">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="be45e-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="be45e-124">Określa niestandardową lokalizację, w której można znaleźć narzędzia globalne.</span><span class="sxs-lookup"><span data-stu-id="be45e-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="be45e-125">PATH może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="be45e-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="be45e-126">Nie można połączyć z `--global` tą opcją.</span><span class="sxs-lookup"><span data-stu-id="be45e-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="be45e-127">Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="be45e-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="be45e-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="be45e-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="be45e-129">Wyświetla listę wszystkich narzędzi globalnych zainstalowanych dla użytkownika na komputerze (bieżący profil użytkownika).</span><span class="sxs-lookup"><span data-stu-id="be45e-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="be45e-130">Wyświetla listę narzędzi globalnych z określonego katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="be45e-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="be45e-131">Wyświetla listę narzędzi globalnych z określonego katalogu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="be45e-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="be45e-132">Wyświetla listę wszystkich narzędzi lokalnych dostępnych w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="be45e-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="be45e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be45e-133">See also</span></span>

- [<span data-ttu-id="be45e-134">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="be45e-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="be45e-135">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="be45e-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="be45e-136">Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="be45e-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
