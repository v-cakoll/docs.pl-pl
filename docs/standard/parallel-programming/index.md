---
title: Programowanie równoległe w .NET
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: 75f5ded48acfb82b0327ead3880ee23e6ef4bc2f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588152"
---
# <a name="parallel-programming-in-net"></a>Programowanie równoległe w .NET

Wiele komputerów osobistych i stacji roboczych ma wiele rdzeni procesora, które umożliwiają jednoczesne wykonanie wielu wątków. Aby skorzystać ze sprzętu, można zrównoleglić kodu do dystrybucji pracy na wielu procesorach.

W przeszłości przetwarzanie równoległe wymagało operowania wątkami i blokadami na niskim poziomie. Visual Studio i .NET Framework zwiększają obsługę programowania równoległego, zapewniając środowisko uruchomieniowe, typy bibliotek klas i narzędzia diagnostyczne. Te funkcje, które zostały wprowadzone wraz z .NET Framework 4, upraszczają równoległe opracowywanie. Można napisać wydajny, drobnoziarnisty i skalowalny kod równoległy w naturalnym idiomie bez konieczności pracy bezpośrednio z wątkami lub pulą wątków.

Poniższa ilustracja zawiera omówienie wysokiego poziomu architektury programowania równoległego w programie .NET Framework:

![Architektura programowania równoległego .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Tematy pokrewne

|Technologia|Opis|
|----------------|-----------------|
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera dokumentację <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> dla klasy, która `For` `ForEach` zawiera równoległe wersje <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i pętli, a także dla klasy, która reprezentuje preferowany sposób wyrażania operacji asynchronicznych.|
|[Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)|Implementacja przetwarzania równoległego LINQ to Objects, która znacznie zwiększa wydajność w wielu scenariuszach.|
|[Struktury danych dla Programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Zawiera łącza do dokumentacji dla kolekcji klas o bezpiecznych wątkowo, lekkich typów synchronizacji i typów d inicjowania z opóźnieniem.|
|[Równoległe narzędzia diagnostyczne](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Zawiera łącza do dokumentacji dla okien debugera programu Visual Studio dla zadań i stosów równoległych oraz dla [wizualizatora współbieżności.](/visualstudio/profiling/concurrency-visualizer)|
|[Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|W tym artykule opisano, jak działają moduły partycjonowania i jak konfigurować domyślne moduły partycjonowania lub tworzyć nowe.|
|[Harmonogramy zadań](xref:System.Threading.Tasks.TaskScheduler)|Opisano, jak działa harmonogram zadań i jak można konfigurować domyślny harmonogram.|
|[Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Zawiera krótki przegląd wyrażeń lambda w języku C# i Visual Basic i przedstawia, jak są używane w PLINQ i w bibliotece zadań równoległych.|
|[Dalsze informacje](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Zawiera łącza do dodatkowych informacji i przykładowych zasobów do programowania równoległego w programie .NET.|

## <a name="see-also"></a>Zobacz też

- [Przegląd Async](../async.md)
- [Zarządzane wątki](../threading/index.md)
