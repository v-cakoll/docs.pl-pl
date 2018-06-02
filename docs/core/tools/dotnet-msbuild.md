---
title: polecenie msbuild DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 58aac2a5314758b8711c0b014154022168fb671c
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696848"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="0db89-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="0db89-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0db89-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0db89-104">Name</span></span>

<span data-ttu-id="0db89-105">`dotnet msbuild` -Tworzy projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="0db89-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0db89-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="0db89-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="0db89-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0db89-107">Description</span></span>

<span data-ttu-id="0db89-108">`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0db89-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="0db89-109">Polecenie ma dokładnie takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0db89-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="0db89-110">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="0db89-110">The options are all the same.</span></span> <span data-ttu-id="0db89-111">Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="0db89-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="0db89-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0db89-112">Examples</span></span>

<span data-ttu-id="0db89-113">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="0db89-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="0db89-114">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="0db89-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="0db89-115">Uruchom lokalizacja docelowa publikowania i publikowania dla `osx.10.11-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="0db89-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="0db89-116">Zobacz całego projektu z wszystkie elementy docelowe uwzględniony przez zestaw SDK:</span><span class="sxs-lookup"><span data-stu-id="0db89-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
