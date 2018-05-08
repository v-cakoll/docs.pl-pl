---
title: Wątkowość (C#)
ms.date: 07/20/2015
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
ms.openlocfilehash: 9f1c7071972d8e449bc06054fbe6d70e447b694f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="threading-c"></a>Wątkowość (C#)
Wątkowość Włącza program C# do wykonania równoczesnych przetwarzania, aby zrobić więcej niż jedną operację naraz. Można na przykład użyć wątkowość do monitorowania danych wejściowych od użytkownika, wykonaj zadania w tle i obsługi jednoczesnych strumieni danych wejściowych.  
  
 Wątki mieć następujące właściwości:  
  
-   Wątki włączyć program do przetwarzania współbieżnych.  
  
-   .NET Framework <xref:System.Threading> sprawia, że przestrzeń nazw za pomocą wątków jest łatwiejsze.  
  
-   Wątki współużytkują zasoby aplikacji. Aby uzyskać więcej informacji, zobacz [za pomocą wątków i wątki](../../../../../docs/standard/threading/using-threads-and-threading.md).  
  
 Domyślnie program C# ma jeden wątek. Jednak pomocnicze wątków można tworzyć i używane do wykonywania kodu równolegle z podstawowym wątku. Wątki te są często nazywane *wątków roboczych*.  
  
 Wątki robocze może służyć do wykonywania zadań czasochłonne lub wrażliwego na czas bez angażowania podstawowy wątku. Na przykład wątków roboczych są często używane w aplikacji serwerowych do spełnienia żądań przychodzących bez oczekiwania na ukończenie poprzedniego żądania. Wątki robocze są również używane do wykonywania zadań "tła" w aplikacjach komputerowych, aby wątku głównego--dyski elementy interfejsu użytkownika — pozostaje reakcji na działanie użytkownika.  
  
 Wątkowość rozwiązuje problemy z przepływność i elastyczność, ale mogą też stać udostępniania zasobów problemy, takie jak zakleszczenie i sytuacja wyścigu. Wiele wątków są najlepsze w przypadku zadania, które wymagają różnych zasobów, takich jak dojścia do plików i połączeń sieciowych. Przypisywanie wiele wątków do pojedynczego zasobu jest może spowodować problemy z synchronizacją, a o wątków często blokowane podczas oczekiwania na inne wątki pozbawia sensu używanie wielu wątków.  
  
 Wspólna strategia polega na użyciu wątków roboczych do wykonania czasochłonne wrażliwego na czas zadania, które nie wymagają wielu zasoby używane przez inne wątki. Oczywiście niektórych zasobów w programie muszą być dostępne przez wiele wątków. W tych przypadkach <xref:System.Threading> przestrzeń nazw zawiera klasy dla synchronizacja wątków. Te klasy mają <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.ManualResetEvent>.  
  
 Można zsynchronizować działania wiele wątków niektórych lub wszystkich tych klas, ale niektóre Obsługa wątkowości jest obsługiwany przez język C#. Na przykład [instrukcji "Lock"](../../../../csharp/language-reference/keywords/lock-statement.md) udostępnia funkcje synchronizacji przy użyciu niejawnego <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], znacznie upraszcza programowanie wielowątkowe z <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klas, [równoległe LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), nowej kolekcji współbieżnych klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeń nazw, a nowy model programowania opartego na koncepcji zadania, a nie wątków. Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../../../docs/standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Aplikacje wielowątkowe (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|Opisuje sposób tworzenia i używania wątków.|  
|[Parametry i wartości zwracane dla procedur wielowątkowości (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Opisuje sposób przekazywania i zwracać parametrów z aplikacji wielowątkowych.|  
|[Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Przedstawia sposób tworzenia prostej aplikacji wielowątkowych.|  
|[Synchronizacja wątku (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|Zawiera opis sposobu kontrolowania interakcji wątków.|  
|[Czasomierze wątków (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|Opisuje sposób uruchamiania procedur w oddzielnych wątkach w ustalonych odstępach czasu.|  
|[Wątku puli (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|Opisuje sposób korzystanie z puli wątków roboczych, które są zarządzane przez system.|  
|[Porady: Korzystanie z puli wątków (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Pokazuje zsynchronizowane używanie wielu wątków w puli wątków.|  
|[Wątkowość](../../../../../docs/standard/threading/index.md)|Opisuje sposób wdrożenia wątkowość w programie .NET Framework.|
