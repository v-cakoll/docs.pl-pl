---
title: Ustawienia konfiguracji wątków
description: Dowiedz się więcej o ustawieniach w czasie wykonywania, które konfigurują wątki dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789854"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="aa78d-103">Opcje konfiguracji w czasie wykonywania dla gwintowania</span><span class="sxs-lookup"><span data-stu-id="aa78d-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="aa78d-104">Grupy procesorów</span><span class="sxs-lookup"><span data-stu-id="aa78d-104">CPU groups</span></span>

- <span data-ttu-id="aa78d-105">Konfiguruje, czy wątki są automatycznie rozdzielane między grupami procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="aa78d-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="aa78d-106">Domyślnie: Wyłączone`0`( ).</span><span class="sxs-lookup"><span data-stu-id="aa78d-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="aa78d-107">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="aa78d-107">Setting name</span></span> | <span data-ttu-id="aa78d-108">Wartości</span><span class="sxs-lookup"><span data-stu-id="aa78d-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa78d-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa78d-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="aa78d-110">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="aa78d-110">N/A</span></span> | <span data-ttu-id="aa78d-111">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="aa78d-111">N/A</span></span> |
| <span data-ttu-id="aa78d-112">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="aa78d-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="aa78d-113">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="aa78d-113">`0` - disabled</span></span><br/><span data-ttu-id="aa78d-114">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="aa78d-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="aa78d-115">Minimalne wątki</span><span class="sxs-lookup"><span data-stu-id="aa78d-115">Minimum threads</span></span>

- <span data-ttu-id="aa78d-116">Określa minimalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="aa78d-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="aa78d-117">Odpowiada metodzie. <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="aa78d-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="aa78d-118">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="aa78d-118">Setting name</span></span> | <span data-ttu-id="aa78d-119">Wartości</span><span class="sxs-lookup"><span data-stu-id="aa78d-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa78d-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa78d-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="aa78d-121">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="aa78d-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="aa78d-122">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="aa78d-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="aa78d-123">Liczba całkowita reprezentująca minimalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="aa78d-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="aa78d-124">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="aa78d-124">**Environment variable**</span></span> | <span data-ttu-id="aa78d-125">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="aa78d-125">N/A</span></span> | <span data-ttu-id="aa78d-126">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="aa78d-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="aa78d-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="aa78d-127">Examples</span></span>

<span data-ttu-id="aa78d-128">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="aa78d-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="aa78d-129">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="aa78d-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="aa78d-130">Maksymalna liczba wątków</span><span class="sxs-lookup"><span data-stu-id="aa78d-130">Maximum threads</span></span>

- <span data-ttu-id="aa78d-131">Określa maksymalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="aa78d-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="aa78d-132">Odpowiada metodzie. <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="aa78d-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="aa78d-133">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="aa78d-133">Setting name</span></span> | <span data-ttu-id="aa78d-134">Wartości</span><span class="sxs-lookup"><span data-stu-id="aa78d-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa78d-135">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa78d-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="aa78d-136">Liczba całkowita reprezentująca maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="aa78d-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="aa78d-137">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="aa78d-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="aa78d-138">Liczba całkowita reprezentująca maksymalną liczbę wątków</span><span class="sxs-lookup"><span data-stu-id="aa78d-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="aa78d-139">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="aa78d-139">**Environment variable**</span></span> | <span data-ttu-id="aa78d-140">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="aa78d-140">N/A</span></span> | <span data-ttu-id="aa78d-141">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="aa78d-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="aa78d-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="aa78d-142">Examples</span></span>

<span data-ttu-id="aa78d-143">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="aa78d-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="aa78d-144">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="aa78d-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
