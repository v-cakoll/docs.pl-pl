---
title: Ustawienia konfiguracji wątkowości
description: Informacje na temat ustawień czasu wykonywania, które konfigurują wątki dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761931"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="2314c-103">Opcje konfiguracji czasu wykonywania dla wątków</span><span class="sxs-lookup"><span data-stu-id="2314c-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="2314c-104">Grupy CPU</span><span class="sxs-lookup"><span data-stu-id="2314c-104">CPU groups</span></span>

- <span data-ttu-id="2314c-105">Określa, czy wątki są automatycznie dystrybuowane między grupami CPU.</span><span class="sxs-lookup"><span data-stu-id="2314c-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="2314c-106">W przypadku pominięcia tego ustawienia wątki nie są dystrybuowane między grupami CPU.</span><span class="sxs-lookup"><span data-stu-id="2314c-106">If you omit this setting, threads are not distributed across CPU groups.</span></span> <span data-ttu-id="2314c-107">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="2314c-107">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="2314c-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2314c-108">Setting name</span></span> | <span data-ttu-id="2314c-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="2314c-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2314c-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2314c-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="2314c-111">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="2314c-111">N/A</span></span> | <span data-ttu-id="2314c-112">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="2314c-112">N/A</span></span> |
| <span data-ttu-id="2314c-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2314c-113">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="2314c-114">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="2314c-114">`0` - disabled</span></span><br/><span data-ttu-id="2314c-115">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="2314c-115">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="2314c-116">Minimalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="2314c-116">Minimum threads</span></span>

- <span data-ttu-id="2314c-117">Określa minimalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="2314c-117">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="2314c-118">Odpowiada <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> metodzie.</span><span class="sxs-lookup"><span data-stu-id="2314c-118">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="2314c-119">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2314c-119">Setting name</span></span> | <span data-ttu-id="2314c-120">Wartości</span><span class="sxs-lookup"><span data-stu-id="2314c-120">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2314c-121">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2314c-121">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="2314c-122">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="2314c-122">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="2314c-123">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="2314c-123">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="2314c-124">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="2314c-124">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="2314c-125">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2314c-125">**Environment variable**</span></span> | <span data-ttu-id="2314c-126">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="2314c-126">N/A</span></span> | <span data-ttu-id="2314c-127">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="2314c-127">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="2314c-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2314c-128">Examples</span></span>

<span data-ttu-id="2314c-129">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="2314c-129">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="2314c-130">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="2314c-130">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="2314c-131">Maksymalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="2314c-131">Maximum threads</span></span>

- <span data-ttu-id="2314c-132">Określa maksymalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="2314c-132">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="2314c-133">Odpowiada <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> metodzie.</span><span class="sxs-lookup"><span data-stu-id="2314c-133">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="2314c-134">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2314c-134">Setting name</span></span> | <span data-ttu-id="2314c-135">Wartości</span><span class="sxs-lookup"><span data-stu-id="2314c-135">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2314c-136">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2314c-136">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="2314c-137">Liczba całkowita, która reprezentuje maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="2314c-137">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="2314c-138">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="2314c-138">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="2314c-139">Liczba całkowita, która reprezentuje maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="2314c-139">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="2314c-140">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2314c-140">**Environment variable**</span></span> | <span data-ttu-id="2314c-141">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="2314c-141">N/A</span></span> | <span data-ttu-id="2314c-142">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="2314c-142">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="2314c-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2314c-143">Examples</span></span>

<span data-ttu-id="2314c-144">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="2314c-144">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="2314c-145">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="2314c-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
