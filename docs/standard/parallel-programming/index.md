---
title: "Programowanie równoległe w .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 554de5d65929afc03b57bdc604ceeb6ac35362d4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="parallel-programming-in-net"></a>Programowanie równoległe w .NET
Wiele komputerów osobistych i stacji roboczych ma dwa lub cztery rdzenie (czyli procesorów), które umożliwiają jednoczesne wykonywane wielu wątków. Komputery w najbliższej przyszłości powinny mieć znacznie więcej rdzeni. Aby skorzystać z możliwości dzisiejszego i jutrzejszego sprzętu, można zrównoleglić kod w celu rozłożenia pracy na wiele procesorów. W przeszłości przetwarzanie równoległe wymagało operowania wątkami i blokadami na niskim poziomie. [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)]i [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rozszerzają obsługę programowania równoległego, podając nowe środowisko uruchomieniowe, nowe typy biblioteki klas i nowe narzędzia diagnostyczne. Te funkcje upraszczają równoległe programowanie, dzięki czemu można tworzyć wydajny, precyzyjny i skalowalny kod przetwarzania równoległego w języku naturalnym bez konieczności bezpośredniej pracy z wątkami lub pulą wątków. Następująca ilustracja przedstawia ogólne omówienie architektury programowania równoległego w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
 ![Architektura programowania równoległego .NET](../../../docs/standard/parallel-programming/media/tpl-architecture.png "TPL_Architecture")  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Technologia|Opis|  
|----------------|-----------------|  
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera dokumentacja <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> klasy, która zawiera wersje równoległych `For` i `ForEach` pętle, a także do <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klasy, która reprezentuje preferowany sposób express operacji asynchronicznych.|  
|[Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Implementacja przetwarzania równoległego LINQ to Objects, która znacznie zwiększa wydajność w wielu scenariuszach.|  
|[Struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Zawiera łącza do dokumentacji dla kolekcji klas o bezpiecznych wątkowo, lekkich typów synchronizacji i typów d inicjowania z opóźnieniem.|  
|[Równoległe narzędzia diagnostyczne](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Zawiera łącza do dokumentacji systemu windows debugera programu Visual Studio dla zadań i stosów równoległych i [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer), który zawiera zestaw widoków w [!INCLUDE[vsprvsts](../../../includes/vsprvsts-md.md)] profilera używanego do debugowania i dostrajania wykonywanie równoległego kodu.|  
|[Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|W tym artykule opisano, jak działają moduły partycjonowania i jak konfigurować domyślne moduły partycjonowania lub tworzyć nowe.|  
|[Planiści zadań](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|Opisano, jak działa harmonogram zadań i jak można konfigurować domyślny harmonogram.|  
|[Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Zawiera krótki przegląd wyrażeń lambda w języku C# i Visual Basic i przedstawia, jak są używane w PLINQ i w bibliotece zadań równoległych.|  
|[Dalsze informacje](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Zawiera łącza do dodatkowej dokumentacji i przykładowych zasobów do programowania równoległego w .NET Framework.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce programowania równoległego: opis i stosowanie równoległe wzorce za pomocą programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=185142)  
 [Programowanie równoległe w środowisku .NET Framework — przykłady](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
