---
title: Ustawienia konfiguracji modułu zbierającego elementy bezużyteczne
description: Dowiedz się więcej o ustawieniach czasu wykonywania do konfigurowania sposobu zarządzania pamięcią przez moduł zbierający elementy bezużyteczne dla aplikacji .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733518"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Opcje konfiguracji w czasie wykonywania dla wyrzucania elementów bezużytecznych

Ta strona zawiera informacje o ustawieniach modułu odśmiecania pamięci (GC), które można zmienić w czasie wykonywania. Jeśli próbujesz osiągnąć najwyższą wydajność uruchomionej aplikacji, rozważ użycie tych ustawień. Jednak wartości domyślne zapewniają optymalną wydajność dla większości aplikacji w typowych sytuacjach.

Ustawienia są rozmieszczone w grupach na tej stronie. Ustawienia w każdej grupie są powszechnie używane w połączeniu ze sobą w celu osiągnięcia określonego wyniku.

> [!NOTE]
>
> - Te ustawienia mogą być również zmieniane dynamicznie przez aplikację, ponieważ jest uruchomiona, więc wszystkie ustawienia czasu wykonywania, które ustawisz, mogą zostać zastąpione.
> - Niektóre ustawienia, takie jak [poziom opóźnienia,](../../standard/garbage-collection/latency.md)są zazwyczaj ustawiane tylko za pośrednictwem interfejsu API w czasie projektowania. Takie ustawienia są pomijane na tej stronie.
> - W przypadku wartości liczbowych należy użyć notacji dziesiętnej dla ustawień w pliku *runtimeconfig.json* i notacji szesnastkowej dla ustawień zmiennej środowiskowej. W przypadku wartości szesnastkowych można określić je z prefiksem "0x" lub bez nich.

## <a name="flavors-of-garbage-collection"></a>Smaki wyrzucania elementów bezużytecznych

Dwa główne smaki wyrzucania elementów bezużytecznych to stacja robocza GC i gc serwera. Aby uzyskać więcej informacji na temat różnic między tymi dwoma, zobacz [podstawy wyrzucania elementów bezużytecznych](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Podsmaki wyrzucania elementów bezużytecznych są tła i nierównoczesnych.

Użyj następujących ustawień, aby wybrać smaki wyrzucania elementów bezużytecznych:

### <a name="systemgcservercomplus_gcserver"></a>System.GC.Serwer/COMPlus_gcServer

- Określa, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej, czy wyrzucania elementów bezużytecznych serwera.
- Domyślnie: Wyrzucanie elementów`false`bezużytecznych stacji roboczej ( ).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false`- stacja robocza<br/>`true`- serwer | .NET Core 1.0 |
| **MSBuild, właściwość** | `ServerGarbageCollection` | `false`- stacja robocza<br/>`true`- serwer | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_gcServer` | `0`- stacja robocza<br/>`1`- serwer | .NET Core 1.0 |
| **App.config dla platformy .NET Framework** | [Serwer GC](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`- stacja robocza<br/>`true`- serwer |  |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.GC.Jednobieżny/COMPlus_gcConcurrent

- Konfiguruje, czy w tle (równoczesne) wyrzucanie elementów bezużytecznych jest włączone.
- Domyślnie: Włączone`true`( ).
- Aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych w tle](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) i [wyrzucanie elementów bezużytecznych serwera w tle](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true`- tło GC<br/>`false`- niewspółbieżny GC | .NET Core 1.0 |
| **MSBuild, właściwość** | `ConcurrentGarbageCollection` | `true`- tło GC<br/>`false`- niewspółbieżny GC | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_gcConcurrent` | `true`- tło GC<br/>`false`- niewspółbieżny GC | .NET Core 1.0 |
| **App.config dla platformy .NET Framework** | [gcPrąd jednobieżny](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`- tło GC<br/>`false`- niewspółbieżny GC |  |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>Zarządzanie zużyciem zasobów

Użyj ustawień opisanych w tej sekcji, aby zarządzać pamięcimodułu modułu zbierającego elementy bezużyteczne.

Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zobacz [środkowy grunt między stacją roboczą a wpisem](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu GC serwera.

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System.GC.HeapCount/COMPlus_GCHeapCount

- Ogranicza liczbę stert utworzonych przez moduł zbierający elementy bezużyteczne.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Jeśli koligacja procesora GC jest włączona, co jest ustawieniem domyślnym, ustawienie liczby sterty animuje sterty/wątki `n` GC do pierwszych `n` procesorów. (Użyj ustawienia maski afinitizu lub affinitize zakresów, aby dokładnie określić, które procesory mają się affinitize).)
- Jeśli koligacja procesora GC jest wyłączona, to ustawienie ogranicza liczbę stert GC.
- Aby uzyskać więcej informacji, zobacz [GCHeapCount uwagi](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapCount` | *wartość szesnastkowa* | .NET Core 3.0 |
| **App.config dla platformy .NET Framework** | [Liczba osób gcheap](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *wartość dziesiętna* | .NET Framework 4.6.2 |

Przykład:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną. Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową. Na przykład, aby ograniczyć liczbę stert do 16, wartości będą wynosić 16 dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Określa dokładne procesory, które powinny używać wątków modułu odśmiecania pamięci.
- Jeśli koligacja procesora jest `System.GC.NoAffinitize` `true`wyłączona przez ustawienie , to ustawienie jest ignorowane.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Wartość jest maską bitową, która definiuje procesory, które są dostępne dla procesu. Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używasz zmiennej środowiskowej) jest 0011 1111 1111 w notacji binarnej. Określa, że ma być używanych pierwszych procesorów 10. Aby określić następne procesory 10, czyli procesory 10-19, należy określić wartość dziesiętną 1047552 (lub wartość szesnastkową 0xFFC00 lub FFC00), która jest równoważna wartości binarnej 1111 1111 1100 0000 0000.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapAffinitizeMask` | *wartość szesnastkowa* | .NET Core 3.0 |
| **App.config dla platformy .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *wartość dziesiętna* | .NET Framework 4.6.2 |

Przykład:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Określa listę procesorów do użycia dla wątków modułu odśmiecania pamięci.
- To ustawienie jest `System.GC.HeapAffinitizeMask`podobne do , z wyjątkiem pozwala określić więcej niż 64 procesorów.
- W przypadku systemów operacyjnych Windows prefiks numeru procesora lub zakresu z odpowiednią [grupą procesora](/windows/win32/procthread/processor-groups), na przykład "0:1-10,0:12,1:50-52,1:70".
- Jeśli koligacja procesora jest `System.GC.NoAffinitize` `true`wyłączona przez ustawienie , to ustawienie jest ignorowane.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora DLA GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.GCHeapAffinitizeRanges` | Oddzielona przecinkami lista numerów procesorów lub zakresów numerów procesorów.<br/>Przykład Uniksa: "1-10,12,50-52,70"<br/>Przykład systemu Windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapAffinitizeRanges` | Oddzielona przecinkami lista numerów procesorów lub zakresów numerów procesorów.<br/>Przykład Uniksa: "1-10,12,50-52,70"<br/>Przykład systemu Windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |

Przykład:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- Konfiguruje, czy moduł zbierający elementy bezużyteczne używa [grup procesora CPU,](/windows/win32/procthread/processor-groups) czy nie.

  Gdy 64-bitowy komputer z systemem Windows ma wiele grup procesora CPU, oznacza to, że istnieje więcej niż 64 procesorów, włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU. Moduł zbierający elementy bezużyteczne używa wszystkich rdzeni do tworzenia i równoważenia stert.

- Dotyczy wyrzucania elementów bezużytecznych serwera tylko w 64-bitowych systemach operacyjnych Windows.
- Domyślnie: Wyłączone`0`( ).
- Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora DLA GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_GCCpuGroup` | `0`- wyłączone<br/>`1`- włączona | .NET Core 1.0 |
| **App.config dla platformy .NET Framework** | [Grupa GCCpu](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`- wyłączone<br/>`true`- włączona |  |

> [!NOTE]
> Aby skonfigurować program CLR (Common Language runtime) do dystrybucji wątków z puli wątków we wszystkich grupach procesorów, włącz opcję [elementu Thread_UseAllCpuGroups.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) W przypadku aplikacji .NET Core tę opcję można `COMPlus_Thread_UseAllCpuGroups` włączyć, `1`ustawiając wartość zmiennej środowiskowej na .

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System.GC.NoAffinitize/COMPlus_GCNoAffinitize

- Określa, czy *affinitize* wątków wyrzucania elementów bezużytecznych z procesorów. Affinitize wątku GC oznacza, że można uruchomić tylko na jego określonego procesora CPU. Sterta jest tworzona dla każdego wątku GC.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Domyślnie: Affinitize wątków wyrzucania`false`elementów bezużytecznych z procesorów ( ).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false`- affinitize<br/>`true`- nie affinitize | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCNoAffinitize` | `0`- affinitize<br/>`1`- nie affinitize | .NET Core 3.0 |
| **App.config dla platformy .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`- affinitize<br/>`true`- nie affinitize | .NET Framework 4.6.2 |

Przykład:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit

- Określa maksymalny rozmiar zatwierdzenia w bajtach dla księgowości GC i księgowości GC.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimit` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapHardLimit` | *wartość szesnastkowa* | .NET Core 3.0 |

Przykład:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną. Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową. Na przykład, aby określić limit twardy sterty 200 mebibajtów (MiB), wartości będą 209715200 dla pliku JSON i 0xC800000 lub C800000 dla zmiennej środowiskowej.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Określa użycie sterty GC jako procent całkowitej pamięci.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPercent` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapHardLimitPercent` | *wartość szesnastkowa* | .NET Core 3.0 |

Przykład:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną. Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową. Na przykład, aby ograniczyć użycie sterty do 30%, wartości będą 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System.GC.RetainVM/COMPlus_GCRetainVM

- Określa, czy segmenty, które mają zostać usunięte, są umieszczane na liście gotowości do wykorzystania w przyszłości, czy też są zwalniane z powrotem do systemu operacyjnego(OS).
- Domyślnie: Zwalnianie segmentów z`false`powrotem do systemu operacyjnego ( ).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false`- zwolnienie do os<br/>`true`- umieścić w trybie gotowości | .NET Core 1.0 |
| **MSBuild, właściwość** | `RetainVMGarbageCollection` | `false`- zwolnienie do os<br/>`true`- umieścić w trybie gotowości | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_GCRetainVM` | `0`- zwolnienie do os<br/>`1`- umieścić w trybie gotowości | .NET Core 1.0 |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>Duże strony

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Określa, czy duże strony mają być używane, gdy ustawiono twardy limit sterty.
- Domyślnie: Wyłączone`0`( ).
- Jest to ustawienie eksperymentalne.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_GCLargePages` | `0`- wyłączone<br/>`1`- włączona | .NET Core 3.0 |

## <a name="large-objects"></a>Duże obiekty

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Konfiguruje obsługę modułów zbierających elementy bezużyteczne na platformach 64-bitowych dla macierzy o rozmiarze większym niż 2 gigabajty (GB) w całkowitym rozmiarze.
- Domyślnie: Włączone`1`( ).
- Ta opcja może stać się przestarzała w przyszłej wersji .NET.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_gcAllowVeryLargeObjects` | `1`- włączona<br/> `0`- wyłączone | .NET Core 1.0 |
| **App.config dla platformy .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`- włączona<br/> `0`- wyłączone | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Próg sterty dużych obiektów

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System.GC.LOHThreshold/COMPlus_GCLOHThreshold

- Określa rozmiar progu w bajtach, który powoduje, że obiekty są na stercie dużych obiektów (LOH).
- Domyślny próg to 85 000 bajtów.
- Określona wartość musi być większa niż próg domyślny.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | *wartość dziesiętna* | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_GCLOHThreshold` | *wartość szesnastkowa* | .NET Core 1.0 |
| **App.config dla platformy .NET Framework** | [Próg GCLOH](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *wartość dziesiętna* |  .NET Framework 4.8 |

Przykład:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną. Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową. Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości będą wynosić 120000 dla pliku JSON i 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.

## <a name="standalone-gc"></a>Samodzielny GC

### <a name="complus_gcname"></a>COMPlus_GCName

- Określa ścieżkę do biblioteki zawierającej moduł odśmiecania pamięci, który program runtime zamierza załadować.
- Aby uzyskać więcej informacji, zobacz [Samodzielny projekt modułu ładującego GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
