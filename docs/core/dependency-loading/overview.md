---
title: Ładowanie zależności — .NET Core
description: Omówienie zarządzanego i niezarządzanego ładowania zależności w programie .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 69cca28606c64479d500e731ba95fe404bea38df
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017333"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="4d03c-103">Ładowanie zależności w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d03c-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="4d03c-104">Każda aplikacja .NET Core ma zależności.</span><span class="sxs-lookup"><span data-stu-id="4d03c-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="4d03c-105">Nawet prosta `hello world` aplikacja ma zależności dotyczące części bibliotek klas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d03c-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="4d03c-106">Informacje o standardowej logiki ładowania zestawów programu .NET Core mogą pomóc w zrozumieniu i debugowaniu typowych problemów z wdrażaniem.</span><span class="sxs-lookup"><span data-stu-id="4d03c-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="4d03c-107">W niektórych aplikacjach zależności są określane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4d03c-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="4d03c-108">W takich sytuacjach ważne jest, aby zrozumieć, jak są ładowane zestawy zarządzane i niezarządzane zależności.</span><span class="sxs-lookup"><span data-stu-id="4d03c-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="4d03c-109">Zrozumienie AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="4d03c-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="4d03c-110"><xref:System.Runtime.Loader.AssemblyLoadContext> Interfejs API jest centralny w projekcie ładowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d03c-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="4d03c-111">Artykuł dotyczący [poznania AssemblyLoadContext](understanding-assemblyloadcontext.md) zawiera omówienie pojęć dotyczących projektu.</span><span class="sxs-lookup"><span data-stu-id="4d03c-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="4d03c-112">Szczegóły ładowania</span><span class="sxs-lookup"><span data-stu-id="4d03c-112">Loading details</span></span>

<span data-ttu-id="4d03c-113">Szczegóły algorytmu ładowania zostały omówione krótko w kilku artykułach:</span><span class="sxs-lookup"><span data-stu-id="4d03c-113">The loading algorithm details are covered briefly in several articles:</span></span>
- [<span data-ttu-id="4d03c-114">Algorytm ładowania zestawu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="4d03c-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="4d03c-115">Algorytm ładowania zestawu satelitarnego</span><span class="sxs-lookup"><span data-stu-id="4d03c-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="4d03c-116">Algorytm ładowania biblioteki niezarządzanej (natywnej)</span><span class="sxs-lookup"><span data-stu-id="4d03c-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="4d03c-117">Domyślna sonda</span><span class="sxs-lookup"><span data-stu-id="4d03c-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="4d03c-118">Tworzenie aplikacji platformy .NET Core za pomocą wtyczek</span><span class="sxs-lookup"><span data-stu-id="4d03c-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="4d03c-119">Samouczek [Tworzenie aplikacji platformy .NET Core z wtyczkami](../tutorials/creating-app-with-plugin-support.md) zawiera opis sposobu tworzenia niestandardowego AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="4d03c-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="4d03c-120">Używa <xref:System.Runtime.Loader.AssemblyDependencyResolver> do rozpoznawania zależności wtyczki.</span><span class="sxs-lookup"><span data-stu-id="4d03c-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="4d03c-121">Samouczek prawidłowo izoluje zależności wtyczki od aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="4d03c-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="4d03c-122">Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d03c-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="4d03c-123">[Użycie i debugowanie zestawu do odciążania w artykule .NET Core](../../standard/assembly/unloadability-howto.md) to samouczek krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="4d03c-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability-howto.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="4d03c-124">Pokazuje sposób ładowania aplikacji platformy .NET Core, wykonywania, a następnie zwalniania jej.</span><span class="sxs-lookup"><span data-stu-id="4d03c-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="4d03c-125">Artykuł zawiera również porady dotyczące debugowania.</span><span class="sxs-lookup"><span data-stu-id="4d03c-125">The article also provides debugging tips.</span></span>
