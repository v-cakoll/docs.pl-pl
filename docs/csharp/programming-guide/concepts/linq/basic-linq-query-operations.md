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
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635941"
---
# <a name="basic-linq-query-operations-c"></a>Podstawowe operacje zapytań LINQ (C#)
W tym temacie przedstawiono krótkie wprowadzenie do wyrażeń zapytań LINQ i niektórych typowych rodzajów operacji wykonywanych w kwerendzie. Bardziej szczegółowe informacje znajdują się w następujących tematach:  
  
 [Wyrażenia zapytań LINQ](../../../linq/index.md)  
  
 [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)  
  
 [Instruktaż: Pisanie zapytań w C #](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Jeśli znasz już język zapytania, taki jak SQL lub XQuery, możesz pominąć większość tego tematu. Przeczytaj o`from` "klauzuli" w następnej sekcji, aby dowiedzieć się o kolejności klauzul w wyrażeniach kwerendlinq.  
  
## <a name="obtaining-a-data-source"></a>Uzyskanie źródła danych  
 W kwerendzie LINQ pierwszym krokiem jest określenie źródła danych. W języku C#, jak w większości języków programowania zmienna musi być zadeklarowana, zanim będzie można użyć. W kwerendzie LINQ `from` klauzula jest na pierwszym miejscu`customers`w celu wprowadzenia`cust`źródła danych ( ) i *zmiennej zakresu* ( ).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Zmienna zakresu jest jak zmienna `foreach` iteracji w pętli, z tą różnicą, że w wyrażeniu kwerendy nie występuje rzeczywista iteracja. Po wykonaniu kwerendy zmienna zakresu będzie służyć jako odwołanie `customers`do każdego kolejnego elementu w programie . Ponieważ kompilator można wywnioskować typ `cust`, nie trzeba go jawnie określić. Dodatkowe zmienne zakresu mogą być `let` wprowadzone przez klauzulę. Aby uzyskać więcej informacji, zobacz [klauzulę let](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> W przypadku nieogólnych <xref:System.Collections.ArrayList>źródeł danych, takich jak zmienna zakresu, musi być jawnie wpisana. Aby uzyskać więcej informacji, zobacz [Jak wysyłać zapytania do ArrayList z LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) i [z klauzuli](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrowanie  
 Prawdopodobnie najbardziej popularną operacją kwerendy jest zastosowanie filtru w postaci wyrażenia logicznego. Filtr powoduje, że kwerenda zwraca tylko te elementy, dla których wyrażenie jest prawdziwe. Wynik jest tworzony przy `where` użyciu klauzuli. Filtr w efekcie określa, które elementy wykluczyć z sekwencji źródłowej. W poniższym przykładzie `customers` zwracane są tylko osoby, które mają adres w Londynie.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Za pomocą znanych logicznych `AND` `OR` c# i operatorów, aby zastosować `where` dowolną liczbę wyrażeń filtru, zgodnie z wymogami w klauzuli. Na przykład, aby zwrócić tylko `AND` klientów z "Londynu", którego nazwa jest "Devon", należy napisać następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Aby zwrócić klientów z Londynu lub Paryża, należy napisać następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Szeregowanie  
 Często wygodnie jest sortować zwrócone dane. Klauzula `orderby` spowoduje, że elementy w zwróconej sekwencji mają być sortowane zgodnie z domyślnym porównywarka dla typu są sortowane. Na przykład następującą kwerendę można rozszerzyć, aby `Name` posortować wyniki na podstawie właściwości. Ponieważ `Name` jest to ciąg, domyślny porównywarka wykonuje sortowanie alfabetyczne od A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Aby zamówić wyniki w odwrotnej kolejności, od `orderby…descending` Z do A, użyj klauzuli.  
  
 Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Grupowanie  
 Klauzula `group` umożliwia grupowanie wyników na podstawie klucza, który określisz. Na przykład można określić, że wyniki powinny `City` być pogrupowane według tak, aby wszyscy klienci z Londynu lub Paryża byli w poszczególnych grupach. W tym `cust.City` przypadku jest kluczem.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Po zakończeniu kwerendy `group` z klauzulą, wyniki mają formę listy list. Każdy element na liście jest obiektem, który ma element członkowski `Key` i listę elementów, które są zgrupowane pod tym kluczem. Podczas itetenowania za pomocą kwerendy, która tworzy sekwencję `foreach` grup, należy użyć pętli zagnieżdżonej. Zewnętrzna pętla itere nad każdą grupą, a wewnętrzna pętla iteuje nad członkami każdej grupy.  
  
 Jeśli musisz odwołać się do wyników operacji `into` grupy, można użyć słowa kluczowego, aby utworzyć identyfikator, który może być przeszukiwany dalej. Następująca kwerenda zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzulę group](../../../language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Dołączenie  
 Operacje sprzężenia tworzą skojarzenia między sekwencjami, które nie są jawnie modelowane w źródłach danych. Na przykład można wykonać sprzężenie, aby znaleźć wszystkich klientów i dystrybutorów, którzy mają tę samą lokalizację. W LINQ `join` klauzula zawsze działa przeciwko kolekcje obiektów zamiast tabel bazy danych bezpośrednio.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 W LINQ nie trzeba używać `join` tak często, jak to zrobić w SQL, ponieważ klucze obce w LINQ są reprezentowane w modelu obiektu jako właściwości, które posiadają kolekcję elementów. Na przykład `Customer` obiekt zawiera kolekcję `Order` obiektów. Zamiast wykonywać sprzężenie, można uzyskać dostęp do zamówień za pomocą notacji kropkowej:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Aby uzyskać więcej informacji, zobacz [klauzulę join .](../../../language-reference/keywords/join-clause.md)  
  
## <a name="selecting-projections"></a>Zaznaczenie (projekcje)  
 Klauzula `select` daje wyniki kwerendy i określa "kształt" lub typ każdego zwróconego elementu. Na przykład można określić, czy wyniki `Customer` będą składać się z kompletnych obiektów, tylko jeden element członkowski, podzbiór elementów członkowskich lub jakiś zupełnie inny typ wyniku na podstawie obliczeń lub tworzenia nowego obiektu. Gdy `select` klauzula tworzy coś innego niż kopia elementu źródłowego, operacja jest wywoływana *projekcji*. Wykorzystanie projekcji do przekształcania danych jest zaawansowaną możliwością wyrażeń zapytań LINQ. Aby uzyskać więcej informacji, zobacz [Transformacje danych z LINQ (C#)](./data-transformations-with-linq.md) i [wybierz klauzulę](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia zapytań LINQ](../../../linq/index.md)
- [Instruktaż: Pisanie zapytań w C #](./walkthrough-writing-queries-linq.md)
- [Słowa kluczowe zapytania (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Typy anonimowe](../../classes-and-structs/anonymous-types.md)
