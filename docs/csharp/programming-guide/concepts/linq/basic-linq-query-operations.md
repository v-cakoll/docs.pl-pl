---
title: Podstawowe operacje zapytań LINQ (C#)
description: Wprowadź siebie w wyrażeniach zapytań LINQ i niektórych operacji, które możesz wykonać w zapytaniu.
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
ms.openlocfilehash: d9653be8b67ef4d971c157b8dd8d82b2ae3c2287
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105521"
---
# <a name="basic-linq-query-operations-c"></a>Podstawowe operacje zapytań LINQ (C#)
Ten temat zawiera krótkie wprowadzenie do wyrażeń zapytań LINQ i niektórych typowych rodzajów operacji wykonywanych w zapytaniu. Bardziej szczegółowe informacje znajdują się w następujących tematach:  
  
 [Wyrażenia zapytania LINQ](../../../linq/index.md)  
  
 [Standardowe operatory zapytań — Omówienie (C#)](./standard-query-operators-overview.md)  
  
 [Przewodnik: Pisanie zapytań w języku C #](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Jeśli znasz już język zapytań, taki jak SQL lub XQuery, możesz pominąć większość tego tematu. Przeczytaj temat " `from` klauzula" w następnej sekcji, aby dowiedzieć się więcej na temat porządku klauzul w wyrażeniach zapytań LINQ.  
  
## <a name="obtaining-a-data-source"></a>Uzyskanie źródła danych  
 W zapytaniu LINQ pierwszym krokiem jest określenie źródła danych. W języku C#, jak w większości języków programowania, zmienna musi być zadeklarowana, zanim będzie można jej użyć. W zapytaniu LINQ `from` klauzula jest najpierw w celu wprowadzenia źródła danych ( `customers` ) i *zmiennej zakresu* ( `cust` ).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Zmienna zakresu jest jak Zmienna iteracji w `foreach` pętli, z wyjątkiem tego, że w wyrażeniu zapytania nie ma rzeczywistej iteracji. Gdy zapytanie zostanie wykonane, zmienna zakresu będzie traktować jako odwołanie do każdego kolejnego elementu w `customers` . Ponieważ kompilator może wywnioskować typ `cust` , nie trzeba określać go jawnie. Dodatkowe zmienne zakresów można wprowadzać przez `let` klauzulę. Aby uzyskać więcej informacji, zobacz [klauzula Let](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> W przypadku nieogólnych źródeł danych, takich jak <xref:System.Collections.ArrayList> , zmienna zakresu musi być jawnie wpisana. Aby uzyskać więcej informacji, zobacz [How to Query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) i [from](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrowanie  
 Prawdopodobnie najbardziej typową operacją zapytania jest stosowanie filtru w postaci wyrażenia logicznego. Filtr powoduje, że zapytanie zwraca tylko te elementy, dla których wyrażenie ma wartość true. Wynik jest tworzony przy użyciu `where` klauzuli. Filtr w efekcie określa elementy, które mają zostać wykluczone z sekwencji źródłowej. W poniższym przykładzie zwracane są tylko te `customers` osoby, które mają adres w Londynie.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Możesz użyć znanych operatorów logicznych języka C# `AND` , `OR` Aby zastosować dowolną liczbę wyrażeń filtrów w `where` klauzuli. Aby na przykład zwrócić tylko klientów z "Londyn" o `AND` nazwie "Devon", należy napisać następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Aby zwrócić klientów z Londyn lub Paryż, Napisz następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Szeregowanie  
 Często wygodnie jest posortować zwrócone dane. `orderby`Klauzula spowoduje, że elementy w zwracanej sekwencji będą sortowane zgodnie z domyślną wartością porównującą dla sortowanego typu. Na przykład następujące zapytanie można rozszerzyć, aby posortować wyniki na podstawie `Name` właściwości. Ponieważ `Name` jest ciągiem, domyślna funkcja porównująca wykonuje alfabetyczne sortowanie od a do z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Aby zamówić wyniki w odwrotnej kolejności, od z do A, użyj `orderby…descending` klauzuli.  
  
 Aby uzyskać więcej informacji, zobacz [klauzula OrderBy](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Grupowanie  
 `group`Klauzula pozwala grupować wyniki na podstawie określonego klucza. Można na przykład określić, że wyniki mają być pogrupowane według, `City` aby wszyscy klienci z Londyn lub Paryż w poszczególnych grupach. W tym przypadku `cust.City` jest kluczem.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Po zakończeniu zapytania z `group` klauzulą wyniki mają postać listy list. Każdy element na liście jest obiektem, który ma `Key` element członkowski i listę elementów, które są zgrupowane w tym kluczu. Podczas iteracji w zapytaniu, które tworzy sekwencję grup, należy użyć zagnieżdżonej `foreach` pętli. Pętla zewnętrzna wykonuje iterację dla każdej grupy, a pętla wewnętrzna wykonuje iterację dla wszystkich członków grupy.  
  
 Jeśli musisz odwołać się do wyników operacji grupy, możesz użyć `into` słowa kluczowego, aby utworzyć identyfikator, który może być przeszukiwany w dalszej części. Następujące zapytanie zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzula](../../../language-reference/keywords/group-clause.md)Group.  
  
## <a name="joining"></a>Dołączenie  
 Operacje Join tworzą skojarzenia między sekwencjami, które nie są jawnie modelowane w źródłach danych. Na przykład możesz wykonać sprzężenie, aby znaleźć wszystkich klientów i dystrybutorów, którzy mają tę samą lokalizację. W LINQ `join` klauzula zawsze działa w odniesieniu do kolekcji obiektów, a nie bezpośrednio w tabelach bazy danych.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 W LINQ nie trzeba używać `join` tak często jak w przypadku programu SQL, ponieważ klucze obce w LINQ są reprezentowane w modelu obiektów jako właściwości, które przechowują kolekcję elementów. Na przykład `Customer` obiekt zawiera kolekcję `Order` obiektów. Zamiast wykonywać sprzężenie, uzyskujesz dostęp do zamówień przy użyciu notacji kropkowej:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Aby uzyskać więcej informacji, zobacz [Klauzula join](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Zaznaczenie (projekcje)  
 `select`Klauzula tworzy wyniki zapytania i określa "kształt" lub typ każdego zwróconego elementu. Można na przykład określić, czy wyniki będą składać się z kompletnych `Customer` obiektów, tylko jednego elementu członkowskiego, podzestawu elementów członkowskich, czy pewnego całkowicie innego typu wyników na podstawie obliczeń lub tworzenia nowego obiektu. Gdy `select` klauzula generuje coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcją*. Użycie projekcji do przekształcania danych jest zaawansowaną funkcją wyrażeń zapytań LINQ. Aby uzyskać więcej informacji, zobacz [przekształcenia danych za pomocą LINQ (C#)](./data-transformations-with-linq.md) i [SELECT](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia zapytania LINQ](../../../linq/index.md)
- [Przewodnik: Pisanie zapytań w języku C #](./walkthrough-writing-queries-linq.md)
- [Słowa kluczowe zapytania (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Typy anonimowe](../../classes-and-structs/anonymous-types.md)
