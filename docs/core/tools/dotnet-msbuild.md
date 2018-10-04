---
title: polecenie msbuild DotNet — interfejs wiersza polecenia platformy .NET Core
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583724"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="b6ff7-103">Program msbuild DotNet</span><span class="sxs-lookup"><span data-stu-id="b6ff7-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b6ff7-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b6ff7-104">Name</span></span>

<span data-ttu-id="b6ff7-105">`dotnet msbuild` -Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b6ff7-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b6ff7-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="b6ff7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b6ff7-107">Description</span></span>

<span data-ttu-id="b6ff7-108">`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="b6ff7-109">Polecenie ma dokładnie te same możliwości co istniejący klient wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="b6ff7-110">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-110">The options are all the same.</span></span> <span data-ttu-id="b6ff7-111">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="b6ff7-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="b6ff7-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b6ff7-112">Examples</span></span>

<span data-ttu-id="b6ff7-113">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="b6ff7-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="b6ff7-114">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="b6ff7-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild -p:Configuration=Release`

<span data-ttu-id="b6ff7-115">Uruchom docelową lokalizację publikacji i publikowania dla `osx.10.11-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="b6ff7-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="b6ff7-116">Zobacz całego projektu za pomocą wszystkie elementy docelowe uwzględniony przez zestaw SDK:</span><span class="sxs-lookup"><span data-stu-id="b6ff7-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild -pp`
