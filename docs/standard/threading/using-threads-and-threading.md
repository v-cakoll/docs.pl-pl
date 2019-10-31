---
title: Używanie wątków i wątkowości
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 863fa565f7c107214273912a6d110b7664bffe6b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131499"
---
# <a name="using-threads-and-threading"></a>Używanie wątków i wątkowości

Za pomocą platformy .NET można pisać aplikacje, które wykonują wiele operacji w tym samym czasie. Operacje z możliwością utrzymywania innych operacji można wykonać w oddzielnych wątkach, procesie znanym *jako* wielowątkowość lub *bezpłatne wątki*.  
  
Aplikacje używające wielowątkowości są wydajniejsze do wprowadzania danych przez użytkownika, ponieważ interfejs użytkownika pozostaje aktywny jako zadania intensywnie korzystające z procesora wykonywane w oddzielnym wątku. Wielowątkowość jest również przydatna podczas tworzenia skalowalnych aplikacji, ponieważ można dodać wątki w miarę wzrostu obciążenia.

> [!NOTE]
> Jeśli potrzebujesz większej kontroli nad zachowaniem wątków aplikacji, możesz samodzielnie zarządzać wątkami. Jednak począwszy od .NET Framework 4, programowanie wielowątkowe jest znacznie uproszczone przy użyciu klas <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Parallel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md), nowych klas kolekcji współbieżnych w przestrzeni nazw <xref:System.Collections.Concurrent?displayProperty=nameWithType> i nowego modelu programowania jest to oparte na koncepcji zadań, a nie w wątkach. Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../parallel-programming/index.md) i [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Instrukcje: Tworzenie i uruchamianie nowego wątku

Tworzysz nowy wątek, tworząc nowe wystąpienie klasy <xref:System.Threading.Thread?displayProperty=nameWithType> i dostarczając nazwę metody, która ma zostać wykonana w nowym wątku do konstruktora. Aby uruchomić utworzony wątek, wywołaj metodę <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji i przykładów, zobacz artykuł [Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia](creating-threads-and-passing-data-at-start-time.md) oraz informacje o interfejsie API <xref:System.Threading.Thread>.

## <a name="how-to-stop-a-thread"></a>Instrukcje: zatrzymywanie wątku

Aby zakończyć wykonywanie wątku, użyj metody <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Ta metoda podnosi <xref:System.Threading.ThreadAbortException> w wątku, w którym jest wywoływana. Aby uzyskać więcej informacji, zobacz [niszczenie wątków](destroying-threads.md).

Począwszy od .NET Framework 4, można użyć <xref:System.Threading.CancellationToken?displayProperty=nameWithType>, aby anulować wątki wspólnie. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](cancellation-in-managed-threads.md).

Użyj metody <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, aby wątek wywołujący oczekiwał na zakończenie wątku, w którym wywoływana jest metoda.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Instrukcje: Wstrzymywanie lub przerywanie wątku

Użyj metody <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>, aby wstrzymać bieżący wątek przez określony czas. Możesz przerwać zablokowany wątek, wywołując metodę <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Wstrzymywanie i przerywanie wątków](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Właściwości wątku

W poniższej tabeli przedstawiono niektóre z <xref:System.Threading.Thread> właściwości:  
  
|Właściwość|Opis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Zwraca `true`, jeśli wątek został uruchomiony i nie został jeszcze zakończony normalnie lub przerwany.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Pobiera lub ustawia wartość logiczną wskazującą, czy wątek jest wątkiem w tle. Wątki w tle są takie same jak wątki pierwszego planu, ale wątek w tle nie uniemożliwia zatrzymywania procesu. Gdy wszystkie wątki pierwszego planu, które należą do procesu, przestaną działać, środowisko uruchomieniowe języka wspólnego kończy proces, wywołując metodę <xref:System.Threading.Thread.Abort%2A> w wątkach w tle, które są nadal aktywne. Aby uzyskać więcej informacji, zobacz [wątki pierwszego planu i tła](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Pobiera lub ustawia nazwę wątku. Najczęściej używane do odnajdywania pojedynczych wątków podczas debugowania.|  
|<xref:System.Threading.Thread.Priority%2A>|Pobiera lub ustawia wartość <xref:System.Threading.ThreadPriority>, która jest używana przez system operacyjny do określania priorytetów planowania wątków. Aby uzyskać więcej informacji, zobacz [Planowanie wątków](scheduling-threads.md) i odwołanie <xref:System.Threading.ThreadPriority>.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Pobiera <xref:System.Threading.ThreadState> wartość zawierającą bieżące Stany wątku.|  

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Wątki i wątkowość](threads-and-threading.md)
- [Programowanie równoległe](../parallel-programming/index.md)
