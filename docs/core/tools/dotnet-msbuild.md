---
title: polecenie msbuild DotNet
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: 983fae6f4ecf875da0b155a668009984b5df50de
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632026"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="a8958-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a8958-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a8958-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a8958-104">Name</span></span>

<span data-ttu-id="a8958-105">`dotnet msbuild` -Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="a8958-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a8958-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a8958-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="a8958-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a8958-107">Description</span></span>

<span data-ttu-id="a8958-108">`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a8958-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="a8958-109">Polecenie ma dokładnie te same możliwości co istniejący klient wiersza polecenia MSBuild tylko projekt w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a8958-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="a8958-110">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="a8958-110">The options are all the same.</span></span> <span data-ttu-id="a8958-111">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="a8958-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="a8958-112">[Kompilacji dotnet](dotnet-build.md) polecenie jest odpowiednikiem `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="a8958-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="a8958-113">`dotnet build` jest częściej używany do tworzenia projektów, ale `dotnet msbuild` daje większą kontrolę.</span><span class="sxs-lookup"><span data-stu-id="a8958-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="a8958-114">Na przykład, jeśli określony element docelowy ma zostać uruchomiony (bez konieczności uruchamiania docelowej kompilacji), prawdopodobnie chcesz użyć `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="a8958-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="a8958-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a8958-115">Examples</span></span>

* <span data-ttu-id="a8958-116">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="a8958-116">Build a project and its dependencies:</span></span>

  ```console
  dotnet msbuild
  ```

* <span data-ttu-id="a8958-117">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="a8958-117">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="a8958-118">Uruchom docelową lokalizację publikacji i publikowania dla `osx.10.11-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="a8958-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="a8958-119">Zobacz całego projektu za pomocą wszystkie elementy docelowe uwzględniony przez zestaw SDK:</span><span class="sxs-lookup"><span data-stu-id="a8958-119">See the whole project with all targets included by the SDK:</span></span>

  ```console
  dotnet msbuild -pp
  ```
