---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: d6b8a0a4e16aa3169888958fa1376bfa61526dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137929"
---
# <a name="managed-threading"></a>Zarządzana wątkowość
Niezależnie od tego, czy tworzysz komputery z jednym procesorem, czy kilkoma, aplikacja ma zapewniać najbardziej responsywną interakcję z użytkownikiem, nawet jeśli aplikacja wykonuje obecnie inną pracę. Przy użyciu wielu wątków wykonywania jest jednym z najbardziej zaawansowanych sposobów, aby utrzymać aplikację reaguje na użytkownika i jednocześnie korzystać z procesora pomiędzy lub nawet podczas zdarzeń użytkownika. Podczas gdy w tej sekcji wprowadza podstawowe pojęcia wątków, koncentruje się na zarządzanych wątków i przy użyciu zarządzanych wątków.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, programowanie wielowątkowe <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest znacznie uproszczone za pomocą i klas, Parallel <xref:System.Collections.Concurrent?displayProperty=nameWithType> [LINQ (PLINQ),](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)nowych klas kolekcji równoczesnych w przestrzeni nazw i nowego modelu programowania, który jest oparty na koncepcji zadań, a nie wątków. Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)  
 Zawiera omówienie zarządzanych wątków i omówiono, kiedy należy używać wielu wątków.  
  
 [Korzystanie z wątków i wątków](../../../docs/standard/threading/using-threads-and-threading.md)  
 W tym artykule wyjaśniono, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 W tym artykule omówiono poziomy synchronizacji, jak uniknąć zakleszczenia i warunków wyścigu i innych problemów wątków.  
  
 [Wątkowe obiekty i operacje](../../../docs/standard/threading/threading-objects-and-features.md)  
 Opisuje klasy zarządzane, których można użyć do synchronizacji działań wątków i danych obiektów dostępnych w różnych wątkach i zawiera omówienie wątków puli wątków.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Threading>  
 Zawiera klasy do używania i synchronizowania wątków zarządzanych.  
  
 <xref:System.Collections.Concurrent>  
 Zawiera klasy kolekcji, które są bezpieczne do użytku z wieloma wątkami.  
  
 <xref:System.Threading.Tasks>  
 Zawiera klasy do tworzenia i planowania równoczesnych zadań przetwarzania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Zawiera omówienie domen aplikacji i ich używania przez infrastrukturę języka wspólnego.  
  
 [Asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.  
  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Zawiera omówienie zalecanego wzorca programowania asynchronicznego w programie .NET.  
  
 [Wywołanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 W tym artykule wyjaśniono, jak wywoływać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 Opisuje równoległe biblioteki programowania, które upraszczają korzystanie z wielu wątków w aplikacjach.  
  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 W tym artykule opisano system do uruchamiania kwerend równolegle, aby skorzystać z wielu procesorów.
