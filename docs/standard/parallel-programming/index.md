---
title: Programowanie równoległe w .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 372ffd7e17f60b8045cd5f89d52456c5f9655de1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802306"
---
# <a name="parallel-programming-in-net"></a>Programowanie równoległe w .NET

Wiele komputerów osobistych i stacji roboczych ma wiele rdzeni procesora CPU, które umożliwiają jednoczesne wykonywane wielu wątków. Komputery w najbliższej przyszłości powinny mieć znacznie więcej rdzeni. Aby skorzystać z możliwości dzisiejszego i jutrzejszego sprzętu, można zrównoleglić kod w celu rozłożenia pracy na wiele procesorów. W przeszłości przetwarzanie równoległe wymagało operowania wątkami i blokadami na niskim poziomie. Visual Studio 2010 oraz programu .NET Framework 4 należy poprawić obsługę programowania równoległego, zapewniając nowego środowiska uruchomieniowego, nowych typów bibliotek klas i nowych narzędzi diagnostycznych. Te funkcje upraszczają równoległe programowanie, dzięki czemu można tworzyć wydajny, precyzyjny i skalowalny kod przetwarzania równoległego w języku naturalnym bez konieczności bezpośredniej pracy z wątkami lub pulą wątków. Poniższa ilustracja zawiera ogólne omówienie architektury programowania równoległego w .NET Framework 4.

 ![Architektura programowania równoległego w .NET](./media/tpl-architecture.png "TPL_Architecture")

## <a name="related-topics"></a>Tematy pokrewne

|Technologia|Opis|
|----------------|-----------------|
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera dokumentację dotyczącą <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> klasy, która zawiera wersje równoległe `For` i `ForEach` pętli, a także <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klasy, która reprezentuje preferowanym sposób wyrażania operacji asynchronicznych.|
|[Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Implementacja przetwarzania równoległego LINQ to Objects, która znacznie zwiększa wydajność w wielu scenariuszach.|
|[Struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Zawiera łącza do dokumentacji dla kolekcji klas o bezpiecznych wątkowo, lekkich typów synchronizacji i typów d inicjowania z opóźnieniem.|
|[Równoległe narzędzia diagnostyczne](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Oferuje łącza do dokumentacji okien debugera programu Visual Studio do zadań i stosów przetwarzania równoległego oraz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).|
|[Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|W tym artykule opisano, jak działają moduły partycjonowania i jak konfigurować domyślne moduły partycjonowania lub tworzyć nowe.|
|[Planiści zadań](https://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|Opisano, jak działa harmonogram zadań i jak można konfigurować domyślny harmonogram.|
|[Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Zawiera krótki przegląd wyrażeń lambda w języku C# i Visual Basic i przedstawia, jak są używane w PLINQ i w bibliotece zadań równoległych.|
|[Dalsze informacje](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Zawiera łącza do dodatkowych informacji i przykładowych zasobów do programowania równoległego w .NET.|

## <a name="see-also"></a>Zobacz także

- [Async — omówienie](../async.md)
- [Zarządzana wątkowość](../threading/index.md)
