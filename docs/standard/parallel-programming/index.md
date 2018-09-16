---
title: Programowanie równoległe w .NET
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d1cd0b797373da4cab59484e3e6302927d821ed
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676736"
---
# <a name="parallel-programming-in-net"></a>Programowanie równoległe w .NET

Wiele komputerów osobistych i stacji roboczych ma wiele rdzeni procesora CPU, które umożliwiają jednoczesne wykonywane wielu wątków. Aby móc korzystać z urządzeń, można zrównoleglić kod w celu rozłożenia pracy na wiele procesorów.

W przeszłości przetwarzanie równoległe wymagało operowania wątkami i blokadami na niskim poziomie. Visual Studio i .NET Framework pozwala zwiększyć obsługę programowania równoległego, dostarczając środowisko uruchomieniowe, typy biblioteki klas i narzędzia diagnostyczne. Te funkcje, które zostały wprowadzone w programie .NET Framework 4, upraszczają równoległe programowanie. Można napisać wydajny, precyzyjny i skalowalny kod przetwarzania równoległego w języku naturalnym, bez konieczności bezpośredniej pracy z wątkami lub pulą wątków.

Poniższa ilustracja zawiera przegląd wysokiego poziomu architektury programowania równoległego w .NET Framework:

![Architektura programowania równoległego w .NET](./media/tpl-architecture.png)

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
