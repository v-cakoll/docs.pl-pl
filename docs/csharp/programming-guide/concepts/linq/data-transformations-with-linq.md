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
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635954"
---
# <a name="data-transformations-with-linq-c"></a>Przekształcanie danych za pomocą LINQ (C#)
Zapytanie zintegrowane z językiem (LINQ) to nie tylko pobieranie danych. Jest to również potężne narzędzie do przekształcania danych. Za pomocą kwerendy LINQ, można użyć sekwencji źródłowej jako dane wejściowe i zmodyfikować go na wiele sposobów, aby utworzyć nową sekwencję danych wyjściowych. Można zmodyfikować samą sekwencję bez modyfikowania samych elementów, sortując i grupując. Ale być może najpotężniejszą cechą zapytań LINQ jest możliwość tworzenia nowych typów. Odbywa się to w [select](../../../language-reference/keywords/select-clause.md) klauzuli. Na przykład można wykonać następujące zadania:  
  
- Scalanie wielu sekwencji wejściowych w jedną sekwencję danych wyjściowych, która ma nowy typ.  
  
- Tworzenie sekwencji wyjściowych, których elementy składają się tylko z jednej lub kilku właściwości każdego elementu w sekwencji źródłowej.  
  
- Tworzenie sekwencji wyjściowych, których elementy składają się z wyników operacji wykonywanych na danych źródłowych.  
  
- Tworzenie sekwencji wyjściowych w innym formacie. Na przykład można przekształcić dane z wierszy SQL lub plików tekstowych w XML.  
  
 To tylko kilka przykładów. Oczywiście te przekształcenia mogą być łączone na różne sposoby w tej samej kwerendzie. Ponadto sekwencji wyjściowej jednej kwerendy może służyć jako sekwencji wejściowej dla nowej kwerendy.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Łączenie wielu danych wejściowych w jedną sekwencję wyjściową  
 Za pomocą kwerendy LINQ można utworzyć sekwencję danych wyjściowych, która zawiera elementy z więcej niż jednej sekwencji wejściowej. W poniższym przykładzie pokazano, jak połączyć dwie struktury danych w pamięci, ale te same zasady mogą być stosowane do łączenia danych ze źródeł XML lub SQL lub DataSet. Załóżmy, że następujące dwa typy klas:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 W poniższym przykładzie przedstawiono kwerendę:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Aby uzyskać więcej informacji, zobacz [join klauzuli](../../../language-reference/keywords/join-clause.md) i [wybierz klauzulę](../../../language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Wybranie podzestawu każdego elementu źródłowego  
 Istnieją dwa podstawowe sposoby wyboru podzbioru każdego elementu w sekwencji źródłowej:  
  
1. Aby wybrać tylko jeden element członkowski elementu źródłowego, należy użyć operacji kropka. W poniższym przykładzie załóżmy, że `Customer` obiekt zawiera `City`kilka właściwości publicznych, w tym ciąg o nazwie . Po wykonaniu ta kwerenda spowoduje wygenerowanie sekwencji wyjściowej ciągów.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Aby utworzyć elementy, które zawierają więcej niż jedną właściwość z elementu źródłowego, można użyć inicjatora obiektu z nazwanym obiektem lub typem anonimowym. W poniższym przykładzie przedstawiono użycie typu anonimowego do hermetyzacji dwóch właściwości z każdego `Customer` elementu:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](../../classes-and-structs/object-and-collection-initializers.md) oraz [typy anonimowe](../../classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Przekształcanie obiektów w pamięci do formatu XML  
 Kwerendy LINQ ułatwiają przekształcanie danych między strukturami danych w pamięci, bazami danych SQL, ADO.NET zestawami danych i strumieniami xml lub dokumentami. Poniższy przykład przekształca obiekty w strukturze danych w pamięci do elementów XML.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML w języku C# (LINQ do XML)](./creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Wykonywanie operacji na elementach źródłowych  
 Sekwencja danych wyjściowych może nie zawierać żadnych elementów lub właściwości elementu z sekwencji źródłowej. Dane wyjściowe mogą być zamiast tego sekwencji wartości, które są obliczane przy użyciu elementów źródłowych jako argumenty wejściowe. Następujące proste zapytanie, gdy jest wykonywana, generuje sekwencję ciągów, których wartości reprezentują `double`obliczenia oparte na sekwencji źródłowej elementów typu .  
  
> [!NOTE]
> Wywoływanie metod w wyrażeniach kwerendy nie jest obsługiwane, jeśli kwerenda zostanie przetłumaczona na inną domenę. Na przykład nie można wywołać zwykłej [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] metody Języka C#, ponieważ program SQL Server nie ma dla niej kontekstu. Można jednak mapować procedury przechowywane do metod i wywołać te. Aby uzyskać więcej informacji, zobacz [Procedury składowane](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Zobacz też

- [Zapytanie zintegrowane z językiem (LINQ) (C#)](./index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ do DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ do XML (C#)](./linq-to-xml-overview.md)
- [Wyrażenia zapytań LINQ](../../../linq/index.md)
- [klauzula wyboru](../../../language-reference/keywords/select-clause.md)
