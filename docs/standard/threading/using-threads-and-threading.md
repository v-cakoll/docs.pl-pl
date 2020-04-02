---
title: Używanie wątków i wątkowości
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 14159ff9a6ca39108aec14b0ad46004e95fa3cf2
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588432"
---
# <a name="using-threads-and-threading"></a>Używanie wątków i wątkowości

Za pomocą platformy .NET można pisać aplikacje, które wykonują wiele operacji w tym samym czasie. Operacje z potencjałem wstrzymywania innych operacji można wykonać na oddzielnych wątkach, proces znany jako *wielowątkowe* lub *wolne wątki*.  
  
Aplikacje korzystające z wielowątkowych funkcji są bardziej responsywne na dane wejściowe użytkownika, ponieważ interfejs użytkownika pozostaje aktywny, ponieważ zadania wymagające dużej ilości procesora są wykonywane w oddzielnych wątkach. Wielowątkowość jest również przydatna podczas tworzenia aplikacji skalowalnych, ponieważ można dodawać wątki w miarę zwiększania obciążenia.

> [!NOTE]
> Jeśli potrzebujesz większej kontroli nad zachowaniem wątków aplikacji, możesz samodzielnie zarządzać wątkami. Jednak począwszy od .NET Framework 4, programowanie <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> wielowątkowe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest znacznie uproszczone z klasami [i, Parallel LINQ (PLINQ),](../parallel-programming/introduction-to-plinq.md)nowymi klasami równoczesnych kolekcji w obszarze <xref:System.Collections.Concurrent?displayProperty=nameWithType> nazw i nowym modelem programowania, który jest oparty na koncepcji zadań, a nie wątków. Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../parallel-programming/index.md) i [biblioteka równoległa zadań (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Jak: Tworzenie i uruchamianie nowego wątku

Utworzyć nowy wątek, tworząc nowe <xref:System.Threading.Thread?displayProperty=nameWithType> wystąpienie klasy i podając nazwę metody, którą chcesz wykonać w nowym wątku do konstruktora. Aby rozpocząć utworzony wątek, należy wywołać <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metodę. Aby uzyskać więcej informacji i przykładów, zobacz [Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia](creating-threads-and-passing-data-at-start-time.md) artykułu i odwołania <xref:System.Threading.Thread> interfejsu API.

## <a name="how-to-stop-a-thread"></a>Jak: Zatrzymaj wątek

Aby zakończyć wykonywanie wątku, <xref:System.Threading.CancellationToken?displayProperty=nameWithType>należy użyć pliku . Zapewnia ujednolicony sposób, aby zatrzymać wątki wspólnie. Aby uzyskać więcej informacji, zobacz [Anulowanie w wątkach zarządzanych](cancellation-in-managed-threads.md).

Czasami nie jest możliwe, aby zatrzymać wątku wspólnie, ponieważ uruchamia kod innej firmy nie przeznaczony do anulowania współpracy. W takim przypadku można zakończyć jego wykonanie przymusowo. Aby zakończyć wykonywanie wątku na przymusowo, w .NET <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Framework można użyć metody. Ta metoda podnosi <xref:System.Threading.ThreadAbortException> na wątku, na którym jest wywoływana. Aby uzyskać więcej informacji, zobacz [Niszczenie wątków](destroying-threads.md). Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nie jest obsługiwana w .NET Core. Jeśli chcesz zakończyć wykonywanie kodu innej firmy na przymusowo w .NET Core, uruchom <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>go w oddzielnym procesie i użyj .

Nie <xref:System.Threading.CancellationToken?displayProperty=nameWithType> jest dostępna przed .NET Framework 4. Aby zatrzymać wątek w starszych wersjach programu .NET Framework, należy zaimplementować anulowanie współpracy ręcznie przy użyciu technik synchronizacji wątków. Na przykład można utworzyć pole `shouldStop` logiczne lotne i użyć go do żądania kodu wykonywanego przez wątek, aby zatrzymać. Aby uzyskać więcej [volatile](../../csharp/language-reference/keywords/volatile.md) informacji, zobacz <xref:System.Threading.Volatile?displayProperty=nameWithType>volatile w języku C# Reference i .

Użyj <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody, aby wątek wywołujący czekać na zakończenie wątku jest zatrzymany.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Jak: Wstrzymanie lub przerwanie wątku

Metoda służy <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> do wstrzymania bieżącego wątku przez określony czas. Zablokowany wątek można przerwać, wywołując <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodę. Aby uzyskać więcej informacji, zobacz [Wstrzymywanie i przerywanie wątków](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Właściwości gwintu

W poniższej tabeli <xref:System.Threading.Thread> przedstawiono niektóre właściwości:  
  
|Właściwość|Opis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Zwraca, `true` jeśli wątek został uruchomiony i nie został jeszcze zakończony normalnie lub przerwany.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Pobiera lub ustawia wartość logiczną, która wskazuje, jeśli wątek jest wątku tła. Wątki tła są jak wątki pierwszego planu, ale wątek tła nie uniemożliwia zatrzymywania procesu. Po zatrzymaniu wszystkich wątków pierwszego planu, które należą do procesu, środowisko <xref:System.Threading.Thread.Abort%2A> uruchomieniowe języka wspólnego kończy proces, wywołując metodę w wątkach w tle, które są nadal żywe. Aby uzyskać więcej informacji, zobacz [Wątki pierwszego planu i wątki w tle](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Pobiera lub ustawia nazwę wątku. Najczęściej używane do odnajdowania poszczególnych wątków podczas debugowania.|  
|<xref:System.Threading.Thread.Priority%2A>|Pobiera lub <xref:System.Threading.ThreadPriority> ustawia wartość, która jest używana przez system operacyjny do ustalania priorytetów planowania wątków. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.ThreadPriority> [Planowanie wątków](scheduling-threads.md) i odwołanie.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Pobiera <xref:System.Threading.ThreadState> wartość zawierającą bieżące stany wątku.|  

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Wątki i wątkowość](threads-and-threading.md)
- [Programowanie równoległe](../parallel-programming/index.md)
