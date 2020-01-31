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
# <a name="run-time-configuration-options-for-threading"></a>Opcje konfiguracji czasu wykonywania dla wątków

## <a name="cpu-groups"></a>Grupy CPU

- Określa, czy wątki są automatycznie dystrybuowane między grupami CPU.
- Domyślnie: wyłączone (`0`).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_Thread_UseAllCpuGroups` | `0` — wyłączone<br/>`1` — włączono |

## <a name="minimum-threads"></a>Minimalna liczba wątków

- Określa minimalną liczbę wątków dla puli wątków roboczych.
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

- Określa maksymalną liczbę wątków dla puli wątków roboczych.
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
