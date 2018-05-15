---
title: polecenie msbuild DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: c51c058391de4925afd4339fe84e28500d692e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="ebe54-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="ebe54-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ebe54-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ebe54-104">Name</span></span>

<span data-ttu-id="ebe54-105">`dotnet msbuild` -Tworzy projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="ebe54-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ebe54-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ebe54-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="ebe54-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ebe54-107">Description</span></span>

<span data-ttu-id="ebe54-108">`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ebe54-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="ebe54-109">Polecenie ma dokładnie takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ebe54-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="ebe54-110">Opcje są takie same.</span><span class="sxs-lookup"><span data-stu-id="ebe54-110">The options are all the same.</span></span> <span data-ttu-id="ebe54-111">Użyj [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) uzyskiwania informacji na temat dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="ebe54-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="ebe54-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ebe54-112">Examples</span></span>

<span data-ttu-id="ebe54-113">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="ebe54-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="ebe54-114">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="ebe54-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="ebe54-115">Uruchom lokalizacja docelowa publikowania i publikowania dla `osx.10.11-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="ebe54-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="ebe54-116">Zobacz całego projektu z wszystkie elementy docelowe uwzględniony przez zestaw SDK:</span><span class="sxs-lookup"><span data-stu-id="ebe54-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
