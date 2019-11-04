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
ms.openlocfilehash: 361101258caca763502f92d897866c75bc8d7da2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418720"
---
# <a name="basic-linq-query-operations-c"></a>Podstawowe operacje zapytań LINQ (C#)
Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeń zapytań i niektórych typowych rodzajów operacji wykonywanych w kwerendzie. Bardziej szczegółowe informacje znajdują się w następujących tematach:  
  
 [Wyrażenia zapytania LINQ](../../../linq/index.md)  
  
 [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)  
  
 [Przewodnik: Pisanie zapytań wC#](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Jeśli znasz już język zapytań, taki jak SQL lub XQuery, możesz pominąć większość tego tematu. Przeczytaj temat "`from` klauzula" w następnej sekcji, aby dowiedzieć się więcej na temat porządku klauzul w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.  
  
## <a name="obtaining-a-data-source"></a>Uzyskanie źródła danych  
 W zapytaniu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pierwszym krokiem jest określenie źródła danych. W C# przypadku większości języków programowania zmienna musi być zadeklarowana, zanim będzie mogła zostać użyta. W zapytaniu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] klauzula `from` jest najpierw w celu wprowadzenia źródła danych (`customers`) i *zmiennej zakresu* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Zmienna zakresu jest jak Zmienna iteracji w pętli `foreach`, z wyjątkiem braku rzeczywistej iteracji w wyrażeniu zapytania. Gdy zapytanie zostanie wykonane, zmienna zakresu będzie traktować jako odwołanie do każdego kolejnego elementu w `customers`. Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określać go jawnie. Dodatkowe zmienne zakresowe mogą być wprowadzane przez klauzulę `let`. Aby uzyskać więcej informacji, zobacz [klauzula Let](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> W przypadku nieogólnych źródeł danych, takich jak <xref:System.Collections.ArrayList>, zmienna zakresu musi być jawnie wpisana. Aby uzyskać więcej informacji, zobacz [How to: Query a ArrayList with LINQC#()](./how-to-query-an-arraylist-with-linq.md) i [from](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrowanie  
 Prawdopodobnie najbardziej typową operacją zapytania jest stosowanie filtru w postaci wyrażenia logicznego. Filtr powoduje, że zapytanie zwraca tylko te elementy, dla których wyrażenie ma wartość true. Wynik jest tworzony przy użyciu klauzuli `where`. Filtr w efekcie określa elementy, które mają zostać wykluczone z sekwencji źródłowej. W poniższym przykładzie zwracane są tylko te `customers`, które mają adres w Londynie.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Możesz użyć znanych C# operatorów logicznych `AND` i `OR`, aby zastosować dowolną liczbę wyrażeń filtrów w klauzuli `where`. Aby na przykład zwrócić tylko klientów z "Londyn" `AND`, których nazwa to "Devon", należy napisać następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Aby zwrócić klientów z Londyn lub Paryż, Napisz następujący kod:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Szeregowanie  
 Często wygodnie jest posortować zwrócone dane. Klauzula `orderby` powoduje, że elementy w zwracanej sekwencji będą sortowane zgodnie z domyślną wartością porównującą dla sortowanego typu. Na przykład następujące zapytanie można rozszerzyć, aby posortować wyniki na podstawie właściwości `Name`. Ponieważ `Name` jest ciągiem, domyślna funkcja porównująca wykonuje sortowanie alfabetyczne od A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Aby zamówić wyniki w odwrotnej kolejności, od z do A, użyj klauzuli `orderby…descending`.  
  
 Aby uzyskać więcej informacji, zobacz [klauzula OrderBy](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Grupowanie  
 Klauzula `group` pozwala grupować wyniki na podstawie określonego klucza. Można na przykład określić, że wyniki mają być pogrupowane według `City` tak, że wszyscy klienci z Londyn lub Paryż są w poszczególnych grupach. W tym przypadku `cust.City` jest kluczem.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Po zakończeniu zapytania z klauzulą `group`, wyniki mają postać listy list. Każdy element na liście jest obiektem, który ma `Key` składową i listę elementów, które są zgrupowane w tym kluczu. Podczas iteracji w zapytaniu, które tworzy sekwencję grup, należy użyć zagnieżdżonej pętli `foreach`. Pętla zewnętrzna wykonuje iterację dla każdej grupy, a pętla wewnętrzna wykonuje iterację dla wszystkich członków grupy.  
  
 Jeśli musisz odwołać się do wyników operacji grupy, możesz użyć słowa kluczowego `into`, aby utworzyć identyfikator, który może być przeszukiwany w dalszej części. Następujące zapytanie zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzula](../../../language-reference/keywords/group-clause.md)Group.  
  
## <a name="joining"></a>Łączenie  
 Operacje Join tworzą skojarzenia między sekwencjami, które nie są jawnie modelowane w źródłach danych. Na przykład możesz wykonać sprzężenie, aby znaleźć wszystkich klientów i dystrybutorów, którzy mają tę samą lokalizację. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] klauzula `join` zawsze działa w odniesieniu do kolekcji obiektów, a nie bezpośrednio w tabelach bazy danych.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nie trzeba używać `join` tak często, jak w przypadku programu SQL, ponieważ klucze obce w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] są reprezentowane w modelu obiektów jako właściwości, które zawierają kolekcję elementów. Na przykład obiekt `Customer` zawiera kolekcję obiektów `Order`. Zamiast wykonywać sprzężenie, uzyskujesz dostęp do zamówień przy użyciu notacji kropkowej:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Aby uzyskać więcej informacji, zobacz [Klauzula join](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Zaznaczenie (projekcje)  
 Klauzula `select` generuje wyniki zapytania i określa "kształt" lub typ każdego zwróconego elementu. Można na przykład określić, czy wyniki będą składać się z kompletnych `Customer` obiektów, tylko jednego elementu członkowskiego, podzestawu elementów członkowskich, czy pewnego całkowicie innego typu wyników na podstawie obliczenia lub nowego obiektu. Gdy klauzula `select` generuje coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcją*. Użycie projekcji do przekształcania danych jest zaawansowaną możliwością [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeń zapytań. Aby uzyskać więcej informacji, zobacz [przekształcenia danych za pomocąC#LINQ ()](./data-transformations-with-linq.md) i [SELECT](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia zapytania LINQ](../../../linq/index.md)
- [Przewodnik: Pisanie zapytań wC#](./walkthrough-writing-queries-linq.md)
- [Słowa kluczowe zapytania (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Typy anonimowe](../../classes-and-structs/anonymous-types.md)
