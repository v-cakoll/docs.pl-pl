---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503675"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="a6bf2-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a6bf2-103">dotnet msbuild</span></span>

<span data-ttu-id="a6bf2-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="a6bf2-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a6bf2-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="a6bf2-105">Name</span></span>

<span data-ttu-id="a6bf2-106">`dotnet msbuild` — kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a6bf2-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a6bf2-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="a6bf2-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a6bf2-108">Description</span></span>

<span data-ttu-id="a6bf2-109">`dotnet msbuild` polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="a6bf2-110">Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektów w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="a6bf2-111">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-111">The options are all the same.</span></span> <span data-ttu-id="a6bf2-112">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="a6bf2-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="a6bf2-113">Polecenie [budowania dotnet](dotnet-build.md) jest równoważne `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="a6bf2-114">[kompilacja dotnet](dotnet-build.md) jest częściej używana do kompilowania projektów, ale ponieważ zawsze uruchamia element docelowy kompilacji, można użyć `dotnet msbuild`, gdy nie chcesz kompilować projektu.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="a6bf2-115">Na przykład jeśli masz konkretny cel, który chcesz uruchomić bez kompilowania projektu, użyj `dotnet msbuild` i określ element docelowy.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="a6bf2-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a6bf2-116">Examples</span></span>

- <span data-ttu-id="a6bf2-117">Kompiluj projekt i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="a6bf2-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="a6bf2-118">Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="a6bf2-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="a6bf2-119">Uruchom element docelowy publikowania i Opublikuj dla `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="a6bf2-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="a6bf2-120">Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="a6bf2-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
