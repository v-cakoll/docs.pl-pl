---
title: Ustawienia konfiguracji kompilacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ac51aa13254b2f2b1fdd8d1dd9c52559831a1659
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989119"
---
# <a name="run-time-configuration-options-for-compilation"></a>Opcje konfiguracji w czasie wykonywania kompilacji

## <a name="tiered-compilation"></a>Kompilacja warstwowa

- Konfiguruje, czy kompilator just-in-time (JIT) używa [kompilacji warstwowej.](../whats-new/dotnet-core-3-0.md#tiered-compilation) Metody przejścia kompilacji warstwowej za pośrednictwem dwóch warstw:
  - Pierwsza warstwa generuje kod szybciej[(szybki JIT)](#quick-jit)lub ładuje wstępnie skompilowany kod ([ReadyToRun](#readytorun)).
  - Druga warstwa generuje zoptymalizowany kod w tle ("optymalizacja JIT").
- W .NET Core 3.0 i nowszych kompilacja warstwowa jest domyślnie włączona.
- W .NET Core 2.1 i 2.2 kompilacja warstwowa jest domyślnie wyłączona.
- Aby uzyskać więcej informacji, zobacz [przewodnik kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation` | `true`- włączone<br/>`false`- niepełnosprawnych |
| **Właściwość MSBuild** | `TieredCompilation` | `true`- włączone<br/>`false`- niepełnosprawnych |
| **Zmienna środowiskowa** | `COMPlus_TieredCompilation` | `1`- włączone<br/>`0`- niepełnosprawnych |

### <a name="examples"></a>Przykłady

*runtimeconfig.json:*

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

## <a name="quick-jit"></a>Szybki JIT

- Konfiguruje, czy kompilator JIT używa *szybkiego JIT*. Dla metod, które nie zawierają pętli i dla których wstępnie skompilowany kod nie jest dostępny, szybkie JIT kompiluje je szybciej, ale bez optymalizacji.
- Włączenie szybkiego JIT skracają czas uruchamiania, ale mogą tworzyć kod o obniżonej wydajności. Na przykład kod może użyć więcej miejsca na stosie, przydzielić więcej pamięci i działać wolniej.
- Jeśli szybkie JIT jest wyłączona, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej. Jeśli metoda nie jest wstępnie skompilowana z [ReadyToRun](#readytorun), zachowanie JIT jest takie samo, jak gdyby [kompilacja warstwowa](#tiered-compilation) została wyłączona.
- W .NET Core 3.0 lub nowszych, szybkie JIT jest domyślnie włączona.
- W .NET Core 2.1 i 2.2 szybkie JIT jest domyślnie wyłączone.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJit` | `true`- włączone<br/>`false`- niepełnosprawnych |
| **Właściwość MSBuild** | `TieredCompilationQuickJit` | `true`- włączone<br/>`false`- niepełnosprawnych |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJit` | `1`- włączone<br/>`0`- niepełnosprawnych |

### <a name="examples"></a>Przykłady

*runtimeconfig.json:*

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

## <a name="quick-jit-for-loops"></a>Szybki JIT dla pętli

- Konfiguruje, czy kompilator JIT używa szybkiego JIT na metodach, które zawierają pętle.
- Włączenie szybkiego JIT dla pętli może poprawić wydajność uruchamiania. Jednak długotrwałe pętle mogą utknąć w mniej zoptymalizowanym kodzie przez długi czas.
- Jeśli [szybkie JIT](#quick-jit) jest wyłączone, to ustawienie nie ma wpływu.
- Domyślnie:`false`Wyłączone ( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`- niepełnosprawnych<br/>`true`- włączone |
| **Właściwość MSBuild** | `TieredCompilationQuickJitForLoops` | `false`- niepełnosprawnych<br/>`true`- włączone |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJitForLoops` | `0`- niepełnosprawnych<br/>`1`- włączone |

### <a name="examples"></a>Przykłady

*runtimeconfig.json:*

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
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun (ReadyToRun)

- Konfiguruje, czy środowisko uruchomieniowe .NET Core używa wstępnie skompilowanego kodu dla obrazów z dostępnymi danymi ReadyToRun. Wyłączenie tej opcji wymusza środowisko uruchomieniowe do kodu struktury kompilacji JIT.
- Aby uzyskać więcej informacji, zobacz [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Domyślnie: Włączone`1`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **Zmienna środowiskowa** | `COMPlus_ReadyToRun` | `1`- włączone<br/>`0`- niepełnosprawnych |
