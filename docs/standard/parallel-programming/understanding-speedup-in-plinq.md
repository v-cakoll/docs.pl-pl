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
ms.openlocfilehash: 07b5027d560a4caccc6c0a516c3f70c11df6be83
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139907"
---
# <a name="understanding-speedup-in-plinq"></a>Ogólne informacje o przyspieszeniach w PLINQ
Głównym celem PLINQ jest przyspieszenie wykonywania zapytań LINQ to Objects przez wykonywanie delegatów zapytań równolegle na komputerach wielordzeniowych. PLINQ sprawdza się najlepiej, gdy przetwarzanie każdego elementu w kolekcji źródłowej jest niezależne, bez współużytkowanego stanu wśród poszczególnych delegatów. Takie operacje są typowe w LINQ to Objects i PLINQ i często nazywa się "*delightfully Parallel*", ponieważ ułatwiają one planowanie na wielu wątkach. Jednak nie wszystkie zapytania składają się wyłącznie z delightfully operacji równoległych; w większości przypadków zapytanie obejmuje niektóre operatory, które nie mogą być równoległe lub spowalniają wykonywanie równoległe. Mimo że zapytania, które są całkowicie delightfully równolegle, PLINQ muszą nadal dzielić źródło danych i zaplanować pracę w wątkach, a zazwyczaj scalać wyniki po zakończeniu zapytania. Wszystkie te operacje są dodawane do kosztów obliczeniowych przetwarzanie równoległe; koszty dodawania przetwarzanie równoległe są nazywane *obciążeniem*. Aby osiągnąć optymalną wydajność zapytania PLINQ, celem jest maksymalizacja części, które są delightfully równoległe i zminimalizowanie części, które wymagają narzutu. Ten artykuł zawiera informacje, które pomogą w pisaniu PLINQ zapytań, które są tak wydajne, jak to możliwe, przy zachowaniu prawidłowych wyników.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Czynniki wpływające na wydajność zapytań PLINQ  
 W poniższych sekcjach wymieniono najważniejsze czynniki wpływające na wydajność zapytań równoległych. Są to ogólne instrukcje, które same nie są wystarczające do przewidywania wydajności zapytań we wszystkich przypadkach. Tak samo ważne jest, aby mierzyć rzeczywistą wydajność konkretnych zapytań na komputerach z różnymi konfiguracjami i obciążeniami reprezentatywnymi.  
  
1. Koszt obliczeniowy całościowej pracy.  
  
     Aby osiągnąć przyspieszenie, zapytanie PLINQ musi mieć wystarczającą liczbę delightfully równoległej pracy, aby przesunąć obciążenie. Nakład pracy może być wyrażony jako koszt obliczeniowy każdego delegata pomnożony przez liczbę elementów w kolekcji źródłowej. Przy założeniu, że operacja może być równoległa, im bardziej kosztowne jest, tym większa szansa dla przyspieszenie. Jeśli na przykład funkcja przyjmuje jedną milisekundę, wykonanie tej operacji przez sekwencyjne zapytanie ponad 1000 elementów zajmie jedną sekundę, podczas gdy zapytanie równoległe na komputerze z czterema rdzeniami może trwać tylko 250 milisekund. Daje to przyspieszenie o 750 milisekund. Jeśli funkcja wymagana przez jedną sekundę do wykonania dla każdego elementu, przyspieszenie będzie 750 sekund. Jeśli delegat jest bardzo kosztowny, PLINQ może oferować znaczący przyspieszenie z tylko kilkoma elementami w kolekcji źródłowej. Z kolei małe kolekcje źródłowe z prostymi delegatami zwykle nie są dobrymi kandydatami do PLINQ.  
  
     W poniższym przykładzie zapytanie jest prawdopodobnie dobrym kandydatem do PLINQ, przy założeniu, że jego funkcja SELECT obejmuje wiele pracy. queryB prawdopodobnie nie jest dobrym kandydatem, ponieważ nie ma wystarczającej ilości pracy w instrukcji SELECT, a obciążenie przetwarzanie równoległe będzie przesunięte w większości lub wszystkich przyspieszenie.  
  
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
  
2. Liczba rdzeni logicznych w systemie (stopień równoległości).  
  
     Ten punkt jest oczywistym współrzutem do poprzedniej sekcji zapytania, które są delightfully równoległe na maszynach o większej liczbie rdzeni, ponieważ praca może być dzielona między więcej współbieżnych wątków. Ogólna ilość przyspieszenie zależy od tego, jaki procent ogólnej pracy zapytania to działania równoległego. Jednak nie należy zakładać, że wszystkie zapytania będą uruchamiane dwa razy na osiem komputerów Core jako cztery podstawowe komputery. Podczas dostrajania zapytań w celu uzyskania optymalnej wydajności ważne jest, aby mierzyć rzeczywiste wyniki na komputerach z różnymi liczbami rdzeni. Ten punkt jest związany z punktem #1: większe zestawy danych są wymagane do wykorzystania większej ilości zasobów obliczeniowych.  
  
3. Liczba i rodzaj operacji.  
  
     PLINQ udostępnia operator operator AsOrdered w sytuacjach, w których konieczne jest zachowanie kolejności elementów w sekwencji źródłowej. Istnieje koszt związany z porządkowaniem, ale ten koszt jest zazwyczaj Nieumiarkowany. Operacje GroupBy i Join również powodują naliczanie kosztów. PLINQ sprawdza się najlepiej, gdy może przetwarzać elementy w kolekcji źródłowej w dowolnej kolejności i przekazywać je do następnego operatora, gdy tylko będą gotowe. Aby uzyskać więcej informacji, zobacz temat [porządkowania zamówień w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4. Forma wykonywania zapytania.  
  
     Jeśli przechowujesz wyniki zapytania przez wywołanie ToArray — lub ToList —, wyniki ze wszystkich wątków równoległych muszą zostać scalone w ramach pojedynczej struktury danych. Dotyczy to niemożliwego do uniknięcia kosztu obliczeniowego. Podobnie, w przypadku iteracji wyników przy użyciu pętli foreach (dla każdej w Visual Basic), wyniki wątków roboczych muszą być serializowane do wątku modułu wyliczającego. Jeśli jednak po prostu chcesz wykonać pewne czynności na podstawie wyniku z każdego wątku, możesz użyć metody ForAll, aby wykonać tę czynność na wielu wątkach.  
  
5. Typ opcji scalania.  
  
     PLINQ można skonfigurować w taki sposób, aby buforuje swoje dane wyjściowe, i generować go w fragmentach lub wszystkie jednocześnie po utworzeniu całego zestawu wyników lub w innym strumieniu w miarę ich produkcji. Poprzednie wyniki w skrócie łączny czas wykonywania i ostatnie wyniki zmniejszają opóźnienia między elementami.  Mimo że opcje scalania nie zawsze mają istotny wpływ na ogólną wydajność zapytań, mogą mieć wpływ na postrzeganą wydajność, ponieważ kontrolują, jak długo użytkownik musi czekać, aby zobaczyć wyniki. Aby uzyskać więcej informacji, zobacz [Opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6. Rodzaj partycjonowania.  
  
     W niektórych przypadkach zapytanie PLINQ w kolekcji źródłowej z indeksem może spowodować niezrównoważone obciążenie pracą. W takim przypadku może być możliwe zwiększenie wydajności zapytania przez utworzenie niestandardowego programu Partitioner. Aby uzyskać więcej informacji, zobacz [niestandardowe partycje dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Gdy PLINQ wybiera tryb sekwencyjny  
 PLINQ zawsze podejmie próbę wykonania zapytania co najmniej tak szybko, jak zapytanie zostanie uruchomione sekwencyjnie. Mimo że PLINQ nie sprawdza, w jaki sposób wyliczane są Delegaty użytkowników, lub jak duże jest źródło danych wejściowych, szuka określonych zapytań "Shapes". W odniesieniu do tego szuka operatorów zapytań lub kombinacji operatorów, które zwykle powodują spowolnienie wykonywania zapytania w trybie równoległym. Po znalezieniu takich kształtów PLINQ domyślnie wraca do trybu sekwencyjnego.  
  
 Jednak po pomiarze wydajności określonego zapytania można określić, że faktycznie działa szybciej w trybie równoległym. W takich przypadkach można użyć flagi <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> za pomocą metody <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>, aby nakazać PLINQ zrównoleglanie zapytania. Aby uzyskać więcej informacji, zobacz [How to: Określanie trybu wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Na poniższej liście opisano kształty zapytań, które domyślnie PLINQ są wykonywane w trybie sekwencyjnym:  
  
- Zapytania zawierające klauzulę SELECT, Indexed WHERE, Indexed SelectMany lub ElementAt po operatorze porządkowania lub filtrowania, który usunął lub zmienił rozmieszczenie oryginalnych indeksów.  
  
- Zapytania zawierające operator Take, TakeWhile —, Skip, SkipWhile — i WHERE indeksów w sekwencji źródłowej nie znajdują się w oryginalnej kolejności.  
  
- Zapytania zawierające kod zip lub SequenceEquals, chyba że jedno ze źródeł danych ma pierwotnie uporządkowany indeks, a inne źródło danych jest indeksem (tj. tablicą lub IList (T)).  
  
- Zapytania zawierające element concat, chyba że zostanie zastosowany do indeksowanych źródeł danych.  
  
- Zapytania, które zawierają zwrot, chyba że zostaną zastosowane do źródła danych z indeksem.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
