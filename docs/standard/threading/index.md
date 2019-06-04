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
ms.openlocfilehash: f51920bceef6e83af4f6ef029eb49ae495a58b9b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490847"
---
# <a name="managed-threading"></a>Zarządzana wątkowość
Czy jest tworzona dla komputerów z procesorem jeden lub kilka, ma aplikację w celu zapewnienia najbardziej elastyczny interakcji z użytkownikiem, nawet wtedy, gdy aplikacja wykonuje aktualnie inne prace. Przy użyciu wielu wątków wykonania jest jednym z najbardziej zaawansowanych sposobów prace nad aplikacją reagować na działania użytkownika i w tym samym czasie wykorzystanie procesora pomiędzy lub nawet w trakcie zdarzenia użytkownika. Gdy ten rudział przedstawia podstawowe pojęcia wątkowości, koncentruje się na zarządzanym pojęcia wielowątkowości i przy użyciu zarządzanych wątkach.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 4, programowanie wielowątkowe znacznie zostało uproszczone dzięki <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klas, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nowej kolekcji współbieżnych klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw , a nowy model programowania, który opiera się na koncepcji zadania, a nie wątków. Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)  
 Zawiera omówienie zarządzanych wątkach i omówiono, kiedy należy używać wielu wątków.  
  
 [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)  
 Opis sposobu tworzenia, uruchamiania, wstrzymać, wznowić i przerwać wątków.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 W tym artykule omówiono poziomy synchronizacji, wystawia sposoby unikania zakleszczeń i sytuacje wyścigu, a inne wątki.  
  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 Zawiera opis klas zarządzanych, które służy do synchronizowania działania wątków i dane obiektami w różnych wątkach i zawiera omówienie wątków z puli wątków.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Threading>  
 Zawiera klasy dla przy użyciu i synchronizowanie zarządzanych wątków.  
  
 <xref:System.Collections.Concurrent>  
 Zawiera klasy kolekcji, które są bezpiecznie używać w wielu wątkach.  
  
 <xref:System.Threading.Tasks>  
 Zawiera klasy służące do tworzenia i planowania zadań jednoczesnych przetwarzania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Zawiera omówienie domen aplikacji i ich użycie przez Common Language Infrastructure.  
  
 [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.  
  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Zawiera omówienie zalecany wzorzec dla programowania asynchronicznego w .NET.  
  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Wyjaśnia, jak wywoływać metody dla wątku za pomocą wbudowanych funkcji obiektów delegowanych z puli wątków.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 W tym artykule opisano równoległego programowania bibliotek, które upraszczają korzystanie z wielu wątków w aplikacjach.  
  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 W tym artykule opisano systemem do uruchamiania zapytań równolegle, aby móc korzystać z wielu procesorów.
