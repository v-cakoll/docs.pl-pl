---
title: Używanie wątków i wątkowości
description: Dowiedz się więcej o używaniu wątków i wątkowości w programie .NET, dzięki czemu możesz pisać aplikacje do wykonywania wielu operacji w tym samym czasie (wielowątkowość).
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: c092994818c9105a555acaf63ceba4b8e99bcada
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663034"
---
# <a name="using-threads-and-threading"></a>Używanie wątków i wątkowości

Za pomocą platformy .NET można pisać aplikacje, które wykonują wiele operacji w tym samym czasie. Operacje z możliwością utrzymywania innych operacji można wykonać w oddzielnych wątkach, procesie znanym *jako* wielowątkowość lub *bezpłatne wątki*.  
  
Aplikacje używające wielowątkowości są wydajniejsze do wprowadzania danych przez użytkownika, ponieważ interfejs użytkownika pozostaje aktywny jako zadania intensywnie korzystające z procesora wykonywane w oddzielnym wątku. Wielowątkowość jest również przydatna podczas tworzenia skalowalnych aplikacji, ponieważ można dodać wątki w miarę wzrostu obciążenia.

> [!NOTE]
> Jeśli potrzebujesz większej kontroli nad zachowaniem wątków aplikacji, możesz samodzielnie zarządzać wątkami. Jednak począwszy od .NET Framework 4, programowanie wielowątkowe jest znacznie uproszczone przy użyciu <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klas i, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), nowych klas kolekcji współbieżnych w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw oraz nowy model programowania oparty na koncepcji zadań, a nie w wątkach. Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../parallel-programming/index.md) i [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Instrukcje: Tworzenie i uruchamianie nowego wątku

Tworzysz nowy wątek, tworząc nowe wystąpienie <xref:System.Threading.Thread?displayProperty=nameWithType> klasy i dostarczając nazwę metody, która ma zostać wykonana w nowym wątku do konstruktora. Aby uruchomić utworzony wątek, wywołaj <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metodę. Aby uzyskać więcej informacji i przykładów, zobacz artykuł [Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia](creating-threads-and-passing-data-at-start-time.md) i <xref:System.Threading.Thread> Informacje o interfejsie API.

## <a name="how-to-stop-a-thread"></a>Instrukcje: zatrzymywanie wątku

Aby zakończyć wykonywanie wątku, użyj <xref:System.Threading.CancellationToken?displayProperty=nameWithType> . Zapewnia jednolity sposób, aby zatrzymać wątki wspólnie. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](cancellation-in-managed-threads.md).

Czasami nie jest możliwe zatrzymywanie wątku wspólnie, ponieważ uruchamia kod innej firmy, który nie został zaprojektowany w celu uzyskania spółdzielni. W takim przypadku możesz chcieć przerwać jego wykonywanie. Aby przerwać wykonywanie przymusu wątku, w .NET Framework można użyć <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody. Ta metoda podnosi wartość <xref:System.Threading.ThreadAbortException> w wątku, w którym jest wywoływana. Aby uzyskać więcej informacji, zobacz [niszczenie wątków](destroying-threads.md). <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda nie jest obsługiwana w programie .NET Core. Jeśli konieczne jest zakończenie wykonywania kodu innej firmy w programie .NET Core, należy uruchomić go w osobnym procesie i użyć <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

<xref:System.Threading.CancellationToken?displayProperty=nameWithType>Nie jest dostępny przed .NET Framework 4. Aby zatrzymać wątek w starszych wersjach .NET Framework, należy ręcznie zaimplementować z pomocą technik synchronizacji wątków. Na przykład można utworzyć pole wartości logicznej volatile `shouldStop` i użyć go do żądania kodu wykonywanego przez wątek w celu zatrzymania. Aby uzyskać więcej informacji, zobacz [nietrwałe](../../csharp/language-reference/keywords/volatile.md) w odwołaniach w języku C# i <xref:System.Threading.Volatile?displayProperty=nameWithType> .

Użyj <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody, aby wątek wywołujący oczekiwał na zakończenie zatrzymania wątku.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Instrukcje: Wstrzymywanie lub przerywanie wątku

Użyj metody, <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> Aby wstrzymać bieżący wątek przez określony czas. Możesz przerwać zablokowany wątek, wywołując <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodę. Aby uzyskać więcej informacji, zobacz [Wstrzymywanie i przerywanie wątków](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Właściwości wątku

W poniższej tabeli przedstawiono niektóre z tych <xref:System.Threading.Thread> Właściwości:  
  
|Właściwość|Opis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Zwraca `true` czy wątek został uruchomiony i nie został jeszcze zakończony normalnie lub przerwany.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Pobiera lub ustawia wartość logiczną wskazującą, czy wątek jest wątkiem w tle. Wątki w tle są takie same jak wątki pierwszego planu, ale wątek w tle nie uniemożliwia zatrzymywania procesu. Gdy wszystkie wątki pierwszego planu, które należą do procesu, przestaną działać, środowisko uruchomieniowe języka wspólnego kończy proces przez wywołanie <xref:System.Threading.Thread.Abort%2A> metody w wątkach w tle, które są nadal aktywne. Aby uzyskać więcej informacji, zobacz [wątki pierwszego planu i tła](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Pobiera lub ustawia nazwę wątku. Najczęściej używane do odnajdywania pojedynczych wątków podczas debugowania.|  
|<xref:System.Threading.Thread.Priority%2A>|Pobiera lub ustawia <xref:System.Threading.ThreadPriority> wartość używaną przez system operacyjny do określania priorytetów planowania wątków. Aby uzyskać więcej informacji, zobacz [Planowanie wątków](scheduling-threads.md) i <xref:System.Threading.ThreadPriority> odwołanie.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Pobiera <xref:System.Threading.ThreadState> wartość zawierającą bieżące Stany wątku.|  

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Wątki i wątkowość](threads-and-threading.md)
- [Programowanie równoległe](../parallel-programming/index.md)
