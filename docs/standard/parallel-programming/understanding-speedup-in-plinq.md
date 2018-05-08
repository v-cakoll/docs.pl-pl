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
ms.openlocfilehash: 2c2e7d5ce170feecaf69aa5dd9785346de0375d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="understanding-speedup-in-plinq"></a>Ogólne informacje o przyspieszeniach w PLINQ
Głównym celem PLINQ ma przyspieszyć wykonywanie LINQ do obiektów zapytań, wykonując delegatów zapytania równolegle na komputerach z procesorami wielordzeniowymi. PLINQ sprawdza się najlepiej, gdy przetwarzania każdego elementu w kolekcji źródłowej jest niezależny, bez udostępnionych stanu związane między poszczególnych obiektów delegowanych. Takie operacje są często używane w LINQ do obiektów i PLINQ i są często nazywane "*delightfully równoległe*" ponieważ możliwa jest łatwo planowania na wiele wątków. Jednak nie wszystkie zapytania składa się wyłącznie z operacji równoległych delightfully; w większości przypadków zapytania obejmuje niektóre operatory, które albo nie może być zarządzana z przetwarzaniem lub który spowolnić przetwarzania równoległego. I nawet w przypadku zapytań, które są całkowicie delightfully równoległe, PLINQ i musi być nadal partycji źródła danych i harmonogramu pracy nad wątki, zwykle scalania wyniki po wykonaniu kwerendy. Dodaj te operacje obliczeniową koszty równoległości; Dodawanie paralelizacja koszty są nazywane *koszty*. Aby osiągnąć optymalną wydajność w zapytaniu PLINQ, celem jest zmaksymalizować części, które są delightfully równoległe i zminimalizować części, które wymagają obciążenia. Ten artykuł zawiera informacje, dzięki którym można pisać zapytania PLINQ, które są najbardziej efektywne podczas nadal reaguje poprawnych wyników.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Czynniki wpływające na wydajność zapytań PLINQ  
 Poniższe sekcje wymieniono najważniejsze czynniki tego wydajność zapytań równoległych wpływ. Są to ogólne instrukcje, które same nie są wystarczające do prognozowania wydajność zapytań we wszystkich przypadkach. Jak zawsze należy do mierzenia Rzeczywista wydajność kwerend określonych na komputerach z zakresem reprezentatywny konfiguracji i obciążeń.  
  
1.  Obliczeniowa koszt ogólną pracy.  
  
     Umożliwia przyspieszenie zapytań PLINQ musi mieć wystarczająco dużo pracy delightfully równoległych do przesunięcia obciążenie. Pracy może zostać wyrażona jako obliczeniową koszt każdej delegata pomnożona przez liczbę elementów w kolekcji źródłowej. Przy założeniu, że operacja może być zarządzana z przetwarzaniem, im bardziej praktyce kosztowne jest, tym większa możliwości przyspieszenie. Na przykład jeśli funkcja przyjmuje jeden milisekund do wykonania, kolejne zapytanie ponad 1000 elementów potrwa jednej sekundy do wykonania tej operacji, natomiast równoległego zapytania na komputerze z czterech rdzeni może potrwać tylko 250 milisekund. Daje to przyspieszenie 750 milisekund. W razie potrzeby jednej sekundy można wykonać dla każdego elementu funkcji przyspieszenie byłoby 750 sekund. Jeśli delegat jest bardzo kosztowna, PLINQ może oferować znaczące przyspieszenie tylko kilka elementów w kolekcji źródłowej. Z drugiej strony kolekcje małych źródła z trivial delegatów zazwyczaj nie są odpowiednimi obiektami do PLINQ.  
  
     W poniższym przykładzie queryA prawdopodobnie są odpowiednimi kandydatami do PLINQ, przy założeniu, że wybierz funkcji obejmuje wiele pracy. queryB prawdopodobnie nie jest dobrym wyborem, ponieważ nie jest wystarczająco dużo pracy w instrukcji Select, a obciążenie równoległości zostanie przesunięty większość lub wszystkie przyspieszenie.  
  
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
  
     Ten punkt jest następstwem widocznych w poprzedniej sekcji, zapytania, które są delightfully równoległe szybsze na maszynach z większej liczby rdzeni ponieważ pracy można podzielić między większą liczbę jednoczesnych wątków. Ogólną ilość przyspieszenie zależy od tego, jaki procent ogólnej pracy zapytania jest działania równoległego. Jednak nie należy zakładać, że wszystkie zapytania zostanie uruchomiony dwukrotnie jako szybkiego na komputerze osiem rdzeni jako komputer cztery podstawowe. Dostrajanie zapytania, aby zapewnić optymalną wydajność, koniecznie mierzyć rzeczywiste wyniki na komputerach z różnych liczby rdzeni. Ten punkt jest powiązany z punktu #1: większych zestawów danych są wymagane, aby móc korzystać z większej zasobów obliczeniowych.  
  
3.  Liczba i rodzaj operacji.  
  
     PLINQ zawiera operator operator AsOrdered w sytuacjach, w których jest wymagane do zachowania kolejności elementów w sekwencji źródłowej. Jest koszt związany z kolejności, ale jest to zazwyczaj niewielkie. Operacje GroupBy i sprzężenia podobnie nakładu. PLINQ sprawdza się najlepiej, gdy jest możliwy do przetwarzania elementów w kolekcji źródłowej w dowolnej kolejności i przekazują je do następnego operatora, jak będą gotowe. Aby uzyskać więcej informacji, zobacz [zamawianie zachowywania w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4.  Formularz wykonywania zapytania.  
  
     Jeśli wyniki zapytania są przechowywane przez wywołanie metody ToArray lub tolist —, wyniki ze wszystkich równoległych wątków muszą zostać połączone w strukturze danych jednego. Obejmuje to nieuniknione koszt obliczeniową. Podobnie jeśli wyniki są Iterowanie za pomocą pętli foreach (dla każdej z nich w Visual Basic), wyniki z wątków roboczych konieczne można serializować na wątku modułu wyliczającego. Jednak po prostu chcesz wykonanie akcji na podstawie wyniku z każdy wątek, należy użyć metody ForAll — do wykonywania tej pracy w wielu wątkach.  
  
5.  Typ opcji scalania.  
  
     PLINQ można skonfigurować do albo buforować dane wyjściowe i tworzenia go w fragmentów lub jednorazowo po cały zestaw wyników jest generowany, w przeciwnym razie wyniki poszczególnych strumienia, ponieważ są one tworzone. Poprzedni wynik jest zmniejszyć całkowity czas wykonywania i drugie wyniki zmniejszyć opóźnienia między elementami zwróciło.  Gdy opcji scalania nie zawsze mają istotny wpływ na ogólną wydajność zapytań, ich może wpłynąć na wydajność, ponieważ decydować, jak długo użytkownik musi czekać, aby wyświetlić wyniki. Aby uzyskać więcej informacji, zobacz [opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6.  Rodzaj partycji.  
  
     W niektórych przypadkach PLINQ zapytanie dotyczące kolekcji można indeksować źródło może skutkować obciążenia pracą równowagi. W takim przypadku można zwiększyć wydajność zapytań, tworząc niestandardowe partycjonera. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Gdy PLINQ wybierze tryb sekwencyjne  
 PLINQ zawsze będzie podejmować próby wykonania kwerendy co najmniej tak szybko, jak zapytanie będzie wykonywane sekwencyjnie. Mimo że PLINQ nie wygląda jak praktyce są kosztowne delegatów użytkownika lub jak źródło danych wejściowych jest duży, wyszukaj niektórych zapytania "kształtów." W szczególności szuka operatorów zapytań lub kombinacje operatorów, które zazwyczaj powodują zapytanie w celu wykonania wolniej w trybie równoległym. Po znalezieniu takiego kształtów, PLINQ domyślnie powraca do trybu sekwencyjnych.  
  
 Jednak po pomiaru wydajności określonej kwerendy, należy może określić, że faktycznie działa szybciej w trybie równoległym. W takich przypadkach można użyć <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> Flaga za pośrednictwem <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody nakazać programowi PLINQ do parallelize zapytania. Aby uzyskać więcej informacji, zobacz [porady: Określanie trybu wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Poniższa lista zawiera opis kształty zapytania PLINQ domyślnie będą wykonywane w trybie sekwencyjnych:  
  
-   Zapytania, które zawierają Select, Where, indeksowane indeksowanego operacja SelectMany, lub klauzuli ElementAt po operatorze sortowania i filtrowania, usunąć lub ponownie rozmieszczać oryginalnego indeksów.  
  
-   Zapytań zawierających Pomiń podjęcia, TakeWhile, SkipWhile — operator, i gdy indeksy w sekwencji źródłowej nie są w kolejności.  
  
-   Zapytania zawierające Zip lub SequenceEquals, chyba że ma jedno ze źródeł danych pierwotnie uporządkowanej indeks i źródło danych jest można indeksować (tj. tablica lub IList(T)).  
  
-   Zapytania, które zawierają Concat, chyba że jest ono stosowane do źródeł danych można indeksować.  
  
-   Zapytania, które zawierają odwrócić, o ile nie dotyczy źródła danych można indeksować.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
