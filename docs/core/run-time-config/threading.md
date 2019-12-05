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
# <a name="run-time-configuration-options-for-threading"></a>Opcje konfiguracji czasu wykonywania dla wątków

## <a name="cpu-groups"></a>Grupy CPU

- Określa, czy wątki są automatycznie dystrybuowane między grupami CPU.
- Domyślnie: wyłączone (`0`).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_Thread_UseAllCpuGroups` | `0` — wyłączone<br/>`1` — włączono |

## <a name="minimum-threads"></a>Minimalna liczba wątków

- Określa minimalną liczbę wątków puli wątków roboczych.
- Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Liczba całkowita reprezentująca minimalną liczbę wątków |
| **Zmienna środowiskowa** | N/D | N/D |

## <a name="maximum-threads"></a>Maksymalna liczba wątków

- Określa maksymalną liczbę wątków puli wątków roboczych.
- Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Liczba całkowita, która reprezentuje maksymalną liczbę wątków |
| **Zmienna środowiskowa** | N/D | N/D |
