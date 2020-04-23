---
title: Ustawienia konfiguracji modułu zbierającego elementy bezużyteczne
description: Dowiedz się więcej o ustawieniach czasu wykonywania konfigurowania sposobu zarządzania pamięcią dla aplikacji .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: ec575bdd17c8a7c290673b7085074bbba94cedef
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102869"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Opcje konfiguracji w czasie wykonywania wyrzucania elementów bezużytecznych

Ta strona zawiera informacje o ustawieniach modułu zbierającego elementy bezużyteczne (GC), które można zmienić w czasie wykonywania. Jeśli próbujesz osiągnąć maksymalną wydajność uruchomionej aplikacji, rozważ użycie tych ustawień. Jednak wartości domyślne zapewniają optymalną wydajność dla większości aplikacji w typowych sytuacjach.

Ustawienia są podzielone na grupy na tej stronie. Ustawienia w każdej grupie są powszechnie używane w połączeniu ze sobą w celu osiągnięcia określonego wyniku.

> [!NOTE]
>
> - Te ustawienia mogą być również zmieniane dynamicznie przez aplikację, ponieważ jest uruchomiona, więc wszystkie ustawienia czasu wykonywania, które można ustawić, mogą zostać zastąpione.
> - Niektóre ustawienia, takie jak [poziom opóźnienia,](../../standard/garbage-collection/latency.md)są zazwyczaj ustawiane tylko za pośrednictwem interfejsu API w czasie projektowania. Takie ustawienia są pomijane na tej stronie.
> - W przypadku wartości liczbowych należy użyć notacji dziesiętnej dla ustawień w pliku *runtimeconfig.json* i notacji szesnastowej dla ustawień zmiennych środowiskowych. Dla wartości szesnastkowych można je określić z prefiksem "0x" lub bez niego.

## <a name="flavors-of-garbage-collection"></a>Smaki wyrzucania elementów bezużytecznych

Dwa główne smaki wyrzucania elementów bezużytecznych są gc stacji roboczej i serwera GC. Aby uzyskać więcej informacji na temat różnic między nimi, zobacz [Stacja robocza i wyrzucanie elementów bezużytecznych serwera](../../standard/garbage-collection/workstation-server-gc.md).

Podpochrozumia wyrzucania elementów bezużytecznych są tła i nie jednobieżne.

Użyj następujących ustawień, aby wybrać smaki wyrzucania elementów bezużytecznych:

### <a name="systemgcservercomplus_gcserver"></a>System.GC.Serwer/COMPlus_gcServer

- Konfiguruje, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej lub modułu wyrzucania elementów bezużytecznych serwera.
- Domyślnie: Wyrzucanie`false`elementów bezużytecznych na stacji roboczej ( ).

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false`- stacja robocza<br/>`true`- serwer | .NET Rdzeń 1.0 |
| **Właściwość MSBuild** | `ServerGarbageCollection` | `false`- stacja robocza<br/>`true`- serwer | .NET Rdzeń 1.0 |
| **Zmienna środowiskowa** | `COMPlus_gcServer` | `0`- stacja robocza<br/>`1`- serwer | .NET Rdzeń 1.0 |
| **app.config dla programu .NET Framework** | [Serwer GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`- stacja robocza<br/>`true`- serwer |  |

### <a name="examples"></a>Przykłady

*runtimeconfig.json:*

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

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.GC.Równoczesne/COMPlus_gcConcurrent

- Konfiguruje, czy tło (równoczesnych) wyrzucanie elementów bezużytecznych jest włączone.
- Domyślnie: Włączone`true`( ).
- Aby uzyskać więcej informacji, zobacz [Tło wyrzucania elementów bezużytecznych](../../standard/garbage-collection/background-gc.md).

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true`- tło GC<br/>`false`- niebieżne GC | .NET Rdzeń 1.0 |
| **Właściwość MSBuild** | `ConcurrentGarbageCollection` | `true`- tło GC<br/>`false`- niebieżne GC | .NET Rdzeń 1.0 |
| **Zmienna środowiskowa** | `COMPlus_gcConcurrent` | `true`- tło GC<br/>`false`- niebieżne GC | .NET Rdzeń 1.0 |
| **app.config dla programu .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`- tło GC<br/>`false`- niebieżne GC |  |

### <a name="examples"></a>Przykłady

*runtimeconfig.json:*

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

## <a name="manage-resource-usage"></a>Zarządzanie użyciem zasobów

Użyj ustawień opisanych w tej sekcji, aby zarządzać pamięcią i użyciem procesora modułu zbierającego elementy bezużyteczne.

Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zobacz [Środkowy grunt między stacją roboczą a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) wpisem blogu GC serwera.

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System.GC.HeapCount/COMPlus_GCHeapCount

- Ogranicza liczbę stert utworzonych przez moduł zbierający elementy bezużyteczne.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest włączona, co jest ustawieniem domyślnym, ustawienie liczby stert affinitizes `n` GC sterty/wątki do pierwszych `n` procesorów. (Użyj [affinitize maski](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) lub [affinitize ustawienia zakresów,](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) aby określić dokładnie, które procesory do affinitize.)
- Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie ogranicza liczbę stert GC.
- Aby uzyskać więcej informacji, zobacz [uwagi GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapCount` | *wartość szesnastkowa* | .NET Core 3.0 |
| **app.config dla programu .NET Framework** | [GCHeapCount (GCHeapCount)](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *wartość dziesiętna* | .NET Framework 4.6.2 |

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
> Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną. Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład, aby ograniczyć liczbę stert do 16, wartości będą 16 dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Określa dokładne procesory, które powinny być używane przez wątki modułu zbierającego elementy bezużyteczne.
- Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Wartość jest maską bitową definiującą procesory, które są dostępne dla procesu. Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używasz zmiennej środowiskowej) jest 0011 1111 1111 w notacji binarnej. Określa to, że pierwsze procesory 10 mają być używane. Aby określić następne 10 procesorów, czyli procesory 10-19, należy określić wartość dziesiętną 1047552 (lub wartość szesnastową 0xFFC00 lub FFC00), która jest równoważna wartości binarnej 1111 1111 1100 0000 0000.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapAffinitizeMask` | *wartość szesnastkowa* | .NET Core 3.0 |
| **app.config dla programu .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *wartość dziesiętna* | .NET Framework 4.6.2 |

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

- Określa listę procesorów, które mają być używane dla wątków modułu zbierającego elementy bezużyteczne.
- To ustawienie jest podobne do [systema.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), z tą różnicą, że umożliwia określenie więcej niż 64 procesorów.
- W przypadku systemów operacyjnych Windows prefiksuje numer procesora lub zakres z odpowiednią [grupą procesorów](/windows/win32/procthread/processor-groups), na przykład "0:1-10,0:12,1:50-52,1:70".
- Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora dla GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
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

  Gdy 64-bitowy komputer z systemem Windows ma wiele grup procesorów, oznacza to, że istnieje więcej niż 64 procesory, włączając ten element rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU. Moduł zbierający elementy bezużyteczne używa wszystkich rdzeni do tworzenia i równoważenia sterty.

- Dotyczy wyrzucania elementów bezużytecznych serwera tylko w 64-bitowych systemach operacyjnych systemu Windows.
- Domyślnie:`0`Wyłączone ( ).
- Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora dla GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_GCCpuGroup` | `0`- niepełnosprawnych<br/>`1`- włączone | .NET Rdzeń 1.0 |
| **app.config dla programu .NET Framework** | [Grupa GCCpu](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`- niepełnosprawnych<br/>`true`- włączone |  |

> [!NOTE]
> Aby skonfigurować środowisko uruchomieniowe języka wspólnego (CLR), aby również dystrybuować wątki z puli wątków we wszystkich grupach procesora CPU, włącz opcję [Thread_UseAllCpuGroups elementu.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) W przypadku aplikacji .NET Core można włączyć tę `COMPlus_Thread_UseAllCpuGroups` opcję, `1`ustawiając wartość zmiennej środowiskowej na .

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System.GC.NoAffinitize/COMPlus_GCNoAffinitize

- Określa, czy *affinitize* wątków wyrzucania elementów bezużytecznych z procesorami. Aby affinitize wątku GC oznacza, że można go uruchomić tylko na jego określonego procesora CPU. Sterta jest tworzony dla każdego wątku GC.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Domyślnie: Affinitize wątków wyrzucania`false`elementów bezużytecznych z procesorami ( ).

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false`- affinitize<br/>`true`- nie affinitize | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCNoAffinitize` | `0`- affinitize<br/>`1`- nie affinitize | .NET Core 3.0 |
| **app.config dla programu .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`- affinitize<br/>`true`- nie affinitize | .NET Framework 4.6.2 |

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

- Określa maksymalny rozmiar zatwierdzenia w bajtach dla sterty GC i księgowego GC.
- To ustawienie dotyczy tylko komputerów 64-bitowych.
- Wartość domyślna, która ma zastosowanie tylko w niektórych przypadkach, jest większa od 20 MB lub 75% limitu pamięci w kontenerze. Wartość domyślna ma zastosowanie, jeśli:

  - Proces jest uruchomiony wewnątrz kontenera, który ma określony limit pamięci.
  - [System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) nie jest ustawiony.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
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
> Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną. Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład, aby określić limit twardy sterty 200 mebibajtów (MiB), wartości będą 209715200 dla pliku JSON i 0xC8000000 lub C8000000 dla zmiennej środowiskowej.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Określa dopuszczalne użycie sterty GC jako procent całkowitej pamięci fizycznej.
- Jeśli [system.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) jest również ustawiony, to ustawienie jest ignorowane.
- To ustawienie dotyczy tylko komputerów 64-bitowych.
- Jeśli proces jest uruchomiony wewnątrz kontenera, który ma określony limit pamięci, wartość procentowa jest obliczana jako procent tego limitu pamięci.
- Wartość domyślna, która ma zastosowanie tylko w niektórych przypadkach, jest mniejsza z 20 MB lub 75% limitu pamięci w kontenerze. Wartość domyślna ma zastosowanie, jeśli:

  - Proces jest uruchomiony wewnątrz kontenera, który ma określony limit pamięci.
  - [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) nie jest ustawiony.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
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
> Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną. Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład, aby ograniczyć użycie sterty do 30%, wartości będą 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System.GC.RetainVM/COMPlus_GCRetainVM

- Konfiguruje, czy segmenty, które powinny zostać usunięte, są umieszczane na liście wstrzymania do wykorzystania w przyszłości, czy są zwalniane z powrotem do systemu operacyjnego.
- Domyślnie: Zwolnij segmenty z`false`powrotem do systemu operacyjnego ( ).

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false`- zwolnienie do systemu operacyjnego<br/>`true`- umieścić w trybie gotowości | .NET Rdzeń 1.0 |
| **Właściwość MSBuild** | `RetainVMGarbageCollection` | `false`- zwolnienie do systemu operacyjnego<br/>`true`- umieścić w trybie gotowości | .NET Rdzeń 1.0 |
| **Zmienna środowiskowa** | `COMPlus_GCRetainVM` | `0`- zwolnienie do systemu operacyjnego<br/>`1`- umieścić w trybie gotowości | .NET Rdzeń 1.0 |

### <a name="examples"></a>Przykłady

*runtimeconfig.json:*

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

- Określa, czy duże strony mają być używane po ustawieniu limitu twardego sterty.
- Domyślnie:`0`Wyłączone ( ).
- Jest to ustawienie eksperymentalne.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_GCLargePages` | `0`- niepełnosprawnych<br/>`1`- włączone | .NET Core 3.0 |

## <a name="large-objects"></a>Duże obiekty

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Konfiguruje obsługę modułów zbierających elementy bezużyteczne na platformach 64-bitowych dla macierzy o całkowitym rozmiarze większym niż 2 gigabajty (GB).
- Domyślnie: Włączone`1`( ).
- Ta opcja może stać się przestarzała w przyszłej wersji platformy .NET.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_gcAllowVeryLargeObjects` | `1`- włączone<br/> `0`- niepełnosprawnych | .NET Rdzeń 1.0 |
| **app.config dla programu .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`- włączone<br/> `0`- niepełnosprawnych | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Próg sterty dużych obiektów

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System.GC.LOHThreshold/COMPlus_GCLOHThreshold

- Określa rozmiar progu w bajtach, który powoduje, że obiekty, aby przejść na stercie dużych obiektów (LOH).
- Domyślny próg wynosi 85 000 bajtów.
- Określona wartość musi być większa niż próg domyślny.

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | *wartość dziesiętna* | .NET Rdzeń 1.0 |
| **Zmienna środowiskowa** | `COMPlus_GCLOHThreshold` | *wartość szesnastkowa* | .NET Rdzeń 1.0 |
| **app.config dla programu .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *wartość dziesiętna* |  .NET Framework 4.8 |

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
> Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną. Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości będą 120000 dla pliku JSON i 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.

## <a name="standalone-gc"></a>Samodzielny GC

### <a name="complus_gcname"></a>COMPlus_GCName

- Określa ścieżkę do biblioteki zawierającej moduł zbierający elementy bezużyteczne, które środowisko wykonawcze zamierza załadować.
- Aby uzyskać więcej informacji, zobacz [Samodzielny projekt ładowarki GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nazwa ustawienia | Wartości | Wprowadzono wersję |
| - | - | - | - |
| **runtimeconfig.json** | Nie dotyczy | Nie dotyczy | Nie dotyczy |
| **Zmienna środowiskowa** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
