---
title: Ustawienia konfiguracji wątkowości
description: Informacje na temat ustawień czasu wykonywania, które konfigurują wątki dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733434"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="99111-103">Opcje konfiguracji czasu wykonywania dla wątków</span><span class="sxs-lookup"><span data-stu-id="99111-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="99111-104">Grupy CPU</span><span class="sxs-lookup"><span data-stu-id="99111-104">CPU groups</span></span>

- <span data-ttu-id="99111-105">Określa, czy wątki są automatycznie dystrybuowane między grupami CPU.</span><span class="sxs-lookup"><span data-stu-id="99111-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="99111-106">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="99111-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="99111-107">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="99111-107">Setting name</span></span> | <span data-ttu-id="99111-108">Wartości</span><span class="sxs-lookup"><span data-stu-id="99111-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99111-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="99111-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="99111-110">N/D</span><span class="sxs-lookup"><span data-stu-id="99111-110">N/A</span></span> | <span data-ttu-id="99111-111">N/D</span><span class="sxs-lookup"><span data-stu-id="99111-111">N/A</span></span> |
| <span data-ttu-id="99111-112">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="99111-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="99111-113">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="99111-113">`0` - disabled</span></span><br/><span data-ttu-id="99111-114">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="99111-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="99111-115">Minimalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="99111-115">Minimum threads</span></span>

- <span data-ttu-id="99111-116">Określa minimalną liczbę wątków puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="99111-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="99111-117">Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99111-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="99111-118">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="99111-118">Setting name</span></span> | <span data-ttu-id="99111-119">Wartości</span><span class="sxs-lookup"><span data-stu-id="99111-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99111-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="99111-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="99111-121">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="99111-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="99111-122">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="99111-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="99111-123">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="99111-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="99111-124">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="99111-124">**Environment variable**</span></span> | <span data-ttu-id="99111-125">N/D</span><span class="sxs-lookup"><span data-stu-id="99111-125">N/A</span></span> | <span data-ttu-id="99111-126">N/D</span><span class="sxs-lookup"><span data-stu-id="99111-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="99111-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="99111-127">Examples</span></span>

<span data-ttu-id="99111-128">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="99111-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="99111-129">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="99111-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="99111-130">Maksymalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="99111-130">Maximum threads</span></span>

- <span data-ttu-id="99111-131">Określa maksymalną liczbę wątków puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="99111-131">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="99111-132">Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99111-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="99111-133">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="99111-133">Setting name</span></span> | <span data-ttu-id="99111-134">Wartości</span><span class="sxs-lookup"><span data-stu-id="99111-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99111-135">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="99111-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="99111-136">Liczba całkowita, która reprezentuje maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="99111-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="99111-137">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="99111-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="99111-138">Liczba całkowita, która reprezentuje maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="99111-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="99111-139">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="99111-139">**Environment variable**</span></span> | <span data-ttu-id="99111-140">N/D</span><span class="sxs-lookup"><span data-stu-id="99111-140">N/A</span></span> | <span data-ttu-id="99111-141">N/D</span><span class="sxs-lookup"><span data-stu-id="99111-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="99111-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="99111-142">Examples</span></span>

<span data-ttu-id="99111-143">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="99111-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="99111-144">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="99111-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
