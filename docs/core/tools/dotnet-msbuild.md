---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117705"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="b8af2-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b8af2-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b8af2-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b8af2-104">Name</span></span>

<span data-ttu-id="b8af2-105">`dotnet msbuild`-Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="b8af2-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b8af2-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b8af2-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="b8af2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b8af2-107">Description</span></span>

<span data-ttu-id="b8af2-108">`dotnet msbuild` Polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b8af2-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="b8af2-109">Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektu w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="b8af2-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="b8af2-110">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="b8af2-110">The options are all the same.</span></span> <span data-ttu-id="b8af2-111">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="b8af2-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="b8af2-112">Polecenie [budowania dotnet](dotnet-build.md) jest równoważne z `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="b8af2-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="b8af2-113">`dotnet build`jest często używany do kompilowania projektów, ale `dotnet msbuild` daje większą kontrolę.</span><span class="sxs-lookup"><span data-stu-id="b8af2-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="b8af2-114">Na przykład jeśli masz konkretny cel, który chcesz uruchomić (bez uruchamiania elementu docelowego kompilacji), prawdopodobnie chcesz użyć `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="b8af2-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="b8af2-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b8af2-115">Examples</span></span>

* <span data-ttu-id="b8af2-116">Kompiluj projekt i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="b8af2-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="b8af2-117">Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="b8af2-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="b8af2-118">Uruchom element docelowy publikowania i opublikuj go `osx.10.11-x64` pod kątem identyfikatora RID:</span><span class="sxs-lookup"><span data-stu-id="b8af2-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="b8af2-119">Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="b8af2-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -pp
  ```
