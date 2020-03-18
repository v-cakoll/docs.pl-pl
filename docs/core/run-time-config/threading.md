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
# <a name="run-time-configuration-options-for-threading"></a>Opcje konfiguracji w czasie wykonywania dla gwintowania

## <a name="cpu-groups"></a>Grupy procesorów

- Konfiguruje, czy wątki są automatycznie rozdzielane między grupami procesora CPU.
- Domyślnie: Wyłączone`0`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_Thread_UseAllCpuGroups` | `0`- wyłączone<br/>`1`- włączona |

## <a name="minimum-threads"></a>Minimalne wątki

- Określa minimalną liczbę wątków dla puli wątków roboczych.
- Odpowiada metodzie. <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MinThreads` | Liczba całkowita reprezentująca minimalną liczbę wątków |
| **MSBuild, właściwość** | `ThreadPoolMinThreads` | Liczba całkowita reprezentująca minimalną liczbę wątków |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

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
- Odpowiada metodzie. <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MaxThreads` | Liczba całkowita reprezentująca maksymalną liczbę wątków |
| **MSBuild, właściwość** | `ThreadPoolMaxThreads` | Liczba całkowita reprezentująca maksymalną liczbę wątków |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

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
