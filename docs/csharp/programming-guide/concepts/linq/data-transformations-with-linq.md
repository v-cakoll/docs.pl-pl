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
ms.openlocfilehash: c165f78c53cec0417d39320580b812ff01fef68b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333261"
---
# <a name="data-transformations-with-linq-c"></a>Przekształcanie danych za pomocą LINQ (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotyczy nie tylko pobieranie danych. Istnieje również zaawansowane narzędzia do przekształcania danych. Za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy, można użyć sekwencji źródłowej, jak dane wejściowe, a następnie zmodyfikować go na wiele sposobów, aby utworzyć nową sekwencję danych wyjściowych. Można zmodyfikować sekwencji bez modyfikowania ze sobą elementy sortowania i grupowania. Być może z najbardziej zaawansowanych funkcji, ale [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania jest możliwość tworzenia nowych typów. Jest to realizowane w [wybierz](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli. Na przykład można wykonywać następujące zadania:  
  
-   Scala wiele sekwencji wejściowych sekwencji pojedynczym wyjściowym zawierającej nowego typu.  
  
-   Tworzenie sekwencji danych wyjściowych, której elementy składają się z tylko jednego lub kilku właściwości każdego elementu w sekwencji źródłowej.  
  
-   Tworzenie sekwencji dane wyjściowe, której elementy zawierać wyniki operacji wykonywanych na źródle danych.  
  
-   Tworzenie sekwencji dane wyjściowe w innym formacie. Na przykład można przekształcać dane z plików tekstowych lub wierszy SQL w formacie XML.  
  
 Są to tylko kilka przykładów. Oczywiście przekształcenia te można łączyć w różny sposób w jednym zapytaniu. Ponadto sekwencję wyjściową jednego zapytania może służyć jako sekwencja wejściowa dla nowego zapytania.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Łączenie wielu danych wejściowych w jedną sekwencję wyjściową  
 Można użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie w celu utworzenia sekwencji danych wyjściowych, która zawiera elementy z więcej niż jeden sekwencji wejściowych. Poniższy przykład pokazuje, jak połączyć dwóch struktury danych w pamięci, ale te same zasady mogą być stosowane do łączenia danych ze źródeł XML lub SQL lub zestawu danych. Załóżmy następujące dwie klasy:  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 W poniższym przykładzie przedstawiono zapytania:  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md) i [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Wybranie podzestawu każdego elementu źródłowego  
 Istnieją dwa podstawowe sposoby wybierać podzestaw każdego elementu w sekwencji źródłowej:  
  
1.  Aby wybrać tylko jeden element członkowski elementu źródłowego, za pomocą operacji kropki. W poniższym przykładzie przyjęto założenie, że `Customer` obiekt zawiera kilka właściwości publicznej, w tym ciągu o nazwie `City`. Podczas wykonywania tego zapytania spowoduje utworzenie danych wyjściowych sekwencję ciągów.  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  Do tworzenia elementów, które zawierają więcej niż jedną właściwość z elementu źródłowego, używając inicjatora obiektów nazwanego obiektu lub typu anonimowego. W poniższym przykładzie przedstawiono użycie typu anonimowego w celu hermetyzacji dwie właściwości z każdej `Customer` elementu:  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) i [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Przekształcanie obiektów w pamięci do formatu XML  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania ułatwiają przekształcania danych między struktury danych w pamięci, baz danych, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawów danych i XML strumieni lub dokumenty. Poniższy przykład do elementów XML przy użyciu obiektów w strukturze danych w pamięci.  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 Kod tworzy następujące dane wyjściowe XML:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML w języku C# (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Wykonywanie operacji na elementach źródłowych  
 Sekwencja wyjścia nie może zawierać wszystkie elementy lub właściwości elementu w sekwencji źródłowej. Dane wyjściowe mogą być sekwencję wartości, która jest obliczana przy użyciu elementów źródła jako argumenty wejściowe. Następujące zapytanie proste, po jego wykonaniu danych wyjściowych sekwencję ciągów, którego wartości reprezentują obliczenia na podstawie sekwencji źródło elementów typu `double`.  
  
> [!NOTE]
>  Wywołanie metody w wyrażeniach zapytań nie jest obsługiwane, jeśli zapytanie zostanie zamieniona na innej domeny. Na przykład nie można wywołać zwykłej metody C# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ponieważ program SQL Server ma Brak kontekstu dla niego. Można jednak mapowanie procedur składowanych do metody i te wywołania. Aby uzyskać więcej informacji, zobacz [procedur składowanych](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
 [LINQ do XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [select, klauzula](../../../../csharp/language-reference/keywords/select-clause.md)
