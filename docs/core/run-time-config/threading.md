---
title: Ustawienia konfiguracji wątkowości
description: Informacje na temat ustawień czasu wykonywania, które konfigurują wątki dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789854"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="c9c1c-103">Opcje konfiguracji czasu wykonywania dla wątków</span><span class="sxs-lookup"><span data-stu-id="c9c1c-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="c9c1c-104">Grupy CPU</span><span class="sxs-lookup"><span data-stu-id="c9c1c-104">CPU groups</span></span>

- <span data-ttu-id="c9c1c-105">Określa, czy wątki są automatycznie dystrybuowane między grupami CPU.</span><span class="sxs-lookup"><span data-stu-id="c9c1c-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="c9c1c-106">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="c9c1c-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="c9c1c-107">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="c9c1c-107">Setting name</span></span> | <span data-ttu-id="c9c1c-108">Wartości</span><span class="sxs-lookup"><span data-stu-id="c9c1c-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c9c1c-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="c9c1c-110">N/D</span><span class="sxs-lookup"><span data-stu-id="c9c1c-110">N/A</span></span> | <span data-ttu-id="c9c1c-111">N/D</span><span class="sxs-lookup"><span data-stu-id="c9c1c-111">N/A</span></span> |
| <span data-ttu-id="c9c1c-112">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="c9c1c-113">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="c9c1c-113">`0` - disabled</span></span><br/><span data-ttu-id="c9c1c-114">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="c9c1c-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="c9c1c-115">Minimalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="c9c1c-115">Minimum threads</span></span>

- <span data-ttu-id="c9c1c-116">Określa minimalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="c9c1c-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="c9c1c-117">Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9c1c-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="c9c1c-118">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="c9c1c-118">Setting name</span></span> | <span data-ttu-id="c9c1c-119">Wartości</span><span class="sxs-lookup"><span data-stu-id="c9c1c-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c9c1c-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="c9c1c-121">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="c9c1c-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="c9c1c-122">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="c9c1c-123">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="c9c1c-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="c9c1c-124">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-124">**Environment variable**</span></span> | <span data-ttu-id="c9c1c-125">N/D</span><span class="sxs-lookup"><span data-stu-id="c9c1c-125">N/A</span></span> | <span data-ttu-id="c9c1c-126">N/D</span><span class="sxs-lookup"><span data-stu-id="c9c1c-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="c9c1c-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c9c1c-127">Examples</span></span>

<span data-ttu-id="c9c1c-128">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="c9c1c-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="c9c1c-129">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="c9c1c-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="c9c1c-130">Maksymalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="c9c1c-130">Maximum threads</span></span>

- <span data-ttu-id="c9c1c-131">Określa maksymalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="c9c1c-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="c9c1c-132">Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9c1c-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="c9c1c-133">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="c9c1c-133">Setting name</span></span> | <span data-ttu-id="c9c1c-134">Wartości</span><span class="sxs-lookup"><span data-stu-id="c9c1c-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c9c1c-135">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="c9c1c-136">Liczba całkowita, która reprezentuje maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="c9c1c-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="c9c1c-137">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="c9c1c-138">Liczba całkowita, która reprezentuje maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="c9c1c-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="c9c1c-139">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="c9c1c-139">**Environment variable**</span></span> | <span data-ttu-id="c9c1c-140">N/D</span><span class="sxs-lookup"><span data-stu-id="c9c1c-140">N/A</span></span> | <span data-ttu-id="c9c1c-141">N/D</span><span class="sxs-lookup"><span data-stu-id="c9c1c-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="c9c1c-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c9c1c-142">Examples</span></span>

<span data-ttu-id="c9c1c-143">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="c9c1c-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="c9c1c-144">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="c9c1c-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
