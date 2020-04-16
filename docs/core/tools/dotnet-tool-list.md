---
title: Polecenie lista narzędzi dotnet
description: Polecenie lista narzędzi dotnet zawiera listę narzędzi .NET Core zainstalowanych na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463347"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="fe5b0-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="fe5b0-103">dotnet tool list</span></span>

<span data-ttu-id="fe5b0-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="fe5b0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fe5b0-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fe5b0-105">Name</span></span>

<span data-ttu-id="fe5b0-106">`dotnet tool list`- Wyświetla listę wszystkich [narzędzi .NET Core](global-tools.md) określonego typu aktualnie zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fe5b0-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="fe5b0-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="fe5b0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="fe5b0-108">Description</span></span>

<span data-ttu-id="fe5b0-109">Polecenie `dotnet tool list` umożliwia wyświetlenie listy wszystkich narzędzi globalnych, ścieżki narzędzi lub narzędzi lokalnych zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="fe5b0-110">Polecenie zawiera listę nazwy pakietu, zainstalowanej wersji i polecenia narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="fe5b0-111">Aby użyć polecenia, należy określić jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="fe5b0-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="fe5b0-112">Narzędzie globalne zainstalowane w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-112">A global tool installed in the default location.</span></span> <span data-ttu-id="fe5b0-113">Użyj `--global` tej opcji</span><span class="sxs-lookup"><span data-stu-id="fe5b0-113">Use the `--global` option</span></span>
* <span data-ttu-id="fe5b0-114">Narzędzie globalne zainstalowane w lokalizacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="fe5b0-115">Użyj `--tool-path` tej opcji.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="fe5b0-116">Narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-116">A local tool.</span></span> <span data-ttu-id="fe5b0-117">Pomiń `--global` `--tool-path` opcje i.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="fe5b0-118">**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="fe5b0-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="fe5b0-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="fe5b0-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="fe5b0-120">Wyświetla listę narzędzi globalnych dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-120">Lists user-wide global tools.</span></span> <span data-ttu-id="fe5b0-121">Nie można połączyć `--tool-path` z opcją.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="fe5b0-122">Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="fe5b0-123">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="fe5b0-124">Określa niestandardową lokalizację, w której można znaleźć narzędzia globalne.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="fe5b0-125">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="fe5b0-126">Nie można połączyć `--global` z opcją.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="fe5b0-127">Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="fe5b0-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="fe5b0-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="fe5b0-129">Wyświetla listę wszystkich narzędzi globalnych zainstalowanych w całym urządzeniu (bieżący profil użytkownika).</span><span class="sxs-lookup"><span data-stu-id="fe5b0-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="fe5b0-130">Wyświetla listę narzędzi globalnych z określonego katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="fe5b0-131">Wyświetla listę narzędzi globalnych z określonego katalogu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="fe5b0-132">Wyświetla listę wszystkich narzędzi lokalnych dostępnych w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fe5b0-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe5b0-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe5b0-133">See also</span></span>

- [<span data-ttu-id="fe5b0-134">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe5b0-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="fe5b0-135">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe5b0-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="fe5b0-136">Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe5b0-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
