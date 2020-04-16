---
title: Polecenie odinstalowywania narzędzia dotnet
description: Polecenie odinstalowywania narzędzia dotnet odinstalowuje określone narzędzie .NET Core z komputera.
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463310"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="cfc82-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="cfc82-103">dotnet tool uninstall</span></span>

<span data-ttu-id="cfc82-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="cfc82-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cfc82-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cfc82-105">Name</span></span>

<span data-ttu-id="cfc82-106">`dotnet tool uninstall`- Odinstalowuje określone [narzędzie .NET Core](global-tools.md) z komputera.</span><span class="sxs-lookup"><span data-stu-id="cfc82-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cfc82-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cfc82-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="cfc82-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cfc82-108">Description</span></span>

<span data-ttu-id="cfc82-109">Polecenie `dotnet tool uninstall` umożliwia odinstalowanie narzędzi .NET Core z komputera.</span><span class="sxs-lookup"><span data-stu-id="cfc82-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="cfc82-110">Aby użyć polecenia, należy określić jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="cfc82-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="cfc82-111">Aby odinstalować narzędzie globalne zainstalowane w lokalizacji `--global` domyślnej, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="cfc82-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="cfc82-112">Aby odinstalować narzędzie globalne zainstalowane w lokalizacji `--tool-path` niestandardowej, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="cfc82-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="cfc82-113">Aby odinstalować narzędzie lokalne, pomiń `--global` opcje i `--tool-path` opcje.</span><span class="sxs-lookup"><span data-stu-id="cfc82-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="cfc82-114">**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="cfc82-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="cfc82-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cfc82-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="cfc82-116">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="cfc82-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="cfc82-117">Nazwę pakietu można znaleźć za pomocą polecenia [lista narzędzi dotnet.](dotnet-tool-list.md)</span><span class="sxs-lookup"><span data-stu-id="cfc82-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="cfc82-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="cfc82-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="cfc82-119">Określa, że narzędzie do usunięcia pochodzi z instalacji dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cfc82-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="cfc82-120">Nie można połączyć `--tool-path` z opcją.</span><span class="sxs-lookup"><span data-stu-id="cfc82-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="cfc82-121">Pominięcie obu `--global` `--tool-path` i określa, że narzędzie do usunięcia jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="cfc82-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cfc82-122">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="cfc82-123">Określa lokalizację, w której ma być odinstalowywane narzędzie.</span><span class="sxs-lookup"><span data-stu-id="cfc82-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="cfc82-124">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="cfc82-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="cfc82-125">Nie można połączyć `--global` z opcją.</span><span class="sxs-lookup"><span data-stu-id="cfc82-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="cfc82-126">Pominięcie obu `--global` `--tool-path` i określa, że narzędzie do usunięcia jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="cfc82-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="cfc82-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cfc82-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="cfc82-128">Odinstalowuje globalne narzędzie [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="cfc82-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="cfc82-129">Odinstalowuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cfc82-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="cfc82-130">Odinstalowuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="cfc82-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="cfc82-131">Odinstalowuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="cfc82-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfc82-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfc82-132">See also</span></span>

- [<span data-ttu-id="cfc82-133">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="cfc82-133">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="cfc82-134">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="cfc82-134">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="cfc82-135">Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="cfc82-135">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
