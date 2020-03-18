---
title: dotnet msbuild, polecenie
description: Polecenie dotnet msbuild zapewnia dostęp do wiersza polecenia MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503675"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="06d4c-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="06d4c-103">dotnet msbuild</span></span>

<span data-ttu-id="06d4c-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="06d4c-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="06d4c-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="06d4c-105">Name</span></span>

<span data-ttu-id="06d4c-106">`dotnet msbuild`- Buduje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="06d4c-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="06d4c-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="06d4c-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="06d4c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="06d4c-108">Description</span></span>

<span data-ttu-id="06d4c-109">Polecenie `dotnet msbuild` umożliwia dostęp do w pełni funkcjonalnego MSBuild.</span><span class="sxs-lookup"><span data-stu-id="06d4c-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="06d4c-110">Polecenie ma dokładnie takie same możliwości jak istniejący klient wiersza polecenia MSBuild tylko dla projektów w stylu SDK.</span><span class="sxs-lookup"><span data-stu-id="06d4c-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="06d4c-111">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="06d4c-111">The options are all the same.</span></span> <span data-ttu-id="06d4c-112">Aby uzyskać więcej informacji na temat dostępnych opcji, zobacz [odwołanie wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="06d4c-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="06d4c-113">Polecenie [dotnet build](dotnet-build.md) jest `dotnet msbuild -restore -target:Build`równoważne .</span><span class="sxs-lookup"><span data-stu-id="06d4c-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="06d4c-114">[dotnet kompilacji](dotnet-build.md) jest powszechnie używany do tworzenia projektów, ale ponieważ zawsze `dotnet msbuild` uruchamia cel kompilacji, można użyć, gdy nie chcesz budować projekt.</span><span class="sxs-lookup"><span data-stu-id="06d4c-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="06d4c-115">Na przykład jeśli masz określony cel, który chcesz uruchomić `dotnet msbuild` bez tworzenia projektu, użyj i określ miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="06d4c-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="06d4c-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="06d4c-116">Examples</span></span>

- <span data-ttu-id="06d4c-117">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="06d4c-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="06d4c-118">Tworzenie projektu i jego zależności przy użyciu konfiguracji wersji:</span><span class="sxs-lookup"><span data-stu-id="06d4c-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="06d4c-119">Uruchom obiekt docelowy publikowania `osx.10.11-x64` i opublikuj dla rid:</span><span class="sxs-lookup"><span data-stu-id="06d4c-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="06d4c-120">Zobacz cały projekt ze wszystkimi celami zawartymi w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="06d4c-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
