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
# <a name="run-time-configuration-options-for-threading"></a>Opcje konfiguracji czasu wykonywania dla wątków

## <a name="cpu-groups"></a>Grupy CPU

- Określa, czy wątki są automatycznie dystrybuowane między grupami CPU.
- W przypadku pominięcia tego ustawienia wątki nie są dystrybuowane między grupami CPU. Jest to równoznaczne z ustawieniem wartości `0` .

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_Thread_UseAllCpuGroups` | `0`-wyłączone<br/>`1`-włączone |

## <a name="minimum-threads"></a>Minimalna liczba wątków

- Określa minimalną liczbę wątków dla puli wątków roboczych.
- Odpowiada <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> metodzie.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Liczba całkowita reprezentująca minimalną liczbę wątków |
| **Właściwość programu MSBuild** | `ThreadPoolMinThreads` | Liczba całkowita reprezentująca minimalną liczbę wątków |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

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

- Określa maksymalną liczbę wątków dla puli wątków roboczych.
- Odpowiada <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> metodzie.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Liczba całkowita, która reprezentuje maksymalną liczbę wątków |
| **Właściwość programu MSBuild** | `ThreadPoolMaxThreads` | Liczba całkowita, która reprezentuje maksymalną liczbę wątków |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

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
