---
title: Ładowanie zależności — .NET Core
description: Omówienie ładowania zależności zarządzanej i niezarządzanej w ustom .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416641"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="86a4e-103">Ładowanie zależności w ustom .NET Core</span><span class="sxs-lookup"><span data-stu-id="86a4e-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="86a4e-104">Każda aplikacja .NET Core ma zależności.</span><span class="sxs-lookup"><span data-stu-id="86a4e-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="86a4e-105">Nawet prosta `hello world` aplikacja ma zależności od części bibliotek klas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86a4e-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="86a4e-106">Opis logiki domyślnego ładowania zestawu .NET Core może pomóc w zrozumieniu i debugowaniu typowych problemów z wdrażaniem.</span><span class="sxs-lookup"><span data-stu-id="86a4e-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="86a4e-107">W niektórych aplikacjach zależności są dynamicznie określane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86a4e-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="86a4e-108">W takich sytuacjach ważne jest, aby zrozumieć, jak są ładowane zestawy zarządzane i niezarządzane zależności.</span><span class="sxs-lookup"><span data-stu-id="86a4e-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="86a4e-109">Informacje o elemencie AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="86a4e-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="86a4e-110">Interfejs <xref:System.Runtime.Loader.AssemblyLoadContext> API jest centralnym elementem projektu ładowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86a4e-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="86a4e-111">[Opis AssemblyLoadContext](understanding-assemblyloadcontext.md) artykuł zawiera omówienie koncepcyjne do projektu.</span><span class="sxs-lookup"><span data-stu-id="86a4e-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="86a4e-112">Ładowanie szczegółów</span><span class="sxs-lookup"><span data-stu-id="86a4e-112">Loading details</span></span>

<span data-ttu-id="86a4e-113">Szczegóły algorytmu ładowania są krótko omówione w kilku artykułach:</span><span class="sxs-lookup"><span data-stu-id="86a4e-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="86a4e-114">Algorytm ładowania zestawu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="86a4e-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="86a4e-115">Algorytm ładowania zestawu satelitarnego</span><span class="sxs-lookup"><span data-stu-id="86a4e-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="86a4e-116">Niezarządzany (natywny) algorytm ładowania biblioteki</span><span class="sxs-lookup"><span data-stu-id="86a4e-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="86a4e-117">Sondowanie domyślne</span><span class="sxs-lookup"><span data-stu-id="86a4e-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="86a4e-118">Tworzenie aplikacji platformy .NET Core za pomocą wtyczek</span><span class="sxs-lookup"><span data-stu-id="86a4e-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="86a4e-119">Samouczek [Tworzenie aplikacji .NET Core z wtyczkami](../tutorials/creating-app-with-plugin-support.md) opisuje sposób tworzenia niestandardowego AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="86a4e-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="86a4e-120">Używa <xref:System.Runtime.Loader.AssemblyDependencyResolver> do rozwiązywania zależności wtyczki.</span><span class="sxs-lookup"><span data-stu-id="86a4e-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="86a4e-121">Samouczek poprawnie izoluje zależności wtyczki od aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="86a4e-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="86a4e-122">Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="86a4e-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="86a4e-123">[Jak używać i debugować zwalnialność zestawu w](../../standard/assembly/unloadability.md) artykule .NET Core jest samouczek krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="86a4e-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="86a4e-124">Pokazuje, jak załadować aplikację .NET Core, wykonać, a następnie zwolnić go.</span><span class="sxs-lookup"><span data-stu-id="86a4e-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="86a4e-125">Artykuł zawiera również wskazówki dotyczące debugowania.</span><span class="sxs-lookup"><span data-stu-id="86a4e-125">The article also provides debugging tips.</span></span>
