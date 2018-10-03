---
title: polecenie msbuild DotNet — interfejs wiersza polecenia platformy .NET Core
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029703"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="66a4e-103">Program msbuild DotNet</span><span class="sxs-lookup"><span data-stu-id="66a4e-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="66a4e-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="66a4e-104">Name</span></span>

<span data-ttu-id="66a4e-105">`dotnet msbuild` -Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="66a4e-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="66a4e-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="66a4e-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="66a4e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="66a4e-107">Description</span></span>

<span data-ttu-id="66a4e-108">`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="66a4e-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="66a4e-109">Polecenie ma dokładnie te same możliwości co istniejący klient wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="66a4e-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="66a4e-110">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="66a4e-110">The options are all the same.</span></span> <span data-ttu-id="66a4e-111">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="66a4e-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="66a4e-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="66a4e-112">Examples</span></span>

<span data-ttu-id="66a4e-113">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="66a4e-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="66a4e-114">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="66a4e-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild -p:Configuration=Release`

<span data-ttu-id="66a4e-115">Uruchom docelową lokalizację publikacji i publikowania dla `osx.10.11-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="66a4e-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="66a4e-116">Zobacz całego projektu za pomocą wszystkie elementy docelowe uwzględniony przez zestaw SDK:</span><span class="sxs-lookup"><span data-stu-id="66a4e-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild -pp`
