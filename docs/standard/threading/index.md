---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b1226f51143b912f85e94146948091891376e49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="managed-threading"></a>Zarządzana wątkowość
Czy tworzysz dla komputerów z procesorem jednego lub kilku, mają Twojej aplikacji w celu umożliwienia najbardziej reakcji interakcji z użytkownikiem, nawet wtedy, gdy aplikacja jest aktualnie wykonywanych czynności inne zadania. Używanie wielu wątków wykonywania jest jednym z najbardziej zaawansowanych sposoby Zachowaj reakcji użytkownikowi aplikacji i w tym samym czasie wykorzystanie procesora w między lub nawet podczas zdarzeń użytkownika. Gdy w tej sekcji przedstawiono podstawowe pojęcia związane z wątków, koncentruje się na zarządzanych wątków koncepcje i przy użyciu zarządzanych wątków.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], znacznie upraszcza programowanie wielowątkowe z <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klas, [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nowej kolekcji współbieżnych klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeń nazw, a nowy model programowania opartego na koncepcji zadania, a nie wątków. Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)  
 Omówienie wątków zarządzanych i omówiono, kiedy należy używać wiele wątków.  
  
 [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)  
 Opisano sposób tworzenia, uruchamiania, wstrzymać, wznowić i abort wątków.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Omówienie poziomów synchronizacji, jak uniknąć zakleszczenie i sytuacja wyścigu, jeden procesor i komputerach wieloprocesorowych i inne problemy z wątków.  
  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 Zawiera opis klas zarządzanych, które służy do synchronizowania działania wątków i danych dostępne w różnych wątkach obiektów i zawiera omówienie wątków z puli wątków.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Threading>  
 Zawiera klasy przy użyciu i synchronizacja wątków zarządzanych.  
  
 <xref:System.Collections.Concurrent>  
 Zawiera klasy kolekcji, które są bezpieczne dla użytku z wielu wątków.  
  
 <xref:System.Threading.Tasks>  
 Zawiera klasy służące do tworzenia i planowania zadań jednoczesnych przetwarzania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Zawiera omówienie domen aplikacji i ich użycie za pomocą wspólnej infrastruktury języka.  
  
 [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.  
  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Omówienie zalecanych wzorca dla programowania asynchronicznego w programie .NET.  
  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Wyjaśniono, jak wywoływać metod w wątku puli wątków przy użyciu wbudowanych funkcji obiektów delegowanych.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 W tym artykule opisano równoległe programowania, bibliotek, co upraszcza używanie wielu wątków w aplikacji.  
  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 W tym artykule opisano system uruchamiania zapytań równolegle, aby móc korzystać z wielu procesorów.
