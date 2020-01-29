---
title: Ustawienia konfiguracji modułu wyrzucania elementów bezużytecznych
description: Informacje o ustawieniach czasu wykonywania w celu skonfigurowania sposobu, w jaki moduł zbierający elementy bezużyteczne zarządza pamięcią dla aplikacji platformy .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733518"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Opcje konfiguracji czasu wykonywania dla wyrzucania elementów bezużytecznych

Ta strona zawiera informacje na temat ustawień modułu zbierającego elementy bezużyteczne (GC), które można zmienić w czasie wykonywania. Jeśli próbujesz osiągnąć szczytową wydajność uruchomionej aplikacji, rozważ użycie tych ustawień. Jednak wartości domyślne zapewniają optymalną wydajność większości aplikacji w typowych sytuacjach.

Ustawienia są ułożone w grupach na tej stronie. Ustawienia w ramach każdej grupy są często używane w połączeniu ze sobą, aby osiągnąć konkretny wynik.

> [!NOTE]
>
> - Te ustawienia mogą być również dynamicznie zmieniane przez aplikację w trakcie działania, więc wszystkie ustawione ustawienia czasu wykonywania mogą zostać zastąpione.
> - Niektóre ustawienia, takie jak [poziom opóźnienia](../../standard/garbage-collection/latency.md), są zazwyczaj ustawiane tylko za pomocą interfejsu API w czasie projektowania. Takie ustawienia zostały pominięte na tej stronie.
> - W przypadku wartości liczbowych Użyj notacji dziesiętnej dla ustawień w pliku *runtimeconfig. JSON* i notacji szesnastkowej dla ustawień zmiennych środowiskowych. W przypadku wartości szesnastkowych można je określić z prefiksem "0x" lub bez niego.

## <a name="flavors-of-garbage-collection"></a>Typy wyrzucania elementów bezużytecznych

Dwa główne typy wyrzucania elementów bezużytecznych to stacja robocza i serwer GC. Aby uzyskać więcej informacji o różnicach między tymi dwoma, zobacz podstawowe informacje dotyczące [wyrzucania elementów bezużytecznych](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Podelementy wyrzucania elementów bezużytecznych są tła i niewspółbieżne.

Użyj następujących ustawień, aby wybrać typy wyrzucania elementów bezużytecznych:

### <a name="systemgcservercomplus_gcserver"></a>System. GC. Server/COMPlus_gcServer

- Określa, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera.
- Domyślnie: wyrzucanie elementów bezużytecznych stacji roboczej (`false`).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Server` | `false` — stacja robocza<br/>`true` — serwer | .NET Core 1.0 |
| **Właściwość programu MSBuild** | `ServerGarbageCollection` | `false` — stacja robocza<br/>`true` — serwer | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_gcServer` | `0` — stacja robocza<br/>`1` — serwer | .NET Core 1.0 |
| **App. config dla .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false` — stacja robocza<br/>`true` — serwer |  |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

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

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System. GC. współbieżne/COMPlus_gcConcurrent

- Określa, czy jest włączone wyrzucanie elementów bezużytecznych w tle.
- Wartość domyślna: włączone (`true`).
- Aby uzyskać więcej informacji, zobacz [zbieranie elementów bezużytecznych w tle](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) i [odzyskiwanie pamięci serwera w tle](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Concurrent` | `true` — w tle GC<br/>`false` — niewspółbieżne GC | .NET Core 1.0 |
| **Właściwość programu MSBuild** | `ConcurrentGarbageCollection` | `true` — w tle GC<br/>`false` — niewspółbieżne GC | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_gcConcurrent` | `true` — w tle GC<br/>`false` — niewspółbieżne GC | .NET Core 1.0 |
| **App. config dla .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true` — w tle GC<br/>`false` — niewspółbieżne GC |  |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

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

Ustawienia opisane w tej sekcji służą do zarządzania użyciem pamięci i procesora modułu wyrzucania elementów bezużytecznych.

Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zapoznaj się z wpisem na blogu centrum [robocze i serwer GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System. GC. HeapCount/COMPlus_GCHeapCount

- Ogranicza liczbę stert utworzonych przez moduł wyrzucania elementów bezużytecznych.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Jeśli koligacja procesora GC jest włączona, co jest ustawieniem domyślnym, licznik sterty skoligacony `n` GC sterty/wątki z pierwszymi procesorami `n`. (Użyj koligacji maska lub ustawienia zakresów koligacji, aby określić, które procesory mają być koligacji).
- Jeśli koligacja procesora GC jest wyłączona, to ustawienie ogranicza liczbę stert GC.
- Aby uzyskać więcej informacji, zobacz [uwagi GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapCount` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapCount` | *wartość szesnastkowa* | .NET Core 3.0 |
| **App. config dla .NET Framework** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *wartość dziesiętna* | .NET Framework 4.6.2 |

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
> Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną. Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład aby ograniczyć liczbę stert do 16, wartości dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Określa dokładne procesory, które powinny być używane przez wątki modułu wyrzucania elementów bezużytecznych.
- Jeśli Koligacja procesorów jest wyłączona przez ustawienie `System.GC.NoAffinitize` do `true`, to ustawienie zostanie zignorowane.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Wartość jest maską bitową, która definiuje procesory, które są dostępne dla procesu. Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używana jest zmienna środowiskowa) to 0011 1111 1111 w notacji binarnej. Oznacza to, że pierwsze 10 procesorów ma być używany. Aby określić następne 10 procesorów, czyli procesorów 10-19, określ wartość dziesiętną 1047552 (lub wartość szesnastkową 0xFFC00 lub FFC00), która jest równoważna z wartością binarną 1111 1111 1100 0000 0000.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapAffinitizeMask` | *wartość dziesiętna* | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapAffinitizeMask` | *wartość szesnastkowa* | .NET Core 3.0 |
| **App. config dla .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *wartość dziesiętna* | .NET Framework 4.6.2 |

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

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Określa listę procesorów, które mają być używane na potrzeby wątków modułu wyrzucania elementów bezużytecznych.
- To ustawienie jest podobne do `System.GC.HeapAffinitizeMask`, z tą różnicą, że pozwala określić więcej niż 64 procesorów.
- W przypadku systemów operacyjnych Windows należy prefiksować numer procesora lub zakres z odpowiednią [grupą procesorów CPU](/windows/win32/procthread/processor-groups), na przykład "0:1-10, 0:12, 1:50-52, 1:70".
- Jeśli Koligacja procesorów jest wyłączona przez ustawienie `System.GC.NoAffinitize` do `true`, to ustawienie zostanie zignorowane.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.GCHeapAffinitizeRanges` | Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.<br/>Przykład UNIX: "1-10, 12, 50-52, 70"<br/>Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCHeapAffinitizeRanges` | Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.<br/>Przykład UNIX: "1-10, 12, 50-52, 70"<br/>Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |

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

- Określa, czy moduł wyrzucania elementów bezużytecznych używa [grup CPU](/windows/win32/procthread/processor-groups) , czy nie.

  Gdy 64-bitowy komputer z systemem Windows ma wiele grup CPU, oznacza to, że istnieje więcej niż 64 procesorów, włączając ten element rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU. Moduł wyrzucania elementów bezużytecznych używa wszystkich rdzeni do tworzenia i równoważenia sterty.

- Stosuje się do wyrzucania elementów bezużytecznych serwera w 64-bitowych systemach operacyjnych Windows.
- Domyślnie: wyłączone (`0`).
- Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_GCCpuGroup` | `0` — wyłączone<br/>`1` — włączono | .NET Core 1.0 |
| **App. config dla .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false` — wyłączone<br/>`true` — włączono |  |

> [!NOTE]
> Aby skonfigurować środowisko uruchomieniowe języka wspólnego (CLR) do dystrybucji wątków z puli wątków we wszystkich grupach procesora, Włącz opcję [Thread_UseAllCpuGroups elementu](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) . W przypadku aplikacji platformy .NET Core można włączyć tę opcję, ustawiając wartość zmiennej środowiskowej `COMPlus_Thread_UseAllCpuGroups` na `1`.

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System. GC. NoAffinitize/COMPlus_GCNoAffinitize

- Określa, czy *koligacji* wątki odzyskiwania pamięci z procesorami. Aby koligacji wątek GC, oznacza to, że można go uruchomić tylko w określonym procesorze CPU. Sterta jest tworzona dla każdego wątku GC.
- Dotyczy tylko wyrzucania elementów bezużytecznych serwera.
- Domyślnie: koligacji wątki odzyskiwania pamięci z procesorami (`false`).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.NoAffinitize` | `false` — koligacji<br/>`true` — nie koligacji | .NET Core 3.0 |
| **Zmienna środowiskowa** | `COMPlus_GCNoAffinitize` | `0` — koligacji<br/>`1` — nie koligacji | .NET Core 3.0 |
| **App. config dla .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false` — koligacji<br/>`true` — nie koligacji | .NET Framework 4.6.2 |

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

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit

- Określa maksymalny rozmiar zatwierdzeń w bajtach dla sterty GC i księgowości GC.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimit` | *wartość dziesiętna* | .NET Core 3.0 |
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
> Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną. Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład aby określić stały limit sterty wynoszący 200 mebibytes (MiB), wartości byłyby 209715200 dla pliku JSON i 0xC800000 lub C800000 dla zmiennej środowiskowej.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Określa użycie sterty GC jako procent całkowitej ilości pamięci.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimitPercent` | *wartość dziesiętna* | .NET Core 3.0 |
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
> Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną. Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład aby ograniczyć użycie sterty do 30%, wartości byłyby 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System. GC. RetainVM/COMPlus_GCRetainVM

- Określa, czy segmenty, które mają zostać usunięte, są umieszczane na liście gotowości do użycia w przyszłości lub są wyłączane z powrotem do systemu operacyjnego (OS).
- Domyślnie: segmenty wydań z powrotem do systemu operacyjnego (`false`).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.RetainVM` | `false` — wydanie do systemu operacyjnego<br/>`true` — Umieść w stanie wstrzymania | .NET Core 1.0 |
| **Właściwość programu MSBuild** | `RetainVMGarbageCollection` | `false` — wydanie do systemu operacyjnego<br/>`true` — Umieść w stanie wstrzymania | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_GCRetainVM` | `0` — wydanie do systemu operacyjnego<br/>`1` — Umieść w stanie wstrzymania | .NET Core 1.0 |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

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

- Określa, czy mają być używane duże strony, gdy jest ustawiony limit sztywny sterty.
- Domyślnie: wyłączone (`0`).
- Jest to ustawienie eksperymentalne.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_GCLargePages` | `0` — wyłączone<br/>`1` — włączono | .NET Core 3.0 |

## <a name="large-objects"></a>Duże obiekty

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Konfiguruje obsługę modułu wyrzucania elementów bezużytecznych na platformach 64-bitowych dla tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.
- Wartość domyślna: włączone (`1`).
- Ta opcja może stać się przestarzała w przyszłej wersji platformy .NET.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_gcAllowVeryLargeObjects` | `1` — włączono<br/> `0` — wyłączone | .NET Core 1.0 |
| **App. config dla .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1` — włączono<br/> `0` — wyłączone | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Próg sterty dla dużego obiektu

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System. GC. LOHThreshold/COMPlus_GCLOHThreshold

- Określa rozmiar progu (w bajtach), który powoduje, że obiekty są na stosie dużego obiektu (LOH).
- Domyślny próg to 85 000 bajtów.
- Określona wartość musi być większa niż wartość progu domyślnego.

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.LOHThreshold` | *wartość dziesiętna* | .NET Core 1.0 |
| **Zmienna środowiskowa** | `COMPlus_GCLOHThreshold` | *wartość szesnastkowa* | .NET Core 1.0 |
| **App. config dla .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *wartość dziesiętna* | .NET Framework 4,8 |

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
> Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną. Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową. Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości byłyby 120000 dla pliku JSON oraz 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.

## <a name="standalone-gc"></a>Autonomiczna GC

### <a name="complus_gcname"></a>COMPlus_GCName

- Określa ścieżkę do biblioteki zawierającej Moduł wyrzucania elementów bezużytecznych, który środowisko uruchomieniowe zamierza załadować.
- Aby uzyskać więcej informacji, zobacz [prekonstrukcja modułu ładującego GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nazwa ustawienia | Wartości | Wprowadzona wersja |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Zmienna środowiskowa** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
