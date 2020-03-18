---
title: Ustawienia konfiguracji kompilacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują działanie kompilatora JIT dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092892"
---
# <a name="run-time-configuration-options-for-compilation"></a>Opcje konfiguracji w czasie wykonywania kompilacji

## <a name="tiered-compilation"></a>Kompilacja warstwowa

- Konfiguruje, czy kompilator just-in-time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation). Warstwowe metody przejścia kompilacji za pośrednictwem dwóch warstw:
  - Pierwsza warstwa generuje kod szybciej[(szybkie JIT)](#quick-jit)lub ładuje wstępnie skompilowany kod ([ReadyToRun](#readytorun)).
  - Druga warstwa generuje zoptymalizowany kod w tle ("optymalizacja JIT").
- W .NET Core 3.0 i nowszych kompilacji warstwowej jest włączona domyślnie.
- W .NET Core 2.1 i 2.2 kompilacja warstwowa jest domyślnie wyłączona.
- Aby uzyskać więcej informacji, zobacz [przewodnik kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation` | `true`- włączona<br/>`false`- wyłączone |
| **MSBuild, właściwość** | `TieredCompilation` | `true`- włączona<br/>`false`- wyłączone |
| **Zmienna środowiskowa** | `COMPlus_TieredCompilation` | `1`- włączona<br/>`0`- wyłączone |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

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

## <a name="quick-jit"></a>Szybkie JIT

- Konfiguruje, czy kompilator JIT używa *szybkiego JIT*. W przypadku metod, które nie zawierają pętli i dla których wstępnie skompilowany kod nie jest dostępny, szybki JIT kompiluje je szybciej, ale bez optymalizacji.
- Włączenie szybkiego JIT skraca czas uruchamiania, ale może generować kod o obniżonych właściwościach wydajności. Na przykład kod może używać więcej miejsca na stosie, przydzielić więcej pamięci i działać wolniej.
- Jeśli szybki JIT jest wyłączony, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej. Jeśli metoda nie jest wstępnie skompilowany z [ReadyToRun](#readytorun), zachowanie JIT jest taka sama, jak gdyby [warstwowe kompilacji](#tiered-compilation) zostały wyłączone.
- W .NET Core 3.0 i nowszych, szybkie JIT jest domyślnie włączona.
- W programach .NET Core 2.1 i 2.2 szybkie jit jest domyślnie wyłączone.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJit` | `true`- włączona<br/>`false`- wyłączone |
| **MSBuild, właściwość** | `TieredCompilationQuickJit` | `true`- włączona<br/>`false`- wyłączone |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJit` | `1`- włączona<br/>`0`- wyłączone |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

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

## <a name="quick-jit-for-loops"></a>Szybki JIT do pętli

- Konfiguruje, czy kompilator JIT używa szybkiego JIT na metody, które zawierają pętle.
- Włączenie szybkiego JIT dla pętli może zwiększyć wydajność uruchamiania. Jednak długotrwałe pętle mogą utknąć w mniej zoptymalizowanym kodzie przez długi czas.
- Jeśli [szybkie JIT](#quick-jit) jest wyłączone, to ustawienie nie ma wpływu.
- Domyślnie: Wyłączone`false`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`- wyłączone<br/>`true`- włączona |
| **MSBuild, właściwość** | `TieredCompilationQuickJitForLoops` | `false`- wyłączone<br/>`true`- włączona |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJitForLoops` | `0`- wyłączone<br/>`1`- włączona |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

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

## <a name="readytorun"></a>Readytorun (Gotowy)

- Konfiguruje, czy program .NET Core używa wstępnie skompilowanego kodu dla obrazów z dostępnymi danymi ReadyToRun. Wyłączenie tej opcji wymusza, że program runtime jest kodem frameworkkompilacji JIT.
- Aby uzyskać więcej informacji, zobacz [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Domyślnie: Włączone`1`( ).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **Zmienna środowiskowa** | `COMPlus_ReadyToRun` | `1`- włączona<br/>`0`- wyłączone |
