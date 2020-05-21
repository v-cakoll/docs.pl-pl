---
title: Ustawienia konfiguracji kompilacji
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: cfcf9b5fc8d11a4ae35ab9b152f32133cd6930bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762009"
---
# <a name="run-time-configuration-options-for-compilation"></a>Opcje konfiguracji czasu wykonywania dla kompilacji

## <a name="tiered-compilation"></a>Kompilacja warstwowa

- Określa, czy kompilator just-in-Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation). Warstwy z przechodzeniem warstwowym w ramach dwóch warstw:
  - Pierwsza warstwa generuje kod szybciej (szybko[JIT](#quick-jit)) lub ładuje wstępnie skompilowany kod ([ReadyToRun](#readytorun)).
  - Druga warstwa generuje zoptymalizowany kod w tle ("Optymalizacja JIT").
- W programie .NET Core 3,0 i nowszych kompilacja warstwowa jest domyślnie włączona.
- W przypadku oprogramowania .NET Core 2,1 i 2,2 kompilacja warstwowa jest domyślnie wyłączona.
- Aby uzyskać więcej informacji, zobacz [Przewodnik po kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true`-włączone<br/>`false`-wyłączone |
| **Właściwość programu MSBuild** | `TieredCompilation` | `true`-włączone<br/>`false`-wyłączone |
| **Zmienna środowiskowa** | `COMPlus_TieredCompilation` | `1`-włączone<br/>`0`-wyłączone |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a>Szybka JIT

- Określa, czy kompilator JIT używa *szybkiej JIT*. W przypadku metod, które nie zawierają pętli i dla których wstępnie skompilowany kod jest niedostępny, szybka JIT kompiluje je szybciej, ale bez optymalizacji.
- Włączenie szybkiej JIT skraca czas uruchamiania, ale może generować kod o obniżonej wydajności. Na przykład kod może używać większej ilości miejsca, przydzielać więcej pamięci i działać wolniej.
- Jeśli szybka JIT jest wyłączona, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej. Jeśli metoda nie jest wstępnie skompilowana za pomocą [ReadyToRun](#readytorun), zachowanie JIT jest takie samo, jakby była wyłączona [kompilacja warstwowa](#tiered-compilation) .
- W przypadku platformy .NET Core 3,0 i nowszych tryb szybkiej JIT jest domyślnie włączony.
- W przypadku programów .NET Core 2,1 i 2,2 Szybka metoda JIT jest domyślnie wyłączona.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJit` | `true`-włączone<br/>`false`-wyłączone |
| **Właściwość programu MSBuild** | `TieredCompilationQuickJit` | `true`-włączone<br/>`false`-wyłączone |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJit` | `1`-włączone<br/>`0`-wyłączone |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a>Szybka JIT dla pętli

- Określa, czy kompilator JIT używa szybkiej JIT metod, które zawierają pętle.
- Włączenie szybkiej JIT dla pętli może poprawić wydajność uruchamiania. Jednak długotrwałe pętle mogą być zablokowane w niezoptymalizowanym kodzie przez długi czas.
- Jeśli [szybka JIT](#quick-jit) jest wyłączona, to ustawienie nie ma żadnego wpływu.
- W przypadku pominięcia tego ustawienia szybka JIT nie jest używana dla metod, które zawierają pętle. Jest to równoznaczne z ustawieniem wartości `false` .

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`-wyłączone<br/>`true`-włączone |
| **Właściwość programu MSBuild** | `TieredCompilationQuickJitForLoops` | `false`-wyłączone<br/>`true`-włączone |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJitForLoops` | `0`-wyłączone<br/>`1`-włączone |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun

- Określa, czy środowisko uruchomieniowe programu .NET Core używa wstępnie skompilowanego kodu dla obrazów z dostępnymi danymi ReadyToRun. Wyłączenie tej opcji zmusza środowisko uruchomieniowe do kompilowania kodu struktury JIT.
- Aby uzyskać więcej informacji, zobacz [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- W przypadku pominięcia tego ustawienia platforma .NET będzie używać danych ReadyToRun, gdy jest ona dostępna. Jest to równoznaczne z ustawieniem wartości `1` .

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **Zmienna środowiskowa** | `COMPlus_ReadyToRun` | `1`-włączone<br/>`0`-wyłączone |
