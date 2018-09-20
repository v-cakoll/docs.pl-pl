---
title: Ogólne informacje o przyspieszeniach w PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc36c926ba81de8a59ff3af69719bec6b7370efc
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326322"
---
# <a name="understanding-speedup-in-plinq"></a>Ogólne informacje o przyspieszeniach w PLINQ
Głównym celem PLINQ jest przyspieszenie wykonywania zapytań LINQ do zapytań obiekt, wykonując delegatów zapytania równolegle na komputerach z wielordzeniowymi procesorami. Program PLINQ sprawdza się najlepiej, gdy przetwarzania każdego elementu w kolekcji źródłowej jest niezależne, bez udostępnionego stanu związane między poszczególnych obiektów delegowanych. Operacje takie są wspólne w składniku LINQ do obiektów i PLINQ i są często nazywane "*delightfully równoległe*" ponieważ one nadają się łatwo do planowania w wielu wątkach. Jednak nie wszystkie kwerendy składać się z samych operacji delightfully równoległych; w większości przypadków zapytanie obejmuje niektóre operatory, albo nie może być przeprowadzana równolegle lub który spowolnić wykonywanie równoległe. A nawet w przypadku zapytań, które są całkowicie delightfully równoległego, PLINQ musi nadal partycji źródła danych harmonogramu pracy nad wątków i zazwyczaj scalać wyniki po wykonaniu kwerendy. Wszystkie te operacje dodawania obliczeniową koszty przetwarzania równoległego; te koszty, dodawanie funkcji przetwarzania równoległego, są nazywane *obciążenie*. Aby uzyskać optymalną wydajność w zapytaniu PLINQ, celem jest maksymalne części, które są delightfully równoległe i zminimalizować części, które wymagają narzutu. Ten artykuł zawiera informacje, dzięki którym można tworzyć zapytania PLINQ, które są najbardziej efektywne podczas nadal reaguje poprawne wyniki.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Czynniki wpływające na wydajność zapytań PLINQ  
 W poniższych sekcjach wymieniono niektóre z najważniejszych czynników tego obniżenie wydajności zapytania równolegle. Są to ogólne instrukcje, które same w sobie nie są wystarczające, aby przewidzieć wydajności zapytań we wszystkich przypadkach. Jak zawsze jest ważne, aby zmierzyć wydajność rzeczywistego określonych zapytań na komputerach z szerokim zakresem reprezentatywny konfiguracje i obciążeniami.  
  
1.  Obliczeniową koszty ogólne pracy.  
  
     Aby osiągnąć przyspieszenie, zapytanie PLINQ musi mieć wystarczającą ilość delightfully równoległą pracę, aby zrównoważyć obciążenie. Praca może być wyrażona jako obliczeniową koszt każdego delegata pomnożona przez liczbę elementów w kolekcji źródłowej. Przy założeniu, że operacji może odbywać się równolegle, tym bardziej praktyce kosztowne jest, tym większa możliwość przyspieszenie. Na przykład jeśli funkcja przyjmuje jeden milisekund do wykonania, sekwencyjne zapytanie ponad 1000 elementów zajmie 1 sekundy do wykonania tej operacji, natomiast równoległego zapytań na komputerze z cztery rdzenie może zająć tylko 250 milisekund. Daje to przyspieszenie 750 milisekund. W razie potrzeby jednej sekundy można wykonać dla każdego elementu funkcji przyspieszenie byłoby 750 sekund. Jeśli delegat jest bardzo kosztowna, PLINQ może oferować znaczące przyspieszenie za pomocą tylko kilku elementów w kolekcji źródłowej. Z drugiej strony kolekcje małych źródła z uproszczonych delegatów zazwyczaj nie są dobrymi kandydatami do PLINQ.  
  
     W poniższym przykładzie queryA prawdopodobnie jest dobrym kandydatem do PLINQ, zakładając, że jego funkcja wybierz polega na sporego nakładu pracy. queryB prawdopodobnie nie jest dobrym kandydatem, ponieważ nie jest wystarczająco dużo pracy w instrukcji Select, a obciążenie związane z przetwarzaniem równoległym spowoduje przesunięcie większości lub wszystkich przyspieszenie.  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
    ```  
  
2.  Liczba rdzeni logicznych w systemie (stopień równoległości).  
  
     Ten punkt jest oczywisty następstwem w poprzedniej sekcji, zapytania, które są delightfully równoległe działają szybciej na komputerach przy użyciu więcej rdzeni, ponieważ można podzielić pracę między większą liczbę jednoczesnych wątków. Ogólną ilość przyspieszenie zależy od tego, jaki procent ogólnej pracy kwerendy jest równoległego. Jednak nie należy zakładać, że wszystkie zapytania będą uruchamiane dwa razy szybkiego na komputerze osiem podstawowe jako komputer cztery podstawowe. Podczas dostosowywania zapytań, aby uzyskać optymalną wydajność, należy do mierzenia rzeczywiste wyniki na komputerach mających różne liczby rdzeni. Ten punkt jest powiązany z punktu #1: większych zestawów danych są wymagane, aby móc korzystać z większej zasobów obliczeniowych.  
  
3.  Liczba i rodzaj operacji.  
  
     Program PLINQ zawiera AsOrdered operator w sytuacjach, w których jest to konieczne zachować kolejność elementów w sekwencji źródłowej. Istnieje koszt związany z kolejności, ale ten koszt jest zwykle niewielkie. Operacje GroupBy i sprzężenia podobnie naliczone obciążenie. Program PLINQ sprawdza się najlepiej, gdy jest możliwy do przetwarzania elementów w kolekcji źródłowej, w dowolnej kolejności i przekazywać je dalej operatora, jak są one gotowe. Aby uzyskać więcej informacji, zobacz [zamawianie zachowywania w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4.  Formularz wykonywania zapytania.  
  
     Jeśli wyniki zapytania są przechowywane przez wywołanie metody ToArray lub tolist —, wyniki ze wszystkich wątków równoległych, muszą zostać połączone w strukturze danych jednego. Obejmuje to da się uniknąć kosztów obliczeniową. Podobnie jeśli wyniki iteracji za pomocą pętli foreach (dla każdego w języku Visual Basic), wyniki z wątków roboczych muszą być serializowany na wątek modułu wyliczającego. Ale jeśli chcesz wykonywać niektórych akcji, na podstawie wyniku z każdego wątku, można użyć metody ForAll do wykonywania tej pracy w wielu wątkach.  
  
5.  Typ opcji scalania.  
  
     Program PLINQ można skonfigurować do buforowania danych wyjściowych i przedstawić go we fragmentach, lub wszystkie na raz po cały zestaw wyników jest generowany, lub do poszczególnych wyników strumienia jako są produkowane. Wynik poprzedniego jest obniżenie całkowity czas wykonywania i ostatnie wyniki zmniejszenia opóźnienia między elementami yielded.  Chociaż opcje scalania nie zawsze mają istotny wpływ na ogólną wydajność zapytań, mogą one wpływać na wydajność ponieważ kontrolują jak długo użytkownik musi czekać, aby zobaczyć wyniki. Aby uzyskać więcej informacji, zobacz [opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6.  Rodzaj partycji.  
  
     W niektórych przypadkach zapytanie PLINQ przez kolekcję można indeksować źródła może spowodować obciążenia pracą niezrównoważone. W takiej sytuacji można zwiększyć wydajność zapytań, tworząc niestandardowy partycjoner. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Gdy wybierze trybu sekwencyjnego w PLINQ  
 Program PLINQ zawsze będzie podejmował próbę wykonania kwerendy co najmniej tak szybko, jak uruchomić zapytanie sekwencyjnie. Mimo, że PLINQ nie wygląda jak praktyce są kosztowne delegatów użytkownika lub jak duże źródło danych wejściowych jest, poszukaj niektórych zapytań "kształty". W szczególności szuka operatorów zapytań lub kombinacji operatorów, które zazwyczaj powodują zapytanie w celu wykonania wolniej w trybie równoległych. Po znalezieniu takiego kształty, PLINQ domyślnie powraca do trybu sekwencyjnego.  
  
 Jednak po mierzenia wydajności określonej kwerendy, można stwierdzić czy on rzeczywiście działa szybciej w trybie równoległych. W takich przypadkach można użyć <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> Flaga za pośrednictwem <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metodę, aby nakazać PLINQ do zrównoleglenia zapytania. Aby uzyskać więcej informacji, zobacz [porady: Określanie trybu wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Na poniższej liście opisano kształty zapytanie PLINQ domyślnie będą wykonywane w trybie sekwencyjnego:  
  
-   Zapytania, które zawierają Select, Where, indeksowane indeksowanych SelectMany lub klauzuli ElementAt po operatorze sortowania lub filtrowania, który został usunięty lub przestawiać, oryginalnym indeksów.  
  
-   Zapytania zawierające Pomiń Take, takewhile —, skipwhile — operator i której indeksów w sekwencji źródłowej nie są w kolejności, oryginalnym.  
  
-   Zapytania, które zawierają Zip lub SequenceEquals, chyba że jest to jedno ze źródeł danych i inne źródła danych jest można indeksować zamówiony indeksu (czyli tablicy lub IList(T)).  
  
-   Zapytania, które zawierają Concat, chyba że zostanie zastosowany do źródeł danych można indeksować.  
  
-   Zapytania, które zawierają odwrócić, chyba że stosowane do źródła danych można indeksować.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
