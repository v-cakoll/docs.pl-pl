---
title: 'Porady: zapisywanie prostej równoległej pętli For'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29da081784c06d8cd467f0566f9d4db92a130b53
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087277"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Porady: zapisywanie prostej równoległej pętli For
Ten temat zawiera dwa przykłady ilustrujące <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Używa pierwszego <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> przeciążenia metody, a drugie <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> przeciążenia, dwa przeciążenia najprostszym <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Możesz użyć tych dwa przeciążenia metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody, gdy jest konieczne anulowanie pętli, zerwać iteracji pętli lub zarządzania stanem żadnych wątków lokalnych.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Pierwszy przykład oblicza rozmiar plików w jednym katalogu. Druga instrukcja Oblicza iloczyn dwóch macierzy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest prostego narzędzia wiersza polecenia, który oblicza całkowity rozmiar plików w katalogu. Oczekuje, że ścieżka pojedynczego katalogu jako argument i zgłasza liczbę i całkowity rozmiar plików w tym katalogu. Po sprawdzeniu, czy katalog istnieje, używa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodę, aby wyliczyć pliki w katalogu i określić ich rozmiarów plików. Rozmiar każdego pliku jest następnie dodawana do `totalSize` zmiennej. Należy pamiętać, że dodanie odbywa się przez wywołanie metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> tak, aby dodanie odbywa się jako operację niepodzielną. W przeciwnym razie wiele zadań można spróbować zaktualizować `totalSize` zmiennej jednocześnie.  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodę w celu obliczenia iloczyn dwóch macierzy. Prezentuje sposób użycia <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> klasy, aby porównać wydajność pętli równoległej z pętlą nierównoległy. Należy pamiętać, że, ponieważ może generować dużą ilość danych wyjściowych, przykład zezwala na dane wyjściowe do pliku.  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 Przekształcają dowolnego kodu, łącznie z pętli, jeden cel ważne jest wykorzystanie procesorów, jak to możliwe, bez za pośrednictwem przekształcają do punktu, w którym obciążenie do przetwarzania równoległego neguje żadnych korzyści wydajności. W tym konkretnym przykładzie tylko zewnętrzna pętla jest zrównoleglona, ponieważ nie jest bardzo wykonywanych wewnętrzną pętlę. Kombinacja niewielką ilość pracy i pamięci podręcznej niepożądanych skutków może spowodować obniżenie wydajności w pętlach równoległych zagnieżdżonych. W związku z tym przekształcają zewnętrzna pętla tylko jest najlepszy sposób, aby zmaksymalizować korzyści współbieżności w większości systemów.  
  
## <a name="the-delegate"></a>Delegat  
 Trzeci parametr to przeciążenie <xref:System.Threading.Tasks.Parallel.For%2A> jest delegat typu `Action<int>` w języku C# lub `Action(Of Integer)` w języku Visual Basic. `Action` Delegata, czy zawiera on zero, co najmniej parametrami typu szesnastu, zawsze zwraca wartość void. W języku Visual Basic, zachowanie `Action` jest zdefiniowana za pomocą `Sub`. W przykładzie użyto wyrażenia lambda do utworzenia delegata, ale w inny sposób, jak również można utworzyć obiektu delegowanego. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="the-iteration-value"></a>Wartość iteracji  
 Delegat przyjmuje jeden parametr danych wejściowych, którego wartością jest bieżąca iteracja. Ta wartość iteracji jest dostarczany przez środowisko uruchomieniowe i jej wartość początkową to indeks pierwszego elementu w segmencie (partycja) źródła, który jest przetwarzany w bieżącym wątku.  
  
 Jeśli potrzebujesz większej kontroli nad poziom współbieżności, użyj jednego z przeciążeń, które przyjmuje <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> parametr wejściowy, takich jak: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.  
  
## <a name="return-value-and-exception-handling"></a>Wartość zwracana w obsłudze wyjątków  
 <xref:System.Threading.Tasks.Parallel.For%2A> Zwraca <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> obiektu po zakończeniu wszystkich wątków. To zwraca wartość jest przydatne, gdy zatrzymujesz lub podziału iteracji pętli ręcznie, ponieważ <xref:System.Threading.Tasks.ParallelLoopResult> przechowuje informacje takie jak ostatniej iteracji, które zakończyło się. Jeśli jeden lub kilka wyjątków występują na jednym z wątków, <xref:System.AggregateException?displayProperty=nameWithType> zostanie zgłoszony.  
  
 W kodzie, w tym przykładzie wartość zwracaną przez <xref:System.Threading.Tasks.Parallel.For%2A> nie jest używany.  
  
## <a name="analysis-and-performance"></a>Analiza i wydajności  
 Kreator wydajności można użyć, aby wyświetlić dane użycia procesora CPU na komputerze. Jako eksperyment należy zwiększyć liczbę wierszy i kolumn w macierzach. Im większy macierzy, większa różnica w wydajności wersjach równoległych i sekwencyjnych obliczeń. W przypadku macierzy jest mała, kolejna wersja działa szybciej ze względu na obciążenie związane z konfigurowaniem pętli równoległej.  
  
 Synchroniczne wywołania do udostępnionych zasobów, takich jak konsoli lub systemu plików zostanie znacząco obniżą wydajność pętli równoległej. Gdy mierzenia wydajności, należy unikać wywołania, takie jak <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> w ramach pętli.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Skopiuj i wklej ten kod do projektu programu Visual Studio 2010.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Parallel.For%2A>  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
