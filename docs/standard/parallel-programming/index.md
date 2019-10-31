---
title: Programowanie równoległe w .NET
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: ae129ef0cb2b331c1eb0220282f21fec6f6fb77d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134149"
---
# <a name="parallel-programming-in-net"></a>Programowanie równoległe w .NET

Wiele komputerów osobistych i stacji roboczych ma wiele rdzeni procesora, które umożliwiają jednoczesne wykonywanie wielu wątków. Aby skorzystać ze sprzętu, możesz zrównoleglanie swój kod w celu dystrybucji pracy na wielu procesorach.

W przeszłości przetwarzanie równoległe wymagało operowania wątkami i blokadami na niskim poziomie. Program Visual Studio i .NET Framework rozszerzają obsługę programowania równoległego dzięki udostępnieniu środowiska uruchomieniowego, typów bibliotek klas i narzędzi diagnostycznych. Te funkcje, które zostały wprowadzone w .NET Framework 4, upraszczają programowanie równoległe. Można napisać wydajny, szczegółowy i skalowalny kod równoległy w naturalnym idiom bez konieczności bezpośredniej pracy z wątkami lub pulą wątków.

Poniższa ilustracja przedstawia ogólny przegląd architektury programowania równoległego w .NET Framework:

![Architektura programowania równoległego .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Tematy pokrewne

|Technologia|Opis|
|----------------|-----------------|
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera dokumentację klasy <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, która obejmuje równoległe wersje `For` i `ForEach` pętle, a także dla klasy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, która reprezentuje preferowany sposób wyrażania operacji asynchronicznych.|
|[Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Implementacja przetwarzania równoległego LINQ to Objects, która znacznie zwiększa wydajność w wielu scenariuszach.|
|[Struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Zawiera łącza do dokumentacji dla kolekcji klas o bezpiecznych wątkowo, lekkich typów synchronizacji i typów d inicjowania z opóźnieniem.|
|[Równoległe narzędzia diagnostyczne](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Zawiera łącza do dokumentacji programu Visual Studio debugger Windows na potrzeby zadań i stosów równoległych oraz dla [wizualizatora współbieżności](/visualstudio/profiling/concurrency-visualizer).|
|[Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|W tym artykule opisano, jak działają moduły partycjonowania i jak konfigurować domyślne moduły partycjonowania lub tworzyć nowe.|
|[Harmonogramy zadań](xref:System.Threading.Tasks.TaskScheduler)|Opisano, jak działa harmonogram zadań i jak można konfigurować domyślny harmonogram.|
|[Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Zawiera krótki przegląd wyrażeń lambda w języku C# i Visual Basic i przedstawia, jak są używane w PLINQ i w bibliotece zadań równoległych.|
|[Dalsze informacje](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Zawiera łącza do dodatkowych informacji i przykładowych zasobów na potrzeby programowania równoległego w programie .NET.|

## <a name="see-also"></a>Zobacz także

- [Przegląd Async](../async.md)
- [Zarządzane wątki](../threading/index.md)
