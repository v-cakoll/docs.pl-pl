---
title: Ustawienia konfiguracji kompilacji
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802821"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="217cc-103">Opcje konfiguracji czasu wykonywania dla kompilacji</span><span class="sxs-lookup"><span data-stu-id="217cc-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="217cc-104">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="217cc-104">Tiered compilation</span></span>

- <span data-ttu-id="217cc-105">Określa, czy kompilator JIT używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="217cc-105">Configures whether the JIT compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>
- <span data-ttu-id="217cc-106">W programie .NET Core 3,0 i nowszych kompilacja warstwowa jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="217cc-106">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="217cc-107">W przypadku oprogramowania .NET Core 2,1 i 2,2 kompilacja warstwowa jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="217cc-107">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>

| | <span data-ttu-id="217cc-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="217cc-108">Setting name</span></span> | <span data-ttu-id="217cc-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="217cc-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="217cc-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="217cc-110">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="217cc-111">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="217cc-111">`true` - enabled</span></span><br/><span data-ttu-id="217cc-112">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="217cc-112">`false` - disabled</span></span> |
| <span data-ttu-id="217cc-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="217cc-113">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="217cc-114">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="217cc-114">`1` - enabled</span></span><br/><span data-ttu-id="217cc-115">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="217cc-115">`0` - disabled</span></span> |
