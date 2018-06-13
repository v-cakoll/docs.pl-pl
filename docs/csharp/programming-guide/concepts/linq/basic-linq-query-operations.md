---
title: Podstawowe operacje zapytań LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 2825b79c9638fff050522da43184a8d95a3fe02f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333043"
---
# <a name="basic-linq-query-operations-c"></a>Podstawowe operacje zapytań LINQ (C#)
Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażeń i niektóre rodzaje typowych operacji wykonywanych w zapytaniu. Bardziej szczegółowe informacje są w następujących tematach:  
  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Wskazówki: Pisanie zapytań w języku C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Jeśli już znasz język zapytania, takie jak SQL lub wyrażenie XQuery, możesz pominąć większość tego tematu. Przeczytaj informacje o "`from` klauzuli" w następnej sekcji, aby dowiedzieć się więcej o zamówieniu klauzule [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań.  
  
## <a name="obtaining-a-data-source"></a>Uzyskanie źródła danych  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, pierwszym krokiem jest określenie źródła danych. W języku C#, tak jak większość języków programowania zmiennej musi być zadeklarowany, zanim będzie można go używać. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, `from` klauzuli przypada wcześniej w celu wprowadzenia źródła danych (`customers`) i *zmiennej zakresu* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 Zmienna zakresu przypomina zmiennej iteracji w `foreach` pętli z tą różnicą, że występuje nie rzeczywiste iteracji w wyrażeniu zapytania. Podczas wykonywania zapytania zmienna zakresu będzie służyć jako odwołanie do każdy element w `customers`. Ponieważ kompilator można wywnioskować typu elementu `cust`, nie trzeba określić ręcznie. Zmienne zakresu dodatkowe może zostać wprowadzony przez `let` klauzuli. Aby uzyskać więcej informacji, zobacz [klauzula let](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  Dla danych nierodzajową źródeł takich jak <xref:System.Collections.ArrayList>, zmienna zakresu musi być jawnie określone typy. Aby uzyskać więcej informacji, zobacz [porady: zapytanie w ArrayList za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) i [klauzuli from](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrowanie  
 Prawdopodobnie najbardziej typowych operacji zapytania jest stosowanie filtru w postaci wyrażenia logicznego. Filtr powoduje, że kwerenda zwraca tylko te elementy, dla których wyrażenie jest prawdziwe. Wynik jest generowany przy użyciu `where` klauzuli. Filtr skutkuje Określa, które elementy do wykluczenia z sekwencji źródłowej. W poniższym przykładzie, tylko te `customers` mających adresu w Londynie są zwracane.  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 Można użyć znanych C# logicznej `AND` i `OR` operatory stosować jak wyrażenia w razie potrzeby w wielu filtru `where` klauzuli. Na przykład, aby zwrócić tylko w przypadku klientów z "Londynie" `AND` których nazwa to "Devon" piszesz następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 Aby przywrócić klientów w Londynie lub Paryża, czy zapisu następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [gdzie klauzuli](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Szeregowanie  
 Często jest wygodne posortuj zwrócone dane. `orderby` Klauzuli spowoduje, że elementy w sekwencji zwrócony ma zostać posortowana według typu sortowane domyślna funkcja porównująca. Na przykład poniższe zapytanie można rozszerzyć do sortowania wyników na podstawie `Name` właściwości. Ponieważ `Name` jest ciągiem, domyślna funkcja porównująca przeprowadza alfabetycznej sortowania z zakresu od A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 Aby w odwrotnej kolejności kolejność wyników z malejąco, należy użyć `orderby…descending` klauzuli.  
  
 Aby uzyskać więcej informacji, zobacz [klauzula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Grupowanie  
 `group` Klauzuli umożliwiają grupowanie wyników według klucza, który określisz. Na przykład można określić, czy wyniki powinny zostać utworzone przez `City` tak, aby wszystkich klientów w Londynie lub Paryża znajdują się w poszczególnych grupach. W takim przypadku `cust.City` jest kluczem.  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 Kiedy zakończysz zapytanie z `group` klauzuli wyniki formę listę list. Każdy element na liście jest obiekt, który ma `Key` element członkowski i listę elementów, które są zgrupowane w tym kluczu. Iteracja kwerendę, która tworzy sekwencję grupy, należy używać zagnieżdżoną `foreach` pętli. Zewnętrzne pętli przechodzi przez każdą grupę, a wewnętrzny pętli przechodzi przez członków poszczególnych grup.  
  
 Jeśli musi odwoływać się do wyniki operacji grupy, możesz użyć `into` — słowo kluczowe można utworzyć identyfikatora, który może być badana dodatkowe. Następujące zapytanie zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzuli group](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Łączenie  
 Operacji łączenia tworzenia skojarzenia między sekwencji nie są jawnie modelowane w źródłach danych. Na przykład można wykonywać na przyłączenie do wszystkich klientów i dystrybutorów, którzy mają tę samą lokalizację. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` klauzuli zawsze działa w względem kolekcji obiektów zamiast tabel bazy danych bezpośrednio.  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nie trzeba używać `join` tyle razy, tak jak w języku SQL, ponieważ klucze obce w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] reprezentowany w modelu obiektu właściwości, które zawiera kolekcję elementów. Na przykład `Customer` obiektu zawiera kolekcję `Order` obiektów. Zamiast wykonywanie sprzężenia, dostęp do zamówienia, używając zapisu kropkowego:  
  
```  
from order in Customer.Orders...  
```  
  
 Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Zaznaczenie (projekcje)  
 `select` Klauzuli tworzy wyniki zapytania i określa "kształtu" lub typ każdego zwróconego elementu. Na przykład można określić, czy wyniki będzie składać się z pełną `Customer` obiekty, tylko jeden element członkowski, podzestaw elementów członkowskich lub typu całkowicie różne wyniki na podstawie obliczeń lub tworzenia nowego obiektu. Gdy `select` klauzuli powoduje inną niż kopię elementu źródła, operacja jest wywoływana *projekcji*. Korzystanie z projekcje do przekształcania danych jest zaawansowanych możliwości [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań. Aby uzyskać więcej informacji, zobacz [Przekształcanie danych za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) i [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Wskazówki: Pisanie zapytań w języku C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Słowa kluczowe zapytania (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [Typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
