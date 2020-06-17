---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803175"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="222a9-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="222a9-103">dotnet msbuild</span></span>

<span data-ttu-id="222a9-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="222a9-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="222a9-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="222a9-105">Name</span></span>

<span data-ttu-id="222a9-106">`dotnet msbuild`-Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="222a9-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="222a9-107">Uwaga: może być konieczne określenie rozwiązania lub pliku projektu, jeśli istnieje wiele.</span><span class="sxs-lookup"><span data-stu-id="222a9-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="222a9-108">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="222a9-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="222a9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="222a9-109">Description</span></span>

<span data-ttu-id="222a9-110">`dotnet msbuild`Polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="222a9-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="222a9-111">Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektów w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="222a9-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="222a9-112">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="222a9-112">The options are all the same.</span></span> <span data-ttu-id="222a9-113">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="222a9-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="222a9-114">Polecenie [budowania dotnet](dotnet-build.md) jest równoważne z `dotnet msbuild -restore` .</span><span class="sxs-lookup"><span data-stu-id="222a9-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="222a9-115">Gdy nie chcesz kompilować projektu i masz określony cel, który chcesz uruchomić, użyj `dotnet build` lub `dotnet msbuild` i określ cel.</span><span class="sxs-lookup"><span data-stu-id="222a9-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="222a9-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="222a9-116">Examples</span></span>

- <span data-ttu-id="222a9-117">Kompiluj projekt i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="222a9-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="222a9-118">Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="222a9-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="222a9-119">Uruchom element docelowy publikowania i opublikuj go pod kątem `osx.10.11-x64` identyfikatora RID:</span><span class="sxs-lookup"><span data-stu-id="222a9-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="222a9-120">Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="222a9-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
