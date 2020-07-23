---
title: Omówienie narzędzi diagnostycznych — .NET Core
description: Przegląd narzędzi i technik dostępnych do diagnozowania aplikacji .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: dc64c03ee9c8cee6a5b3c5cc089b4a1a2c27f84a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924785"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Jakie narzędzia diagnostyczne są dostępne w środowisku .NET Core?

Oprogramowanie nie zawsze zachowuje się w oczekiwany sposób, ale .NET Core ma narzędzia i interfejsy API, które ułatwią zdiagnozowanie tych problemów szybko i efektywnie.

Ten artykuł ułatwia znalezienie różnych potrzebnych narzędzi.

## <a name="managed-debuggers"></a>Debugery zarządzane

[Zarządzane debugery](managed-debuggers.md) umożliwiają korzystanie z programu. Wstrzymywanie, przyrostowe wykonywanie, badanie i wznawianie zawiera szczegółowe informacje o zachowaniu kodu. Debuger to pierwszy wybór służący do diagnozowania problemów funkcjonalnych, które można łatwo odtworzyć.

## <a name="logging-and-tracing"></a>Rejestrowanie i śledzenie

[Rejestrowanie i śledzenie](logging-tracing.md) to powiązane techniki. Odnoszą się one do kodu instrumentacji do tworzenia plików dziennika. Pliki rejestrują szczegóły działania programu. Te szczegółowe informacje mogą służyć do diagnozowania najbardziej złożonych problemów. W połączeniu z sygnaturami czasowymi te techniki są również przydatne w badaniach wydajności.

## <a name="unit-testing"></a>Testy jednostkowe

[Testowanie jednostkowe](../testing/index.md) to kluczowy składnik ciągłej integracji i wdrażania wysokiej jakości oprogramowania. Testy jednostkowe zostały zaprojektowane w celu zapewnienia wczesnego ostrzegania w przypadku wystąpienia elementu.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>Narzędzia diagnostyczne programu .NET Core dotnet Diagnostic

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-Counters](dotnet-counters.md) to narzędzie do monitorowania wydajności służące do monitorowania kondycji pierwszego poziomu i badania wydajności. Obserwuje wartości liczników wydajności publikowane za pośrednictwem <xref:System.Diagnostics.Tracing.EventCounter> interfejsu API. Można na przykład szybko monitorować elementy, takie jak użycie procesora CPU, lub częstotliwość zgłaszania wyjątków w aplikacji .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

Narzędzie [dotnet-dump](dotnet-dump.md) to sposób zbierania i analizowania zrzutów podstawowych systemów Windows i Linux bez natywnego debugera.

### <a name="dotnet-trace"></a>dotnet-trace

Program .NET Core zawiera informacje o tym, w jaki sposób są `EventPipe` udostępniane dane diagnostyczne. Narzędzie do [śledzenia dotnet](dotnet-trace.md) umożliwia korzystanie z interesujących danych profilowania z poziomu aplikacji, które mogą pomóc w scenariuszach, w których konieczne jest powolne działanie aplikacji.

## <a name="net-core-diagnostics-tutorials"></a>Samouczki dotyczące diagnostyki platformy .NET Core

### <a name="debug-a-memory-leak"></a>Debugowanie przecieku pamięci

[Samouczek: debugowanie przecieku pamięci](debug-memory-leak.md) przeprowadzi przez znalezienie przecieku pamięci. Narzędzie [dotnet-Counters](dotnet-counters.md) służy do potwierdzenia przecieku i narzędzia [dotnet-dump](dotnet-dump.md) służy do diagnozowania wycieku.

### <a name="debug-high-cpu-usage"></a>Debuguj wysokie użycie procesora CPU

[Samouczek: debugowanie dużego użycia procesora CPU](debug-highcpu.md) przeprowadzi Cię przez badanie wysokiego użycia procesora CPU. Za pomocą narzędzia [dotnet-Counters](dotnet-counters.md) można potwierdzić duże użycie procesora CPU. Następnie przeprowadzi Cię przez proces [śledzenia narzędzia do analizy wydajności ( `dotnet-trace` )](dotnet-trace.md) lub systemu Linux `perf` w celu zbierania i wyświetlania profilu użycia procesora CPU.

### <a name="debug-deadlock"></a>Zakleszczenie debugowania

[Samouczek: zakleszczenie debugowania](debug-deadlock.md) pokazuje, w jaki sposób używać narzędzia [dotnet-dump](dotnet-dump.md) do badania wątków i blokad.
