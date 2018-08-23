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
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42753951"
---
# <a name="basic-linq-query-operations-c"></a>Podstawowe operacje zapytań LINQ (C#)
Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażeń i niektóre typowe rodzaje operacji, które można wykonywać w zapytaniu. Więcej szczegółowych informacji znajduje się w następujących tematach:  
  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Wskazówki: Pisanie zapytań w języku C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Jeśli już znasz język zapytań, takich jak bazy danych SQL lub wyrażenie XQuery, możesz pominąć większość części tego tematu. Przeczytaj o "`from` klauzuli" w następnej sekcji, aby dowiedzieć się więcej na temat kolejności klauzul [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.  
  
## <a name="obtaining-a-data-source"></a>Uzyskanie źródła danych  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, pierwszym krokiem jest określenie źródła danych. W języku C#, tak jak większość języków programowania zmiennej musi być zadeklarowany przed jego użyciem. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, `from` klauzuli, co nastąpi wcześniej w celu wprowadzenia źródła danych (`customers`) i *zmiennej zakresu* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 Zmienna zakresu jest podobna do zmiennej iteracji w `foreach` pętli z tą różnicą, że nie rzeczywiste iteracji odbywa się w wyrażeniu zapytania. Po wykonaniu zapytania zmienna zakresu będzie służyć jako odwołanie do każdy element w `customers`. Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określić ręcznie. Zmienne dodatkowy zakres może zostać wprowadzony przez `let` klauzuli. Aby uzyskać więcej informacji, zobacz [let, klauzula](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  Przypadku nieogólnego źródeł danych takich jak <xref:System.Collections.ArrayList>, musi jawnie wpisana zmienna zakresu. Aby uzyskać więcej informacji, zobacz [porady: zapytanie w ArrayList za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) i [klauzuli from](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrowanie  
 Prawdopodobnie najbardziej typowych operacji zapytania polega na zastosowaniu filtrowania w postaci wyrażenia logicznego. Filtr powoduje, że zapytanie, aby zwrócić tylko te elementy, dla których wyrażenie jest prawdziwe. Wynik jest generowany przy użyciu `where` klauzuli. Filtr w praktyce określa, które elementy, które mają zostać wykluczone z sekwencji źródłowej. W poniższym przykładzie, tylko te `customers` mających adresu w Londynie są zwracane.  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 Możesz użyć znanej języka C# logiczne `AND` i `OR` operatory do zastosowania jako wiele filtr wyrażeń zgodnie z potrzebami `where` klauzuli. Na przykład, aby zwrócić tylko w przypadku klientów z "Londyn" `AND` której nazwa to "Devon", należy napisać następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 Aby zwrócić klienci z Londynu lub Paryż, należy napisać następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Szeregowanie  
 Często jest wygodne, posortuj zwrócone dane. `orderby` Klauzuli spowoduje, że elementy w zwracanej sekwencji, która ma zostać posortowana według domyślny moduł porównujący dla typu posortowana. Na przykład, następujące zapytanie można rozszerzyć, aby posortować wyniki na podstawie `Name` właściwości. Ponieważ `Name` jest ciągiem, domyślny moduł porównujący przeprowadza sortowania alfabetycznego od A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 Aby uporządkować wyniki w odwrotnej kolejności od Z do A, należy użyć `orderby…descending` klauzuli.  
  
 Aby uzyskać więcej informacji, zobacz [klauzuli orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Grupowanie  
 `group` Klauzuli umożliwiają grupowanie wyników według klucza, który określisz. Na przykład można określić, czy wyniki powinny być grupowane według `City` tak, aby wszyscy klienci z Londynu lub Paryż znajdują się w poszczególnych grupach. W tym przypadku `cust.City` jest kluczem.  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 Zakończenia zapytanie o `group` klauzuli wyniki formę listę list. Każdy element na liście jest obiektem, który ma `Key` elementu członkowskiego i listę elementów, które są grupowane w ramach tego klucza. Podczas iteracji ciągu zapytania, który wytwarza sekwencję grup, należy użyć zagnieżdżoną `foreach` pętli. Zewnętrzna pętla wykonuje iterację na każdą grupę i wewnętrzną pętlę iteruje przez elementy członkowskie w każdej grupie.  
  
 Jeśli musi odwoływać się do wyniki operacji grupy, możesz użyć `into` — słowo kluczowe do tworzenia identyfikatorów, które mogą być dodatkowo przeszukiwane. Następujące zapytanie zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Łączenie  
 Operacje sprzężenia Tworzenie skojarzenia między sekwencjami nie są jawnie modelowane w źródłach danych. Na przykład można wykonywać na przyłączenie do znalezienia wszystkich klientów i dystrybutorów, którzy mają tej samej lokalizacji. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` zawsze działa się klauzuli względem kolekcji obiektów zamiast tabel bazy danych dotyczące bezpośrednio.  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nie trzeba używać `join` tak często, jak to zrobić w języku SQL, ponieważ klucze obce w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] są reprezentowane w modelu obiektu jako właściwości używane do przechowywania kolekcji elementów. Na przykład `Customer` obiekt zawiera zbiór `Order` obiektów. Zamiast wykonywanie sprzężenia, używając zapisu kropkowego dostęp zamówienia:  
  
```  
from order in Customer.Orders...  
```  
  
 Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Zaznaczenie (projekcje)  
 `select` Klauzuli produkuje wyniki zapytania i określa "kształt" lub typ każdego elementu zwróconego. Na przykład można określić, czy wyniki będą zawierać pełną `Customer` obiektów, tylko jeden element członkowski, podzestaw elementów członkowskich lub typu całkowicie różne wyniki na podstawie obliczeń lub tworzenia nowego obiektu. Gdy `select` klauzuli tworzy coś innego niż kopię elementu źródłowego, operacja jest nazywana *projekcji*. Korzystanie z projekcji do przekształcania danych jest zaawansowaną możliwością [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań. Aby uzyskać więcej informacji, zobacz [Przekształcanie danych za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) i [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Wskazówki: Pisanie zapytań w języku C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Słowa kluczowe zapytania (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [Typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
