---
title: Używanie wątków i wątkowości
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15f3aa8d2cd7c21fa2b77660cd668d211f8376a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690621"
---
# <a name="using-threads-and-threading"></a>Używanie wątków i wątkowości

Przy użyciu platformy .NET można pisać aplikacje, które wykonują wiele operacji w tym samym czasie. Operacje maksymalnie inne operacje, z których można wykonywać w oddzielnych wątkach, proces ten jest znany jako *wielowątkowość* lub *bezpłatne wątkowości*.  
  
Aplikacje znajdujące się użycie wielowątkowość reakcji użytkownika, danych wejściowych, ponieważ interfejs użytkownika pozostaje aktywne, jak obciążającą procesor zadania wykonywane w oddzielnych wątkach. Wielowątkowość jest również przydatne podczas tworzenia skalowalnych aplikacji, ponieważ użytkownik może dodać wątków w miarę wzrostu obciążenia.

> [!NOTE]
> Aby uzyskać większą kontrolę nad zachowaniem aplikacji wątki, można zarządzać wątki samodzielnie. Jednak począwszy od programu .NET Framework 4, programowanie wielowątkowe zostało znacznie uproszczone dzięki <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klas, [Parallel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md), nowej kolekcji współbieżnych klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeń nazw, a nowy model programowania, który opiera się na koncepcji zadania, a nie wątków. Aby uzyskać więcej informacji, zobacz [programowania równoległego](../parallel-programming/index.md) i [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Instrukcje: Utwórz i Rozpocznij nowy wątek

Utwórz nowy wątek, tworząc nowe wystąpienie klasy <xref:System.Threading.Thread?displayProperty=nameWithType> klasy i podając nazwę metody, która ma zostać wykonany w nowym wątku do konstruktora. Aby rozpocząć utworzony wątek, wywołaj <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji i przykładów, zobacz [Tworzenie wątków i przekazywanie danych na czas rozpoczęcia](creating-threads-and-passing-data-at-start-time.md) artykułu i <xref:System.Threading.Thread> dokumentacja interfejsu API.

## <a name="how-to-stop-a-thread"></a>Instrukcje: Zatrzymywanie wątków

Aby zakończyć wykonywanie wątku, należy użyć <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody. Ta metoda wywołuje <xref:System.Threading.ThreadAbortException> w wątku, na którym jest wywoływana. Aby uzyskać więcej informacji, zobacz [niszczenie wątków](destroying-threads.md).

Począwszy od programu .NET Framework 4, można użyć <xref:System.Threading.CancellationToken?displayProperty=nameWithType> do wspólne anulowanie wątków. Aby uzyskać więcej informacji, zobacz [wspólne anulowanie wątków](canceling-threads-cooperatively.md).

Użyj <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody wątek wywołujący, poczekaj na zakończenie wątku, na którym jest wywoływana metoda.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Instrukcje: Wstrzymaj lub przerwanie wątku

Możesz użyć <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metodę, aby wstrzymać bieżącego wątku na określoną ilość czasu. Można przerwać zablokowany wątek wywołując <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz [wstrzymywanie i przerywanie wątków](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Właściwości wątku

W poniższej tabeli przedstawiono niektóre <xref:System.Threading.Thread> właściwości:  
  
|Właściwość|Opis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Zwraca `true` Jeśli wątek został uruchomiony, a nie został jeszcze zostało zakończone normalnie lub zostało przerwane.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Pobiera lub ustawia atrybut typu wartość logiczna, która wskazuje, czy wątek jest wątku w tle. Wątków w tle są podobne wątki pierwszoplanowe, ale wątek w tle nie uniemożliwić zatrzymywanie procesu. Po zatrzymaniu wszystkie wątki pierwszego planu, które należą do procesu, środowisko uruchomieniowe języka wspólnego kończy proces, wywołując <xref:System.Threading.Thread.Abort%2A> metody na wątkach w tle, które są nadal aktywne. Aby uzyskać więcej informacji, zobacz [pierwszego planu i tła wątków](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Pobiera lub ustawia nazwę wątku. Najczęściej używane do wykrywania określonych wątków podczas debugowania.|  
|<xref:System.Threading.Thread.Priority%2A>|Pobiera lub ustawia <xref:System.Threading.ThreadPriority> wartość, która jest używana przez system operacyjny do określenia priorytetów, planowanie wątków. Aby uzyskać więcej informacji, zobacz [planowania wątków](scheduling-threads.md) i <xref:System.Threading.ThreadPriority> odwołania.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Pobiera <xref:System.Threading.ThreadState> wartość zawierającą bieżące stany wątku.|  

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Wątki i wątkowość](threads-and-threading.md)
- [Programowanie równoległe](../parallel-programming/index.md)
