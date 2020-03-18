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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139907"
---
# <a name="understanding-speedup-in-plinq"></a>Ogólne informacje o przyspieszeniach w PLINQ
Głównym celem PLINQ jest przyspieszenie wykonywania LINQ do obiektów zapytań wykonując delegatów kwerendy równolegle na komputerach wielordzeniowych. PLINQ działa najlepiej, gdy przetwarzanie każdego elementu w kolekcji źródłowej jest niezależna, bez współużytkowania stanu zaangażowanych między poszczególnych delegatów. Takie operacje są powszechne w LINQ do obiektów i PLINQ, i są często nazywane "*uroczo równolegle*", ponieważ nadają się łatwo do planowania na wielu wątków. Jednak nie wszystkie zapytania składają się wyłącznie z niezwykle równoległych operacji; w większości przypadków kwerenda obejmuje niektóre operatory, które albo nie mogą być równoległe lub które spowalniają wykonywanie równoległe. I nawet w przypadku zapytań, które są całkowicie uroczo równoległe, PLINQ musi nadal partycjonować źródło danych i zaplanować pracę nad wątkami i zwykle scalić wyniki po zakończeniu kwerendy. Wszystkie te operacje dodać do obliczeniowych kosztów równoległości; te koszty dodawania równoległości są nazywane *obciążeniem*. Aby osiągnąć optymalną wydajność w kwerendzie PLINQ, celem jest zmaksymalizowanie części, które są uroczo równoległe i zminimalizować części, które wymagają narzutów. Ten artykuł zawiera informacje, które pomogą Ci napisać zapytania PLINQ, które są tak wydajne, jak to możliwe, a jednocześnie daje poprawne wyniki.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Czynniki wpływające na wydajność zapytań PLINQ  
 W poniższych sekcjach wymieniono niektóre z najważniejszych czynników, które mają wpływ na wydajność kwerendy równoległej. Są to ogólne instrukcje, które same w sobie nie są wystarczające do przewidywania wydajności zapytań we wszystkich przypadkach. Jak zawsze ważne jest, aby zmierzyć rzeczywistą wydajność określonych zapytań na komputerach z szeregiem reprezentatywnych konfiguracji i obciążeń.  
  
1. Koszt obliczeniowy całej pracy.  
  
     Aby osiągnąć przyspieszenie, zapytanie PLINQ musi mieć wystarczająco dużo uroczo równoległej pracy, aby zrównoważyć obciążenie. Praca może być wyrażona jako koszt obliczeniowy każdego delegata pomnożona przez liczbę elementów w kolekcji źródłowej. Zakładając, że operacja może być równoległa, im bardziej kosztowne obliczeniowo jest, tym większa szansa na przyspieszenie. Na przykład jeśli funkcja trwa jedną milisekundę do wykonania, sekwencyjne zapytanie ponad 1000 elementów zajmie jedną sekundę, aby wykonać tę operację, podczas gdy kwerenda równoległa na komputerze z czterema rdzeniami może potrwać tylko 250 milisekund. Daje to przyspieszenie o 750 milisekund. Jeśli funkcja wymaga jednej sekundy do wykonania dla każdego elementu, przyspieszenie będzie 750 sekund. Jeśli delegat jest bardzo drogie, a następnie PLINQ może zaoferować znaczne przyspieszenie z tylko kilka elementów w kolekcji źródłowej. Z drugiej strony małe kolekcje źródłowe z trywialnymi delegatami zazwyczaj nie są dobrymi kandydatami do PLINQ.  
  
     W poniższym przykładzie queryA jest prawdopodobnie dobrym kandydatem do PLINQ, przy założeniu, że jego Select funkcja wymaga dużo pracy. queryB prawdopodobnie nie jest dobrym kandydatem, ponieważ nie ma wystarczającej ilości pracy w Select instrukcji, a obciążenie równoległości zrównoważy większość lub wszystkie przyspieszenie.  
  
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
  
     Ten punkt jest oczywistym następstwem poprzedniej sekcji, zapytania, które są uroczo równolegle uruchomić szybciej na komputerach z większą liczbą rdzeni, ponieważ praca może być podzielona między bardziej równoczesnych wątków. Całkowita ilość przyspieszenia zależy od tego, jaki procent ogólnej pracy kwerendy jest równoległy. Jednak nie należy zakładać, że wszystkie kwerendy będą uruchamiane dwa razy szybciej na komputerze ośmiordzeniowym niż czterordzeniowy komputer. Podczas dostrajania zapytań w celu uzyskania optymalnej wydajności, ważne jest, aby zmierzyć rzeczywiste wyniki na komputerach z różnych liczb rdzeni. Ten punkt jest związany z punktem #1: większe zestawy danych są wymagane do korzystania z większych zasobów obliczeniowych.  
  
3. Liczba i rodzaj operacji.  
  
     PLINQ udostępnia AsOrdered operatora dla sytuacji, w których jest konieczne do utrzymania kolejności elementów w sekwencji źródłowej. Istnieje koszt związany z zamówieniem, ale koszt ten jest zwykle skromny. GroupBy i Join operacji również ponieść obciążenie. PLINQ działa najlepiej, gdy jest dozwolone do przetwarzania elementów w kolekcji źródłowej w dowolnej kolejności i przekazać je do następnego operatora, jak tylko są one gotowe. Aby uzyskać więcej informacji, zobacz [Zachowanie zamówień w PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4. Forma wykonywania zapytań.  
  
     Jeśli przechowujesz wyniki kwerendy, wywołując ToArray lub ToList, wyniki ze wszystkich równoległych wątków muszą zostać scalone w strukturę pojedynczych danych. Wiąże się to z nieuniknionymi kosztami obliczeniowymi. Podobnie jeśli iterate wyniki przy użyciu foreach (For Each w języku Visual Basic) pętli, wyniki z wątków roboczych muszą być serializowane na wątku modułu wyliczania. Ale jeśli chcesz po prostu wykonać niektóre działania na podstawie wyniku z każdego wątku, można użyć ForAll metody do wykonywania tej pracy na wielu wątków.  
  
5. Typ opcji scalania.  
  
     PLINQ można skonfigurować do buforowania jego danych wyjściowych i produkować go w fragmentach lub wszystkie na raz po wygenerowaniu całego zestawu wyników, albo do strumieniowania poszczególnych wyników, ponieważ są one produkowane. Pierwsze powoduje skrócenie całkowitego czasu wykonywania, a drugi powoduje zmniejszenie opóźnienia między elementami plonów.  Opcje scalania nie zawsze mają duży wpływ na ogólną wydajność zapytań, ale mogą mieć wpływ na postrzeganą wydajność, ponieważ kontrolują, jak długo użytkownik musi czekać, aby zobaczyć wyniki. Aby uzyskać więcej informacji, zobacz [Opcje scalania w plinq](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6. Rodzaj partycjonowania.  
  
     W niektórych przypadkach kwerendy PLINQ za względem indeksowalnej kolekcji źródłowej może spowodować niezrównoważone obciążenie pracą. W takim przypadku można zwiększyć wydajność kwerendy, tworząc niestandardowy partycjonator. Aby uzyskać więcej informacji, zobacz [Partycjonery niestandardowe dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Kiedy PLINQ wybiera tryb sekwencyjny  
 PLINQ zawsze będzie próbował wykonać kwerendę co najmniej tak szybko, jak kwerenda będzie działać sekwencyjnie. Mimo że PLINQ nie patrzy na to, jak obliczeniowo drogie są delegaci użytkownika lub jak duże jest źródło danych wejściowych, to nie szukać niektórych zapytań "kształty". W szczególności wyszukuje operatorów zapytań lub kombinacji operatorów, które zazwyczaj powodują kwerendy do wykonywania wolniej w trybie równoległym. Po znalezieniu takich kształtów funkcja PLINQ domyślnie powraca do trybu sekwencyjnego.  
  
 Jednak po zmierzeniu wydajności określonej kwerendy można określić, że faktycznie działa szybciej w trybie równoległym. W takich przypadkach można <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> flagi za pomocą metody, aby poinstruować PLINQ do równoległości kwerendy. Aby uzyskać więcej informacji, zobacz [Jak: Określić tryb wykonywania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Na poniższej liście opisano kształty kwerend, które plinq domyślnie będzie wykonywać w trybie sekwencyjnym:  
  
- Kwerendy, które zawierają Select, indeksowane Gdzie, indeksowane SelectMany lub ElementAt klauzuli po zamawiania lub filtrowania operatora, który usunął lub zmienił kolejność oryginalnych indeksów.  
  
- Zapytania, które zawierają Take, TakeWhile, Skip, SkipWhile operatora i gdzie indeksy w sekwencji źródłowej nie są w oryginalnej kolejności.  
  
- Kwerendy zawierające zip lub SequenceEquals, chyba że jedno ze źródeł danych ma pierwotnie uporządkowany indeks, a inne źródło danych jest indeksowalne (tj. tablica lub IList(T)).  
  
- Kwerendy, które zawierają Concat, chyba że jest stosowany do indeksowalnych źródeł danych.  
  
- Kwerendy, które zawierają Reverse, chyba że stosowane do źródła danych indeksowalny.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
