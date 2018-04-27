---
title: Biblioteka zadań równoległych (TPL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
caps.latest.revision: 37
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f63237e139e4be1d8cbb13e1534c894626fd72d
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="task-parallel-library-tpl"></a>Biblioteka zadań równoległych (TPL)
Zadania biblioteki równoległych (TPL) to zestaw typy publiczne i interfejsów API w <xref:System.Threading?displayProperty=nameWithType> i <xref:System.Threading.Tasks?displayProperty=nameWithType> przestrzeni nazw. Zadaniem biblioteki TPL jest zwiększenie produktywności deweloperów przez uproszczenie procesu dodawania równoległości i współbieżności do aplikacji. Biblioteka TPL skaluje stopień współbieżności dynamicznie, aby jak najefektywniej wykorzystać wszystkie dostępne procesory. Ponadto TPL obsługuje partycjonowanie pracy, planowania wątków <xref:System.Threading.ThreadPool>, obsługa anulowania, zarządzanie stanem oraz innych szczegółów niskiego poziomu. Za pomocą TPL można zmaksymalizować wydajność kodu przy jednoczesnym skoncentrowaniu się na pracy, którą program ma wykonać.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], TPL jest preferowany sposób pisania kodu wielowątkowe i równolegle. Jednak nie cały kod nadaje się do przetwarzania równoległego. Na przykład jeśli pętla wykonuje tylko niewielką ilość pracy w każdej iteracji lub nie działa dla wielu iteracji, obciążenie związane z przetwarzaniem równoległym może powodować wolniejsze działanie kodu. Ponadto przetwarzanie równoległe, jak każdy kod wielowątkowy, dodaje złożoności do wykonywania programu. Chociaż TPL upraszcza scenariusze wielowątkowe, zalecamy przynajmniej podstawowe zrozumienie pojęcia wątkowości, na przykład blokad, zakleszczeń i sytuacje wyścigu, aby skutecznie korzystać z TPL.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-|-|  
|[Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Opisuje sposób tworzenia równoległych `for` i `foreach` pętli (`For` i `For Each` w języku Visual Basic).|  
|[Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Opisuje sposób tworzenia i uruchamiania zadań niejawnie za pomocą <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> lub jawnie za pomocą <xref:System.Threading.Tasks.Task> obiekty bezpośrednio.|  
|[Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|Opisuje, jak używać składników przepływu danych w bibliotece przepływu danych TPL w celu obsługi wielu operacji, które muszą się komunikować ze sobą, lub w celu przetwarzania danych, gdy tylko staną się dostępne.|  
|[Korzystanie z modelu TPL z innymi wzorcami asynchronicznymi](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|Opisuje sposób używania TPL z innymi wzorami asynchronicznymi w .NET|  
|[Potencjalne pułapki związane z równoległością danych i zadań](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Opisuje kilka typowych pułapek oraz sposoby unikania ich.|  
|[Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Opisuje sposób osiągnięcia równoległości danych za pomocą zapytań LINQ.|  
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Węzeł najwyższego poziomu dla równoległego programowania .NET.|  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe w środowisku .NET Framework — przykłady](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
