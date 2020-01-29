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
| **Właściwość programu MSBuild** | `ThreadPoolMinThreads` | Liczba całkowita reprezentująca minimalną liczbę wątków |
| **Zmienna środowiskowa** | N/D | N/D |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a>Maksymalna liczba wątków

- Określa maksymalną liczbę wątków puli wątków roboczych.
- Odpowiada metodzie <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Liczba całkowita, która reprezentuje maksymalną liczbę wątków |
| **Właściwość programu MSBuild** | `ThreadPoolMaxThreads` | Liczba całkowita, która reprezentuje maksymalną liczbę wątków |
| **Zmienna środowiskowa** | N/D | N/D |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
