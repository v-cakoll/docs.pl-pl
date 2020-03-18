---
title: Debugowanie ustawień konfiguracji profilowania
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują debugowanie i profilowanie aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802800"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Opcje konfiguracji w czasie wykonywania do debugowania i profilowania

## <a name="enable-diagnostics"></a>Włączanie diagnostyki

- Konfiguruje, czy debuger, profiler i diagnostyka EventPipe są włączone lub wyłączone.
- Domyślnie: Włączone`1`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_EnableDiagnostics` | `1`- włączona<br/>`0`- wyłączone |

## <a name="enable-profiling"></a>Włącz profilowanie

- Konfiguruje, czy profilowanie jest włączone dla aktualnie uruchomionego procesu.
- Domyślnie: Wyłączone`0`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `CORECLR_ENABLE_PROFILING` | `0`- wyłączone<br/>`1`- włączona |

## <a name="profiler-guid"></a>Identyfikator GUID profilera

- Określa identyfikator GUID profilera do załadowania do aktualnie uruchomionego procesu.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `CORECLR_PROFILER` | *string-guid* |

## <a name="profiler-location"></a>Lokalizacja profilera

- Określa ścieżkę do dll profilera, aby załadować do aktualnie uruchomionego procesu (lub procesu 32-bitowego lub 64-bitowego).
- Jeśli ustawiono więcej niż jedną zmienną, pierwszeństwo mają zmienne specyficzne dla bitness. Określają one, która bitność profilera do załadowania.
- Aby uzyskać więcej informacji, zobacz [Znajdowanie biblioteki profilerów](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **Zmienna środowiskowa** | `CORECLR_PROFILER_PATH` | *ścieżka ciągów* |
| **Zmienna środowiskowa** | `CORECLR_PROFILER_PATH_32` | *ścieżka ciągów* |
| **Zmienna środowiskowa** | `CORECLR_PROFILER_PATH_64` | *ścieżka ciągów* |

## <a name="write-perf-map"></a>Napisz mapę perf

- Włącza lub wyłącza zapisywanie */tmp/perf-$pid.map* w systemach Linux.
- Domyślnie: Wyłączone`0`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_PerfMapEnabled` | `0`- wyłączone<br/>`1`- włączona |

## <a name="perf-log-markers"></a>Znaczniki dziennika Perf

- Gdy `COMPlus_PerfMapEnabled` jest `1`ustawiona na , włącza lub wyłącza określony sygnał, który ma być akceptowany i ignorowany jako znacznik w dziennikach perf.
- Domyślnie: Wyłączone`0`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_PerfMapIgnoreSignal` | `0`- wyłączone<br/>`1`- włączona |
