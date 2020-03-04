---
title: polecenie Narzędzia dotnet narzędzie do odinstalowywania
description: Polecenie Narzędzia dotnet narzędzie do odinstalowywania Odinstalowuje określone narzędzie .NET Core z maszyny.
ms.date: 02/14/2020
ms.openlocfilehash: 7a15c169c73cf5a743e0fa6f47645d6bccedbde3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157048"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="4352b-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="4352b-103">dotnet tool uninstall</span></span>

<span data-ttu-id="4352b-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="4352b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4352b-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="4352b-105">Name</span></span>

<span data-ttu-id="4352b-106">`dotnet tool uninstall` — Odinstalowuje określone [Narzędzie .NET Core](global-tools.md) z maszyny.</span><span class="sxs-lookup"><span data-stu-id="4352b-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4352b-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="4352b-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="4352b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4352b-108">Description</span></span>

<span data-ttu-id="4352b-109">`dotnet tool uninstall` polecenie umożliwia odinstalowanie narzędzi .NET Core z komputera.</span><span class="sxs-lookup"><span data-stu-id="4352b-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="4352b-110">Aby użyć polecenia, należy określić jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="4352b-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="4352b-111">Aby odinstalować narzędzie globalne, które zostało zainstalowane w lokalizacji domyślnej, użyj opcji `--global`.</span><span class="sxs-lookup"><span data-stu-id="4352b-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="4352b-112">Aby odinstalować narzędzie globalne, które zostało zainstalowane w niestandardowej lokalizacji, użyj opcji `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="4352b-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="4352b-113">Aby odinstalować narzędzie lokalne, Pomiń opcje `--global` i `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="4352b-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="4352b-114">**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="4352b-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="4352b-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4352b-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="4352b-116">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="4352b-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="4352b-117">Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="4352b-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="4352b-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="4352b-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="4352b-119">Określa, że narzędzie ma zostać usunięte z instalacji na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4352b-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="4352b-120">Nie można łączyć z opcją `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="4352b-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="4352b-121">Pominięcie obu `--global` i `--tool-path` określa, że narzędzie ma zostać usunięte, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4352b-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4352b-122">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4352b-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="4352b-123">Określa lokalizację, w której ma zostać odinstalowane narzędzie.</span><span class="sxs-lookup"><span data-stu-id="4352b-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="4352b-124">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="4352b-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="4352b-125">Nie można łączyć z opcją `--global`.</span><span class="sxs-lookup"><span data-stu-id="4352b-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="4352b-126">Pominięcie obu `--global` i `--tool-path` określa, że narzędzie ma zostać usunięte, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4352b-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="4352b-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4352b-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="4352b-128">Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="4352b-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="4352b-129">Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4352b-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="4352b-130">Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu systemu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="4352b-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="4352b-131">Odinstalowuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4352b-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="4352b-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4352b-132">See also</span></span>

- [<span data-ttu-id="4352b-133">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="4352b-133">.NET Core tools</span></span>](global-tools.md)
