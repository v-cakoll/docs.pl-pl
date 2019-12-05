---
title: Ustawienia konfiguracji wątkowości
description: Informacje na temat ustawień czasu wykonywania, które konfigurują wątki dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802765"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="b49d8-103">Opcje konfiguracji czasu wykonywania dla wątków</span><span class="sxs-lookup"><span data-stu-id="b49d8-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="b49d8-104">Grupy CPU</span><span class="sxs-lookup"><span data-stu-id="b49d8-104">CPU groups</span></span>

- <span data-ttu-id="b49d8-105">Określa, czy wątki są automatycznie dystrybuowane między grupami CPU.</span><span class="sxs-lookup"><span data-stu-id="b49d8-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="b49d8-106">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="b49d8-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="b49d8-107">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="b49d8-107">Setting name</span></span> | <span data-ttu-id="b49d8-108">Wartości</span><span class="sxs-lookup"><span data-stu-id="b49d8-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b49d8-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b49d8-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="b49d8-110">N/D</span><span class="sxs-lookup"><span data-stu-id="b49d8-110">N/A</span></span> | <span data-ttu-id="b49d8-111">N/D</span><span class="sxs-lookup"><span data-stu-id="b49d8-111">N/A</span></span> |
| <span data-ttu-id="b49d8-112">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="b49d8-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="b49d8-113">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="b49d8-113">`0` - disabled</span></span><br/><span data-ttu-id="b49d8-114">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="b49d8-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="b49d8-115">Minimalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="b49d8-115">Minimum threads</span></span>

- <span data-ttu-id="b49d8-116">Określa minimalną liczbę wątków puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="b49d8-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="b49d8-117">Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b49d8-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="b49d8-118">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="b49d8-118">Setting name</span></span> | <span data-ttu-id="b49d8-119">Wartości</span><span class="sxs-lookup"><span data-stu-id="b49d8-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b49d8-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b49d8-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="b49d8-121">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="b49d8-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="b49d8-122">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="b49d8-122">**Environment variable**</span></span> | <span data-ttu-id="b49d8-123">N/D</span><span class="sxs-lookup"><span data-stu-id="b49d8-123">N/A</span></span> | <span data-ttu-id="b49d8-124">N/D</span><span class="sxs-lookup"><span data-stu-id="b49d8-124">N/A</span></span> |

## <a name="maximum-threads"></a><span data-ttu-id="b49d8-125">Maksymalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="b49d8-125">Maximum threads</span></span>

- <span data-ttu-id="b49d8-126">Określa maksymalną liczbę wątków puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="b49d8-126">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="b49d8-127">Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b49d8-127">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="b49d8-128">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="b49d8-128">Setting name</span></span> | <span data-ttu-id="b49d8-129">Wartości</span><span class="sxs-lookup"><span data-stu-id="b49d8-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b49d8-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b49d8-130">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="b49d8-131">Liczba całkowita, która reprezentuje maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="b49d8-131">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="b49d8-132">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="b49d8-132">**Environment variable**</span></span> | <span data-ttu-id="b49d8-133">N/D</span><span class="sxs-lookup"><span data-stu-id="b49d8-133">N/A</span></span> | <span data-ttu-id="b49d8-134">N/D</span><span class="sxs-lookup"><span data-stu-id="b49d8-134">N/A</span></span> |
