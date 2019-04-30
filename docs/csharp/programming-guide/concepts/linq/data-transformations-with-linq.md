---
title: Przekształcanie danych za pomocą LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: 5928478518b0bc1eb498381567d52d5ddba4d8b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702441"
---
# <a name="data-transformations-with-linq-c"></a>Przekształcanie danych za pomocą LINQ (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotyczy nie tylko podczas pobierania danych. Należy również zaawansowane narzędzie do przekształcania danych. Za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, można użyć sekwencji źródłowej, jak dane wejściowe i zmodyfikuj go na wiele sposobów, aby utworzyć nową sekwencję danych wyjściowych. Można zmodyfikować sekwencji bez modyfikowania samych elementów, sortowania i grupowania. Ale być może z najbardziej zaawansowanych funkcji [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania jest możliwość tworzenia nowych typów. Jest to realizowane w [wybierz](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli. Na przykład należy wykonać następujące zadania:  
  
- Scala wiele sekwencji wejściowych sekwencja pojedynczego wyjścia, która ma nowego typu.  
  
- Utwórz sekwencje danych wyjściowych, której elementy składają się z tylko jednego lub kilku właściwości każdego elementu w sekwencji źródłowej.  
  
- Utwórz sekwencje danych wyjściowych, której elementy składają się z wyniki operacji wykonywanych na danych źródłowych.  
  
- Tworzenie sekwencji wyjścia w innym formacie. Na przykład można przekształcać dane z wierszy SQL lub pliki tekstowe, w formacie XML.  
  
 Są to tylko kilka przykładów. Oczywiście można połączyć te przekształcenia na różne sposoby, w tym samym zapytaniu. Ponadto sekwencja wyjścia jedno zapytanie może służyć jako sekwencji wejściowych dla nowego zapytania.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Łączenie wielu danych wejściowych w jedną sekwencję wyjściową  
 Możesz użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby utworzyć sekwencję wyjściową, który zawiera elementy z więcej niż jednej sekwencji wejściowych. Poniższy przykład pokazuje, jak połączyć dwie struktury danych w pamięci, ale te same zasady można zastosować do łączenia danych ze źródła XML lub SQL lub zestawu danych. Załóżmy następujące typy dwóch klas:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 Poniższy kod przedstawia zapytanie:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md) i [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Wybranie podzestawu każdego elementu źródłowego  
 Istnieją dwa podstawowe sposoby, aby wybrać podzestawu każdego elementu w sekwencji źródłowej:  
  
1. Aby wybrać tylko jeden element członkowski elementu źródłowego, należy użyć operacji kropka. W poniższym przykładzie przyjęto założenie, że `Customer` obiekt zawiera kilka właściwości publicznej, w tym ciągu o nazwie `City`. Po wykonaniu tego zapytania powoduje wygenerowanie danych wyjściowych sekwencją ciągów.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Aby utworzyć elementów, które zawierają więcej niż jedną właściwość z elementu źródłowego, należy użyć inicjatora obiektów, przy użyciu nazwanego obiektu lub typu anonimowego. Poniższy przykład pokazuje użycie typu anonimowego do hermetyzacji dwie właściwości każdego z nich `Customer` elementu:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) i [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Przekształcanie obiektów w pamięci do formatu XML  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania ułatwiają do przekształcania danych między strukturami danych w pamięci, baz danych SQL, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawów danych i XML strumienie lub dokumenty. Poniższy przykład przekształca obiektów w strukturze danych w pamięci do elementów XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 Kod generuje następujące dane wyjściowe XML:  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML w języku C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Wykonywanie operacji na elementach źródłowych  
 Sekwencja wyjścia może nie zawierać żadnych elementów ani właściwości elementów z sekwencji źródłowej. Dane wyjściowe mogą być sekwencja wartości, która jest obliczana przy użyciu elementów źródła jako argumenty wejściowe. Następujące prostego zapytania, gdy jest wykonywany, generuje sekwencją ciągów, w których wartości reprezentują obliczenia oparte na sekwencję źródłową elementów typu `double`.  
  
> [!NOTE]
>  Wywoływanie metod w wyrażeniach zapytań nie jest obsługiwana, jeśli zapytanie zostanie zamieniona na innej domeny. Na przykład nie można wywołać zwykłych metodę języka C# w [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ponieważ program SQL Server ma Brak kontekstu dla niego. Można jednak procedurom składowanym w mapie do metod i wywołać te. Aby uzyskać więcej informacji, zobacz [procedur składowanych](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
- [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [select, klauzula](../../../../csharp/language-reference/keywords/select-clause.md)
