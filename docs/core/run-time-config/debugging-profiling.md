---
title: Debugowanie ustawień konfiguracji profilowania
description: Informacje o ustawieniach czasu wykonywania, które konfigurują debugowanie i profilowanie dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802800"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Opcje konfiguracji czasu wykonywania na potrzeby debugowania i profilowania

## <a name="enable-diagnostics"></a>Włączanie diagnostyki

- Określa, czy debuger, profiler i Diagnostyka EventPipe są włączone lub wyłączone.
- Wartość domyślna: włączone (`1`).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_EnableDiagnostics` | `1` — włączono<br/>`0` — wyłączone |

## <a name="enable-profiling"></a>Włącz profilowanie

- Określa, czy profilowanie jest włączone dla aktualnie uruchomionego procesu.
- Domyślnie: wyłączone (`0`).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Zmienna środowiskowa** | `CORECLR_ENABLE_PROFILING` | `0` — wyłączone<br/>`1` — włączono |

## <a name="profiler-guid"></a>Identyfikator GUID profilera

- Określa identyfikator GUID profilera do załadowania do aktualnie uruchomionego procesu.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Zmienna środowiskowa** | `CORECLR_PROFILER` | *ciąg — identyfikator GUID* |

## <a name="profiler-location"></a>Lokalizacja profilera

- Określa ścieżkę do pliku DLL profilera do załadowania do aktualnie uruchomionego procesu (lub 32-bitowego lub 64-bitowego procesu).
- Jeśli ustawiono więcej niż jedną zmienną, pierwszeństwo mają zmienne specyficzne dla bitów. Określają, która liczba bitów profilera ma zostać załadowana.
- Aby uzyskać więcej informacji, zobacz [Znajdowanie biblioteki profilera](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **Zmienna środowiskowa** | `CORECLR_PROFILER_PATH` | *ścieżka ciągu* |
| **Zmienna środowiskowa** | `CORECLR_PROFILER_PATH_32` | *ścieżka ciągu* |
| **Zmienna środowiskowa** | `CORECLR_PROFILER_PATH_64` | *ścieżka ciągu* |

## <a name="write-perf-map"></a>Zapisz mapę wydajności

- Włącza lub wyłącza zapisywanie */tmp/perf-$PID. map* w systemach Linux.
- Domyślnie: wyłączone (`0`).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_PerfMapEnabled` | `0` — wyłączone<br/>`1` — włączono |

## <a name="perf-log-markers"></a>Znaczniki dzienników wydajności

- Gdy `COMPlus_PerfMapEnabled` jest ustawiona na `1`, włącza lub wyłącza określony sygnał, który ma być akceptowany i ignorowany jako znacznik w dziennikach wydajności.
- Domyślnie: wyłączone (`0`).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_PerfMapIgnoreSignal` | `0` — wyłączone<br/>`1` — włączono |
