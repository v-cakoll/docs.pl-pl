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
# <a name="run-time-configuration-options-for-compilation"></a>Opcje konfiguracji czasu wykonywania dla kompilacji

## <a name="tiered-compilation"></a>Kompilacja warstwowa

- Określa, czy kompilator JIT używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).
- W programie .NET Core 3,0 i nowszych kompilacja warstwowa jest domyślnie włączona.
- W przypadku oprogramowania .NET Core 2,1 i 2,2 kompilacja warstwowa jest domyślnie wyłączona.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true` — włączono<br/>`false` — wyłączone |
| **Zmienna środowiskowa** | `COMPlus_TieredCompilation` | `1` — włączono<br/>`0` — wyłączone |
