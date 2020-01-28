---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733196"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="e2ef2-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="e2ef2-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e2ef2-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e2ef2-104">Name</span></span>

<span data-ttu-id="e2ef2-105">`dotnet msbuild` — kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e2ef2-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e2ef2-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="e2ef2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e2ef2-107">Description</span></span>

<span data-ttu-id="e2ef2-108">`dotnet msbuild` polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="e2ef2-109">Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektów w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="e2ef2-110">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-110">The options are all the same.</span></span> <span data-ttu-id="e2ef2-111">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="e2ef2-111">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="e2ef2-112">Polecenie [budowania dotnet](dotnet-build.md) jest równoważne `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="e2ef2-113">[kompilacja dotnet](dotnet-build.md) jest częściej używana do kompilowania projektów, ale ponieważ zawsze uruchamia element docelowy kompilacji, można użyć `dotnet msbuild`, gdy nie chcesz kompilować projektu.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-113">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="e2ef2-114">Na przykład jeśli masz konkretny cel, który chcesz uruchomić bez kompilowania projektu, użyj `dotnet msbuild` i określ element docelowy.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-114">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="e2ef2-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e2ef2-115">Examples</span></span>

* <span data-ttu-id="e2ef2-116">Kompiluj projekt i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="e2ef2-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="e2ef2-117">Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="e2ef2-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* <span data-ttu-id="e2ef2-118">Uruchom element docelowy publikowania i Opublikuj dla `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="e2ef2-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="e2ef2-119">Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="e2ef2-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
