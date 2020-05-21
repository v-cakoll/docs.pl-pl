---
title: Debugowanie ustawień konfiguracji profilowania
description: Informacje o ustawieniach czasu wykonywania, które konfigurują debugowanie i profilowanie dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761996"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Opcje konfiguracji czasu wykonywania na potrzeby debugowania i profilowania

## <a name="enable-diagnostics"></a>Włączanie diagnostyki

- Określa, czy debuger, profiler i Diagnostyka EventPipe są włączone lub wyłączone.
- W przypadku pominięcia tego ustawienia Diagnostyka zostanie włączona. Jest to równoznaczne z ustawieniem wartości `1` .

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_EnableDiagnostics` | `1`-włączone<br/>`0`-wyłączone |

## <a name="enable-profiling"></a>Włącz profilowanie

- Określa, czy profilowanie jest włączone dla aktualnie uruchomionego procesu.
- Jeśli pominięto to ustawienie, profilowanie jest wyłączone. Jest to równoznaczne z ustawieniem wartości `0` .

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `CORECLR_ENABLE_PROFILING` | `0`-wyłączone<br/>`1`-włączone |

## <a name="profiler-guid"></a>Identyfikator GUID profilera

- Określa identyfikator GUID profilera do załadowania do aktualnie uruchomionego procesu.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | Nie dotyczy | Nie dotyczy |
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
- Jeśli pominięto to ustawienie, zapisanie mapy wydajności jest wyłączone. Jest to równoznaczne z ustawieniem wartości `0` .

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_PerfMapEnabled` | `0`-wyłączone<br/>`1`-włączone |

## <a name="perf-log-markers"></a>Znaczniki dzienników wydajności

- Włącza lub wyłącza określony sygnał, który ma zostać zaakceptowany i zignorowany jako znacznik w dziennikach wydajności.
- W przypadku pominięcia tego ustawienia określony sygnał nie zostanie zignorowany. Jest to równoznaczne z ustawieniem wartości `0` .

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_PerfMapIgnoreSignal` | `0`-wyłączone<br/>`1`-włączone |

> [!NOTE]
> To ustawienie jest ignorowane, jeśli [COMPlus_PerfMapEnabled](#write-perf-map) jest pominięte lub ustawione na `0` (czyli wyłączone).
