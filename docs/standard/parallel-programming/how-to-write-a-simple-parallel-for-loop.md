---
title: "Porady: zapisywanie prostej równoległej pętli For"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3a70dcb5e3811a18e23aeb2ebf0940d2c52f49a9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Porady: zapisywanie prostej równoległej pętli For
Ten temat zawiera dwa przykłady ilustrujące <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Używa pierwszego <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> przeciążenie metody, a drugi używa <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> przeciążenia, dwa przeciążeń najprostszym <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Korzystając z tych dwóch przeciążeń <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody, gdy jest konieczne anulowanie pętli, Podziel poza iteracji pętli lub obsługa każdy stan lokalnej wątku.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Pierwszym przykładzie oblicza rozmiar plików z jednego katalogu. Drugi Oblicza iloczyn dwóch macierzy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest prostego narzędzia wiersza polecenia, który oblicza całkowity rozmiar plików w katalogu. Oczekuje ścieżki jednego katalogu jako argument, a raporty liczby i łączny rozmiar plików w tym katalogu. Po zweryfikowaniu, że katalog istnieje, używa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodę Wyliczanie plików w katalogu oraz ustalić ich rozmiary plików. Rozmiar każdego pliku jest dodawane do `totalSize` zmiennej. Należy pamiętać, że dodanie są wykonywane przez wywołanie metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> tak, aby jako operacją niepodzielną wykonywane jest dodawanie. W przeciwnym razie wiele zadań można spróbuj zaktualizować `totalSize` zmiennej jednocześnie.  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodę w celu obliczenia produktu macierzy dwa. Przedstawiono również sposób użycia <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> klasy do porównania wydajności równoległej pętli z pętli nie są równoległe. Należy zauważyć, że, ponieważ może generować duże ilości danych wyjściowych, przykładzie pozwala dane wyjściowe do pliku.  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 Podczas parallelizing dowolnego kodu, w tym pętle, co ważne celem jest wykorzystywać jak to możliwe, bez procesorów za pośrednictwem parallelizing do punktu, w którym obciążenie przetwarzania równoległego Negacja wszelkie zwiększenia wydajności. W tym przykładzie ponieważ nie jest bardzo dużą ilość pracy wykonanej w pętli wewnętrznej jest zarządzana przetwarzaniem zewnętrzne pętli. Kombinacja niewielką ilość pracy i pamięci podręcznej niepożądanych skutków może spowodować spadek wydajności w pętlach równoległych zagnieżdżonych. W związku z tym parallelizing zewnętrzne pętli jest tylko najlepszy sposób, aby zmaksymalizować korzyści współbieżności na większości systemów.  
  
## <a name="the-delegate"></a>Obiekt delegowany  
 Trzeci parametr to przeciążenie metody <xref:System.Threading.Tasks.Parallel.For%2A> jest delegowanego typu `Action<int>` w języku C# lub `Action(Of Integer)` w języku Visual Basic. `Action` Delegata, czy ma ona wartość zero, co najmniej parametrów typu szesnastu zawsze zwraca typ void. W języku Visual Basic, zachowanie `Action` jest zdefiniowana z `Sub`. W przykładzie użyto wyrażenia lambda, można utworzyć obiektu delegowanego, ale także inne sposoby można utworzyć obiektu delegowanego. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="the-iteration-value"></a>Wartość iteracji  
 Delegat przyjmuje jeden parametr wejściowy, którego wartość jest bieżącą iterację. Ta wartość iteracji jest dostarczany przez środowisko uruchomieniowe i jego wartość początkowa to indeks pierwszego elementu w segmencie (partycja) źródła, które jest przetwarzana w bieżącym wątku.  
  
 Jeśli wymagana większa kontrola nad poziomem współbieżności, użyj jednej z przeciążeń, które przyjmuje <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> parametr wejściowy, takich jak: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.  
  
## <a name="return-value-and-exception-handling"></a>Wartość zwracana i obsługa wyjątków  
 <xref:System.Threading.Tasks.Parallel.For%2A>Zwraca <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> obiekt po zakończeniu wszystkich wątków. To zwrócenie wartości jest przydatne, gdy są zatrzymanie lub podziału iteracji pętli ręcznie, ponieważ <xref:System.Threading.Tasks.ParallelLoopResult> przechowuje informacje, takie jak ostatnich iteracji uruchamianej do zakończenia. Jeśli co najmniej jeden wyjątek występuje w jednym z wątków, <xref:System.AggregateException?displayProperty=nameWithType> zostanie wygenerowany.  
  
 W kodzie w tym przykładzie wartość zwracaną <xref:System.Threading.Tasks.Parallel.For%2A> nie jest używany.  
  
## <a name="analysis-and-performance"></a>Analiza i wydajności  
 Kreator wydajności Wyświetl użycie procesora CPU na komputerze. Jako eksperymentu należy zwiększyć liczbę wierszy i kolumn w macierzy. Im większa macierzy, wyższy różnicy wydajności między wersjami równoległych i sekwencyjnych obliczenia. W przypadku małych macierzy kolejnych wersji będzie szybsze ze względu na obciążenie związane z konfigurowaniem równoległej pętli.  
  
 Synchroniczne wywołania do udostępnionych zasobów, takich jak konsoli lub System plików będzie znacząco pogorszyć wydajność równoległej pętli. Gdy pomiaru wydajności, należy unikać takich jak wywołania <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> w pętli.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Skopiuj i wklej ten kod do projektu programu Visual Studio 2010.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Parallel.For%2A>  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
