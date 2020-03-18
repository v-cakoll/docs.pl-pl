---
title: Używanie wątków i wątkowości
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 1d487edff2cdc2e63f81963bfaa1f68a06e5b36e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75936842"
---
# <a name="using-threads-and-threading"></a>Używanie wątków i wątkowości

Za pomocą programu .NET można zapisywać aplikacje, które wykonują wiele operacji w tym samym czasie. Operacje z potencjałem utrzymywania innych operacji można wykonać na oddzielnych wątków, proces znany jako *wielowątkowości* lub *wątków swobodnego*.  
  
Aplikacje, które używają multithreading są bardziej elastyczne do wprowadzania danych przez użytkownika, ponieważ interfejs użytkownika pozostaje aktywny jako zadania intensywnie korzystających z procesora wykonywane w oddzielnych wątków. Wielowątkowość jest również przydatne podczas tworzenia skalowalnych aplikacji, ponieważ można dodawać wątki w miarę zwiększania obciążenia.

> [!NOTE]
> Jeśli potrzebujesz większej kontroli nad zachowaniem wątków aplikacji, można samodzielnie zarządzać wątkami. Jednak począwszy od .NET Framework 4, programowanie wielowątkowe <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest znacznie uproszczone z i klas, [Parallel LINQ (PLINQ),](../parallel-programming/parallel-linq-plinq.md)nowe klasy kolekcji równoczesnych w przestrzeni <xref:System.Collections.Concurrent?displayProperty=nameWithType> nazw i nowy model programowania, który jest oparty na koncepcji zadań, a nie wątków. Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../parallel-programming/index.md) i [biblioteka równoległa zadań (TPL).](../parallel-programming/task-parallel-library-tpl.md)

## <a name="how-to-create-and-start-a-new-thread"></a>Jak: Tworzenie i rozpoczynanie nowego wątku

Utwórz nowy wątek, tworząc nowe <xref:System.Threading.Thread?displayProperty=nameWithType> wystąpienie klasy i podając nazwę metody, która ma zostać wykonana w nowym wątku do konstruktora. Aby rozpocząć utworzony wątek, <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> wywołaj metodę. Aby uzyskać więcej informacji i przykładów, zobacz [tworzenie wątków i przekazywanie danych w czasie rozpoczęcia](creating-threads-and-passing-data-at-start-time.md) artykuł i odwołanie <xref:System.Threading.Thread> interfejsu API.

## <a name="how-to-stop-a-thread"></a>Jak: Zatrzymać wątek

Aby zakończyć wykonywanie wątku, <xref:System.Threading.CancellationToken?displayProperty=nameWithType>należy użyć pliku . Zapewnia jednolity sposób, aby zatrzymać wątki wspólnie. Aby uzyskać więcej informacji, zobacz [Anulowanie w wątkach zarządzanych](cancellation-in-managed-threads.md).

Czasami nie jest możliwe, aby zatrzymać wątek kooperatywnie, ponieważ uruchamia kod innej firmy nie przeznaczony do anulowania współpracy. W takim przypadku można zakończyć jego wykonanie na siłę. Aby zakończyć wykonywanie wątku siłą, w .NET Framework <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> można użyć metody. Ta metoda <xref:System.Threading.ThreadAbortException> wywołuje w wątku, na którym jest wywoływana. Aby uzyskać więcej informacji, zobacz [Niszczenie wątków](destroying-threads.md). Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nie jest obsługiwana w .NET Core. Jeśli musisz zakończyć wykonywanie kodu innej firmy siłą w .NET Core, uruchom go <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>w oddzielnym procesie i użyj .

Nie <xref:System.Threading.CancellationToken?displayProperty=nameWithType> jest dostępna przed .NET Framework 4. Aby zatrzymać wątek w starszych wersjach .NET Framework, należy zaimplementować anulowanie współpracy ręcznie przy użyciu technik synchronizacji wątków. Na przykład można utworzyć pole `shouldStop` nietrwałego logicznego i użyć go do żądania kodu wykonanego przez wątek, aby zatrzymać. Aby uzyskać więcej [volatile](../../csharp/language-reference/keywords/volatile.md) informacji, zobacz <xref:System.Threading.Volatile?displayProperty=nameWithType>volatile w C# Odwołania i .

Użyj <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody, aby wątek wywołujący czekać na zakończenie wątku jest zatrzymany.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Jak: Wstrzymać lub przerwać wątek

Metoda służy <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> do wstrzymywania bieżącego wątku przez określony czas. Można przerwać zablokowany wątek, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wywołując metodę. Aby uzyskać więcej informacji, zobacz [Wstrzymywanie i przerywanie wątków](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Właściwości wątku

W poniższej tabeli <xref:System.Threading.Thread> przedstawiono niektóre właściwości:  
  
|Właściwość|Opis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Zwraca, `true` jeśli wątek został uruchomiony i nie został jeszcze zakończony normalnie lub przerwane.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Pobiera lub ustawia wartość logiczną, która wskazuje, czy wątek jest wątkiem w tle. Wątki w tle są jak wątki pierwszego planu, ale wątek w tle nie uniemożliwia zatrzymania procesu. Po zatrzymaniu wszystkich wątków pierwszego planu, które należą do procesu, czas <xref:System.Threading.Thread.Abort%2A> uruchomieniowy języka wspólnego kończy proces, wywołując metodę w wątkach w tle, które są nadal aktywne. Aby uzyskać więcej informacji, zobacz [Wątki pierwszego planu i tła](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Pobiera lub ustawia nazwę wątku. Najczęściej używane do odnajdowania poszczególnych wątków podczas debugowania.|  
|<xref:System.Threading.Thread.Priority%2A>|Pobiera lub <xref:System.Threading.ThreadPriority> ustawia wartość, która jest używana przez system operacyjny do ustalania priorytetów planowania wątków. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.ThreadPriority> [Planowanie wątków](scheduling-threads.md) i odwołania.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Pobiera <xref:System.Threading.ThreadState> wartość zawierającą bieżące stany wątku.|  

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Wątki i wątkowość](threads-and-threading.md)
- [Programowanie równoległe](../parallel-programming/index.md)
