---
title: polecenie listy narzędzi dotnet
description: Polecenie Lista narzędzi dotnet zawiera listę narzędzi .NET Core zainstalowanych na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: bb74cfeaf441cf8a1a030d97d16655f85d8267d1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543459"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="03ccd-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="03ccd-103">dotnet tool list</span></span>

<span data-ttu-id="03ccd-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="03ccd-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="03ccd-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="03ccd-105">Name</span></span>

<span data-ttu-id="03ccd-106">`dotnet tool list` — wyświetla wszystkie [Narzędzia .NET Core](global-tools.md) określonego typu aktualnie zainstalowane na maszynie.</span><span class="sxs-lookup"><span data-stu-id="03ccd-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="03ccd-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="03ccd-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="03ccd-108">Opis</span><span class="sxs-lookup"><span data-stu-id="03ccd-108">Description</span></span>

<span data-ttu-id="03ccd-109">`dotnet tool list` polecenie umożliwia wyświetlenie listy wszystkich narzędzi programu .NET Core, ścieżek narzędzi i lokalnych zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="03ccd-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="03ccd-110">Polecenie wyświetla listę Nazwa pakietu, zainstalowana wersja i polecenie Narzędzia.</span><span class="sxs-lookup"><span data-stu-id="03ccd-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="03ccd-111">Aby użyć polecenia, należy określić jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="03ccd-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="03ccd-112">Globalne narzędzie zainstalowane w domyślnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="03ccd-112">A global tool installed in the default location.</span></span> <span data-ttu-id="03ccd-113">Użyj opcji `--global`</span><span class="sxs-lookup"><span data-stu-id="03ccd-113">Use the `--global` option</span></span>
* <span data-ttu-id="03ccd-114">Globalne narzędzie zainstalowane w niestandardowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="03ccd-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="03ccd-115">Użyj opcji `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="03ccd-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="03ccd-116">Narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="03ccd-116">A local tool.</span></span> <span data-ttu-id="03ccd-117">Pomiń opcje `--global` i `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="03ccd-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="03ccd-118">**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="03ccd-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="03ccd-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="03ccd-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="03ccd-120">Wyświetla narzędzia globalne dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="03ccd-120">Lists user-wide global tools.</span></span> <span data-ttu-id="03ccd-121">Nie można łączyć z opcją `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="03ccd-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="03ccd-122">Pominięcie obu `--global` i `--tool-path` powoduje wyświetlenie listy lokalnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="03ccd-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="03ccd-123">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="03ccd-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="03ccd-124">Określa niestandardową lokalizację, w której mają zostać znalezione narzędzia globalne.</span><span class="sxs-lookup"><span data-stu-id="03ccd-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="03ccd-125">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="03ccd-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="03ccd-126">Nie można łączyć z opcją `--global`.</span><span class="sxs-lookup"><span data-stu-id="03ccd-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="03ccd-127">Pominięcie obu `--global` i `--tool-path` powoduje wyświetlenie listy lokalnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="03ccd-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span> 

## <a name="examples"></a><span data-ttu-id="03ccd-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="03ccd-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="03ccd-129">Wyświetla wszystkie narzędzia globalne zainstalowane na komputerze (bieżący profil użytkownika).</span><span class="sxs-lookup"><span data-stu-id="03ccd-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="03ccd-130">Wyświetla listę globalnych narzędzi z określonego katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="03ccd-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="03ccd-131">Wyświetla listę globalnych narzędzi z określonego katalogu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="03ccd-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="03ccd-132">Wyświetla listę wszystkich narzędzi lokalnych dostępnych w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="03ccd-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="03ccd-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03ccd-133">See also</span></span>

- [<span data-ttu-id="03ccd-134">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="03ccd-134">.NET Core tools</span></span>](global-tools.md)
