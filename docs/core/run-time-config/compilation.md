---
title: Ustawienia konfiguracji kompilacji
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733540"
---
# <a name="run-time-configuration-options-for-compilation"></a>Opcje konfiguracji czasu wykonywania dla kompilacji

## <a name="tiered-compilation"></a>Kompilacja warstwowa

- Określa, czy kompilator just-in-Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation). Warstwy z przechodzeniem warstwowym w ramach dwóch warstw:
  - Pierwsza warstwa generuje kod szybciej (szybko[JIT](#quick-jit)) lub ładuje wstępnie skompilowany kod ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).
  - Druga warstwa generuje zoptymalizowany kod w tle ("Optymalizacja JIT").
- W programie .NET Core 3,0 i nowszych kompilacja warstwowa jest domyślnie włączona.
- W przypadku oprogramowania .NET Core 2,1 i 2,2 kompilacja warstwowa jest domyślnie wyłączona.
- Aby uzyskać więcej informacji, zobacz [Przewodnik po kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true` — włączono<br/>`false` — wyłączone |
| **Właściwość programu MSBuild** | `TieredCompilation` | `true` — włączono<br/>`false` — wyłączone |
| **Zmienna środowiskowa** | `COMPlus_TieredCompilation` | `1` — włączono<br/>`0` — wyłączone |

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
- Jeśli szybka JIT jest wyłączona, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej. Jeśli metoda nie jest wstępnie skompilowana za pomocą [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), zachowanie JIT jest takie samo, jakby była wyłączona [kompilacja warstwowa](#tiered-compilation) .
- W przypadku platformy .NET Core 3,0 i nowszych tryb szybkiej JIT jest domyślnie włączony.
- W przypadku programów .NET Core 2,1 i 2,2 Szybka metoda JIT jest domyślnie wyłączona.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJit` | `true` — włączono<br/>`false` — wyłączone |
| **Właściwość programu MSBuild** | `TieredCompilationQuickJit` | `true` — włączono<br/>`false` — wyłączone |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJit` | `1` — włączono<br/>`0` — wyłączone |

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
- Domyślnie: wyłączone (`false`).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false` — wyłączone<br/>`true` — włączono |
| **Właściwość programu MSBuild** | `TieredCompilationQuickJitForLoops` | `false` — wyłączone<br/>`true` — włączono |
| **Zmienna środowiskowa** | `COMPlus_TC_QuickJitForLoops` | `0` — wyłączone<br/>`1` — włączono |

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
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```
