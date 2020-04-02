---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: c5ca102dc98e50067d39d2f0c51a6ff75e342e9f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588666"
---
# <a name="managed-threading"></a>Zarządzana wątkowość
Niezależnie od tego, czy tworzysz dla komputerów z jednym procesorem lub kilku, chcesz, aby aplikacja zapewniała najbardziej responsywną interakcję z użytkownikiem, nawet jeśli aplikacja obecnie wykonuje inną pracę. Za pomocą wielu wątków wykonywania jest jednym z najbardziej zaawansowanych sposobów, aby aplikacja reaguje na użytkownika i jednocześnie korzystać z procesora pomiędzy lub nawet podczas zdarzeń użytkownika. W tej sekcji przedstawiono podstawowe pojęcia wątków, koncentruje się na zarządzanych pojęć wątków i przy użyciu zarządzanych wątków.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, programowanie <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> wielowątkowe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest znacznie uproszczone z klasami [i, Parallel LINQ (PLINQ),](../../../docs/standard/parallel-programming/introduction-to-plinq.md)nowymi równoczesnymi klasami zbierania w obszarze <xref:System.Collections.Concurrent?displayProperty=nameWithType> nazw i nowym modelem programowania, który jest oparty na koncepcji zadań, a nie wątków. Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)  
 Zawiera omówienie zarządzanych wątków i omówiono, kiedy należy używać wielu wątków.  
  
 [Korzystanie z wątków i wątków](../../../docs/standard/threading/using-threads-and-threading.md)  
 W tym artykule wyjaśniono, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 W tym artykule omówiono poziomy synchronizacji, jak uniknąć zakleszczenia i warunki wyścigu i inne problemy wątkowe.  
  
 [Wątki obiektów i operacji](../../../docs/standard/threading/threading-objects-and-features.md)  
 W tym artykule opisano klasy zarządzane, których można użyć do synchronizacji działań wątków i danych obiektów dostępnych w różnych wątkach i zawiera omówienie wątków puli wątków.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Threading>  
 Zawiera klasy do używania i synchronizowania wątków zarządzanych.  
  
 <xref:System.Collections.Concurrent>  
 Zawiera klasy kolekcji, które są bezpieczne do użycia z wieloma wątkami.  
  
 <xref:System.Threading.Tasks>  
 Zawiera klasy do tworzenia i planowania równoczesnych zadań przetwarzania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Zawiera omówienie domen aplikacji i ich użycia przez infrastrukturę języka wspólnego.  
  
 [Asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.  
  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Zawiera omówienie zalecanego wzorca dla programowania asynchroniowego w .NET.  
  
 [Wywołanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Wyjaśniono, jak wywołać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 W tym artykule opisano biblioteki programowania równoległego, które upraszczają korzystanie z wielu wątków w aplikacjach.  
  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
 W tym artykule opisano system uruchamiania zapytań równolegle, aby skorzystać z wielu procesorów.
