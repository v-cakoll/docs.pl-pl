---
title: Programowanie równoległe w .NET
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: ae129ef0cb2b331c1eb0220282f21fec6f6fb77d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134149"
---
# <a name="parallel-programming-in-net"></a>Programowanie równoległe w .NET

Wiele komputerów osobistych i stacji roboczych ma wiele rdzeni procesora CPU, które umożliwiają jednoczesne wykonywanie wielu wątków. Aby korzystać ze sprzętu, można równoległykod, aby rozpowszechniać pracę na wielu procesorach.

W przeszłości przetwarzanie równoległe wymagało operowania wątkami i blokadami na niskim poziomie. Visual Studio i .NET Framework zwiększyć obsługę programowania równoległego, zapewniając czas wykonywania, typy bibliotek klas i narzędzi diagnostycznych. Te funkcje, które zostały wprowadzone za pomocą .NET Framework 4, upraszczają tworzenie równoległe. Można napisać wydajne, drobnoziarniste i skalowalne równoległe kodu w naturalnym idiom bez konieczności pracy bezpośrednio z wątków lub puli wątków.

Poniższa ilustracja zawiera ogólny przegląd architektury programowania równoległego w programie .NET Framework:

![Architektura programowania równoległego .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Tematy pokrewne

|Technologia|Opis|
|----------------|-----------------|
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera dokumentację <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> dla klasy, która `For` `ForEach` zawiera równoległe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> wersje i pętli, a także dla klasy, która reprezentuje preferowany sposób wyrażania operacji asynchronicznych.|
|[Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Implementacja przetwarzania równoległego LINQ to Objects, która znacznie zwiększa wydajność w wielu scenariuszach.|
|[Struktury danych dla Programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Zawiera łącza do dokumentacji dla kolekcji klas o bezpiecznych wątkowo, lekkich typów synchronizacji i typów d inicjowania z opóźnieniem.|
|[Równoległe narzędzia diagnostyczne](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Zawiera łącza do dokumentacji dla okien debugera programu Visual Studio dla zadań i stosów równoległych oraz [wizualizatora współbieżności](/visualstudio/profiling/concurrency-visualizer).|
|[Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|W tym artykule opisano, jak działają moduły partycjonowania i jak konfigurować domyślne moduły partycjonowania lub tworzyć nowe.|
|[Harmonogramy zadań](xref:System.Threading.Tasks.TaskScheduler)|Opisano, jak działa harmonogram zadań i jak można konfigurować domyślny harmonogram.|
|[Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Zawiera krótki przegląd wyrażeń lambda w języku C# i Visual Basic i przedstawia, jak są używane w PLINQ i w bibliotece zadań równoległych.|
|[Dalsze informacje](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Zawiera łącza do dodatkowych informacji i przykładowe zasoby do programowania równoległego w programie .NET.|

## <a name="see-also"></a>Zobacz też

- [Przegląd asynchronicznego](../async.md)
- [Zarządzana wątkowość](../threading/index.md)
