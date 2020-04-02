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
ms.openlocfilehash: 60df814e18f473d84c260511292666c524fda7b7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588077"
---
# <a name="understanding-speedup-in-plinq"></a>Ogólne informacje o przyspieszeniach w PLINQ
Głównym celem PLINQ jest przyspieszenie wykonywania LINQ do obiektów kwerendy wykonując delegatów kwerendy równolegle na komputerach wielordzeniowych. PLINQ sprawdza się najlepiej, gdy przetwarzanie każdego elementu w kolekcji źródłowej jest niezależne, bez współużytkowania stanu między poszczególnymi delegatami. Takie operacje są powszechne w LINQ do obiektów i PLINQ i są często nazywane *"uroczo równolegle",* ponieważ łatwo nadają się do planowania na wielu wątkach. Jednak nie wszystkie zapytania składają się wyłącznie z uroczo równoległych operacji; w większości przypadków kwerenda obejmuje niektóre operatory, które nie mogą być równoległe lub spowolnić wykonywanie równoległe. I nawet w przypadku zapytań, które są całkowicie uroczo równoległe, PLINQ musi nadal partycjonować źródło danych i zaplanować pracę nad wątkami i zwykle scalać wyniki po zakończeniu kwerendy. Wszystkie te operacje dodać do kosztu obliczeniowego równoległości; te koszty dodawania równoległości są nazywane *obciążeniem.* Aby osiągnąć optymalną wydajność w zapytaniu PLINQ, celem jest maksymalizacja części, które są uroczo równoległe i zminimalizowanie części, które wymagają narzutów. Ten artykuł zawiera informacje, które pomogą Ci napisać zapytania PLINQ, które są tak wydajne, jak to możliwe, a jednocześnie daje poprawne wyniki.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Czynniki wpływające na wydajność kwerend PLINQ  
 W poniższych sekcjach wymieniono niektóre z najważniejszych czynników, które wpływają na wydajność zapytań równoległych. Są to ogólne instrukcje, które same w sobie nie są wystarczające do przewidywania wydajności kwerendy we wszystkich przypadkach. Jak zawsze ważne jest, aby zmierzyć rzeczywistą wydajność określonych zapytań na komputerach z zakresu reprezentatywnych konfiguracji i obciążeń.  
  
1. Koszt obliczeniowy całej pracy.  
  
     Aby osiągnąć przyspieszenie, zapytanie PLINQ musi mieć wystarczająco dużo pracy równolegle, aby zrównoważyć obciążenie. Praca może być wyrażona jako koszt obliczeniowy każdego delegata pomnożone przez liczbę elementów w kolekcji źródłowej. Zakładając, że operacja może być równoległa, im bardziej kosztowna pod względem obliczeniowym, tym większa szansa na przyspieszenie. Na przykład jeśli funkcja trwa jedną milisekundę do wykonania, kwerendy sekwencyjnej ponad 1000 elementów zajmie jedną sekundę, aby wykonać tę operację, podczas gdy kwerenda równoległa na komputerze z czterema rdzeniami może potrwać tylko 250 milisekund. Daje to przyspieszenie 750 milisekund. Jeśli funkcja wymaga jednej sekundy do wykonania dla każdego elementu, przyspieszenie będzie 750 sekund. Jeśli delegat jest bardzo drogie, a następnie PLINQ może zaoferować znaczne przyspieszenie tylko kilka elementów w kolekcji źródłowej. Z drugiej strony, małe kolekcje źródłowe z trywialnymi delegatami na ogół nie są dobrymi kandydatami do PLINQ.  
  
     W poniższym przykładzie queryA jest prawdopodobnie dobrym kandydatem do PLINQ, przy założeniu, że jego funkcja Select wymaga dużo pracy. queryB prawdopodobnie nie jest dobrym kandydatem, ponieważ nie ma wystarczającej ilości pracy w Select instrukcji, a obciążenie równoległości będzie kompensowane większość lub wszystkie przyspieszenia.  
  
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
  
     Ten punkt jest oczywistym następstwem poprzedniej sekcji, kwerendy, które są uroczo równoległe działać szybciej na komputerach z większą licznymi rdzeniami, ponieważ praca może być podzielona między więcej równoczesnych wątków. Całkowita ilość przyspieszenia zależy od tego, jaki procent ogólnej pracy kwerendy jest równoległy. Nie należy jednak zakładać, że wszystkie kwerendy będą uruchamiane dwa razy szybciej na komputerze z ośmiordzeniowym komputerem niż na komputerze czterordzeniowym. Podczas dostrajania zapytań w celu uzyskania optymalnej wydajności ważne jest mierzenie rzeczywistych wyników na komputerach z różną liczbą rdzeni. Ten punkt jest związany z punktami #1: większe zestawy danych są wymagane do korzystania z większych zasobów obliczeniowych.  
  
3. Liczba i rodzaj operacji.  
  
     PLINQ zapewnia AsOrdered operatora w sytuacjach, w których jest to konieczne do utrzymania kolejności elementów w sekwencji źródłowej. Istnieje koszt związany z zamawianiem, ale koszt ten jest zwykle niewielki. Operacje GroupBy i Join również ponoszą obciążenie. PLINQ działa najlepiej, gdy jest dozwolone do przetwarzania elementów w kolekcji źródłowej w dowolnej kolejności i przekazać je do następnego operatora, jak tylko są gotowe. Aby uzyskać więcej informacji, zobacz [Zachowanie porządku w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4. Forma wykonywania kwerendy.  
  
     Jeśli przechowujesz wyniki kwerendy, wywołując ToArray lub ToList, wyniki ze wszystkich równoległych wątków muszą zostać scalone w strukturze pojedynczych danych. Wiąże się to z nieuniknionym kosztem obliczeniowym. Podobnie, jeśli iteracji wyników przy użyciu foreach (Dla każdego w języku Visual Basic) pętli, wyniki z wątków procesu roboczego muszą być serializowane na wątku modułu wyliczacza. Ale jeśli chcesz po prostu wykonać pewną akcję na podstawie wyniku z każdego wątku, można użyć ForAll metody do wykonywania tej pracy na wiele wątków.  
  
5. Typ opcji scalania.  
  
     PLINQ można skonfigurować do buforowania jego danych wyjściowych i produkować go w kawałkach lub wszystkie na raz po cały zestaw wyników jest produkowany lub do strumienia poszczególnych wyników, ponieważ są one produkowane. Pierwszy z nich powoduje skrócenie całkowitego czasu wykonania, a drugi powoduje zmniejszenie opóźnienia między elementów uzyskanych.  Chociaż opcje scalania nie zawsze mają duży wpływ na ogólną wydajność zapytań, mogą mieć wpływ na postrzeganą wydajność, ponieważ kontrolują, jak długo użytkownik musi czekać, aby zobaczyć wyniki. Aby uzyskać więcej informacji, zobacz [Opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6. Rodzaj partycjonowania.  
  
     W niektórych przypadkach kwerendy PLINQ za pomocą kolekcji źródłowej z możliwością indeksowania może spowodować niezrównoważone obciążenie pracą. W takim przypadku może być w stanie zwiększyć wydajność kwerendy, tworząc niestandardowy partitioner. Aby uzyskać więcej informacji, zobacz [Niestandardowe partitionery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Kiedy PLINQ wybiera tryb sekwencyjny  
 PLINQ zawsze będzie próbował wykonać kwerendę co najmniej tak szybko, jak kwerenda będzie działać sekwencyjnie. Mimo że PLINQ nie patrzy na to, jak kosztowne obliczeniowo są delegaci użytkownika lub jak duże jest źródło danych wejściowych, szuka niektórych zapytań "kształty". W szczególności wyszukuje operatorów zapytań lub kombinacji operatorów, które zazwyczaj powodują kwerendy do wykonywania wolniej w trybie równoległym. Po znalezieniu takich kształtów PLINQ domyślnie powraca do trybu sekwencyjnego.  
  
 Jednak po zmierzeniu wydajności określonej kwerendy można ustalić, że faktycznie działa szybciej w trybie równoległym. W takich przypadkach można <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> flagi za pomocą metody, aby poinstruować PLINQ do równoległości kwerendy. Aby uzyskać więcej informacji, zobacz [Jak: Określanie trybu wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Na poniższej liście opisano kształty kwerendy, które PLINQ domyślnie będzie wykonywane w trybie sekwencyjnym:  
  
- Kwerendy, które zawierają Select, indeksowane Gdzie, indeksowane SelectMany lub ElementAt klauzuli po operator zamawiania lub filtrowania, który usunął lub przeorganizował oryginalne indeksy.  
  
- Zapytania, które zawierają Take, TakeWhile, SkipWhile operatora i gdzie indeksy w sekwencji źródłowej nie są w oryginalnej kolejności.  
  
- Kwerendy, które zawierają Zip lub SequenceEquals, chyba że jedno ze źródeł danych ma pierwotnie uporządkowany indeks, a inne źródło danych jest indeksowalne (tj. tablica lub IList(T)).  
  
- Kwerendy, które zawierają Concat, chyba że jest stosowany do indeksowalnych źródeł danych.  
  
- Kwerendy zawierające reverse, chyba że są stosowane do źródła danych z wymienią.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
