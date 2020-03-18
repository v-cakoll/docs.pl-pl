---
title: Omówienie narzędzi diagnostycznych - .NET Core
description: Omówienie narzędzi i technik dostępnych do diagnozowania aplikacji .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399050"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Jakie narzędzia diagnostyczne są dostępne w .NET Core?

Oprogramowanie nie zawsze zachowuje się tak, jak można się spodziewać, ale program .NET Core ma narzędzia i interfejsy API, które pomogą ci szybko i skutecznie zdiagnozować te problemy.

Ten artykuł pomoże Ci znaleźć różne narzędzia, których potrzebujesz.

## <a name="managed-debuggers"></a>Debugery zarządzane

[Zarządzane debugerzki](managed-debuggers.md) umożliwiają interakcję z programem. Wstrzymywanie, stopniowe wykonywanie, badanie i wznawianie zapewnia wgląd w zachowanie kodu. Debuger jest pierwszym wyborem do diagnozowania problemów funkcjonalnych, które można łatwo odtworzyć.

## <a name="logging-and-tracing"></a>Rejestrowanie i śledzenie

[Rejestrowanie i śledzenie](logging-tracing.md) są powiązanymi technikami. Odnoszą się one do kodu instrumentastru, aby utworzyć pliki dziennika. Pliki rejestrują szczegóły tego, co robi program. Szczegóły te mogą być wykorzystane do diagnozowania najbardziej złożonych problemów. W połączeniu z znacznikami czasu techniki te są również cenne w badaniach wydajności.

## <a name="unit-testing"></a>Testy jednostkowe

[Testowanie jednostkowe](../testing/index.md) jest kluczowym elementem ciągłej integracji i wdrażania wysokiej jakości oprogramowania. Testy jednostkowe mają na celu zapewnienie wczesnego ostrzegania po złamaniu czegoś.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>Narzędzia globalne diagnostyki .NET Core dotnet

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-counters](dotnet-counters.md) jest narzędziem do monitorowania wydajności do monitorowania kondycji pierwszego poziomu i badania wydajności. Obserwuje wartości licznika wydajności opublikowane <xref:System.Diagnostics.Tracing.EventCounter> za pośrednictwem interfejsu API. Na przykład można szybko monitorować takie rzeczy, jak użycie procesora CPU lub szybkość wyjątków zgłaszanych w aplikacji .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

Narzędzie [dotnet-dump](dotnet-dump.md) jest sposobem zbierania i analizowania zrzutów rdzenia systemu Windows i Linux bez natywnego debugera.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core zawiera to, co nazywa się, `EventPipe` za pośrednictwem którego dane diagnostyczne są udostępniane. Narzędzie [dotnet-trace](dotnet-trace.md) umożliwia korzystanie z interesujących danych profilowania z aplikacji, które mogą pomóc w scenariuszach, w których należy roots powodować aplikacje działa wolno.

## <a name="net-core-diagnostics-tutorials"></a>Samouczki dotyczące diagnostyki platformy .NET Core

### <a name="debug-a-memory-leak"></a>Debugowanie przecieku pamięci

[Samouczek: Debugowanie przeciek pamięci](debug-memory-leak.md) przechodzi przez znalezienie przeciek pamięci. Narzędzie [dotnet-liczniki](dotnet-counters.md) służy do potwierdzenia wycieku i narzędzie [dotnet-dump](dotnet-dump.md) służy do diagnozowania wycieku.
