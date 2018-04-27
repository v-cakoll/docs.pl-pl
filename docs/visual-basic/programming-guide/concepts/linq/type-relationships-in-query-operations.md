---
title: Relacje typu w operacjach zapytań (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
caps.latest.revision: 34
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e38f51d77869dcca8a81fdcbc70aed32c4146935
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacje typu w operacjach zapytań (Visual Basic)
Zmienne używane w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] zapytania operacje są silnie typizowane i muszą być zgodne ze sobą. Silne wpisywanie jest używany w źródle danych, samą kwerendę i do wykonywania zapytania. Poniższa ilustracja identyfikuje terminów używanych w celu opisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Aby uzyskać więcej informacji na temat części zapytania, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Zapytanie pseudocode z wyróżnionym elementów. ] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
Części zapytania LINQ  
  
 Typ zmiennej zakresu w zapytaniu musi być zgodny z typem elementów w źródle danych. Typu zmienną zapytania musi być zgodny z elementem sekwencji zdefiniowane w `Select` klauzuli. Na koniec typ elementów sekwencji również musi być zgodny z typem zmienna sterująca pętli, który jest używany w `For Each` instrukcji, która wykonuje zapytania. Silne wpisywanie ułatwia identyfikację typu błędy w czasie kompilacji.  
  
 Visual Basic powoduje, że silne wpisywanie wygodne zaimplementowanie wnioskowanie o typie lokalnym, znanej także jako *niejawne wpisując*. Funkcja jest używana w poprzednim przykładzie, czy pojawi się on w całym [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i dokumentacja. W języku Visual Basic wnioskowanie o typie lokalnym odbywa się przy użyciu `Dim` instrukcję bez `As` klauzuli. W poniższym przykładzie `city` jest silnie typizowane jako ciąg.  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  Wnioskowanie o typie lokalnym działa tylko wtedy, gdy `Option Infer` ma ustawioną wartość `On`. Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Jednak nawet wtedy, gdy używasz wnioskowanie o typie lokalnym w zapytaniu tego samego typu relacji znajdują się między zmiennych w źródle danych, do zmiennej zapytania i pętlę wykonania zapytania. Warto mieć podstawową wiedzę na temat tych relacji typu podczas pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania lub Praca z przykładów i przykładów kodu w dokumentacji.  
  
 Może być konieczne określenie jawnego typu dla zmiennej zakresu, który jest niezgodny z typem zwracanym ze źródła danych. Typ zmiennej zakresu można określić za pomocą `As` klauzuli. Jednak to powoduje wystąpienie błędu w przypadku konwersji [konwersja zawężająca](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i `Option Strict` ma ustawioną wartość `On`. Dlatego zaleca się dokonać konwersji wartości pobrane ze źródła danych. Można przekonwertować wartości ze źródła danych na typ zmiennej jawnej zakresu przy użyciu <xref:System.Linq.Enumerable.Cast%2A> metody. Można również rzutowania wartości wybrane w `Select` klauzulę jawnego typu, który różni się od typu zmiennej zakresu. Punkty te zostały przedstawione w poniższym kodzie.  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Zapytań zwracających elementy całego źródła danych  
 W poniższym przykładzie przedstawiono [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację, która zwraca sekwencję elementów wybrane źródła danych z zapytania. Źródło, `names`, zawiera tablicę ciągów, i wyników zapytania jest sekwencją zawierającego ciągi rozpoczynające się od litery M.  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 To jest odpowiednikiem następujący kod, ale jest znacznie krótsze i łatwiejsze do zapisu. Zależność od wnioskowanie o typie lokalnym w zapytaniach jest preferowanym stylu w języku Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 Następujące relacje istnieje zarówno w poprzednich przykładach kodu, czy typy są określone jawnie lub niejawnie.  
  
1.  Typ elementów w źródle danych `names`, jest typu zmienną zakresu `name`, w zapytaniu.  
  
2.  Typ obiektu, który jest zaznaczone, `name`, określa typu zmienną zapytania `mNames`. W tym miejscu `name` jest ciągu, więc do zmiennej zapytania jest IEnumerable (Of String) w języku Visual Basic.  
  
3.  Zapytanie określone w `mNames` są wykonywane w `For Each` pętli. Pętla wykonuje iterację na wynik wykonania zapytania. Ponieważ `mNames`po wykonaniu, będzie zwracać sekwencję ciągów, Zmienna iteracji pętli, `nm`, również jest ciągiem.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Zapytań zwracających jedno pole z wybranych elementów  
 W poniższym przykładzie przedstawiono [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zapytania operację, która zwraca sekwencji zawierających tylko jedną część każdego elementu wybrane źródło danych. Zapytanie pobiera zbiór `Customer` obiekty jako źródło danych i tylko projekty `Name` właściwości w wyniku. Ponieważ nazwy klienta jest ciągiem, zapytanie tworzy sekwencję ciągi jako dane wyjściowe.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 Relacje zmienne są podobnie jak w przykładzie prostsze.  
  
1.  Typ elementów w źródle danych `customers`, jest typu zmienną zakresu `cust`, w zapytaniu. W tym przykładzie, który jest typu `Customer`.  
  
2.  `Select` Zwraca instrukcji `Name` właściwości każdego `Customer` obiektu, a nie całym obiektem. Ponieważ `Name` to ciąg do zmiennej zapytania `custNames`, ponownie IEnumerable (Of String), nie będzie z `Customer`.  
  
3.  Ponieważ `custNames` reprezentuje sekwencję ciągów, `For Each` zmiennej iteracji pętli, `custName`, musi być ciągiem.  
  
 Bez wnioskowanie o typie lokalnym poprzedni przykład będzie bardziej skomplikowane, zapisu i zrozumieć, jak przedstawiono na poniższym przykładzie.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>Zapytania wymagające typy anonimowe  
 W poniższym przykładzie przedstawiono bardziej złożonych sytuacji. W poprzednim przykładzie został niewygodne jawnie określić typy dla wszystkich zmiennych. W tym przykładzie jest niemożliwe. Zamiast zaznaczania całego `Customer` elementy ze źródła danych lub pojedyncze pole z każdego elementu `Select` klauzula w tym zapytaniu zwraca dwie właściwości oryginalnej `Customer` obiekt: `Name` i `City`. W odpowiedzi na `Select` klauzuli, kompilator definiuje typ anonimowy, który zawiera te dwie właściwości. Wynik wykonania `nameCityQuery` w `For Each` pętla jest kolekcja wystąpień nowego typu anonimowego. Ponieważ typ anonimowy nie ma używać nazwy, nie można określić typu `nameCityQuery` lub `custInfo` jawnie. Oznacza to, z typu anonimowego, możesz nie mieć typ nazwy do użycia zamiast `String` w `IEnumerable(Of String)`. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 Chociaż nie jest możliwe określenie typów dla wszystkich zmiennych w poprzednim przykładzie, relacje pozostają takie same.  
  
1.  Typ elementów w źródle danych, jest ponownie typu zmienną zakresu w zapytaniu. W tym przykładzie `cust` jest wystąpieniem `Customer`.  
  
2.  Ponieważ `Select` instrukcji tworzy typu anonimowego zmienną zapytania `nameCityQuery`, musi być niejawnie typizowana jako typu anonimowego. Typ anonimowy nie ma używać nazwy i dlatego nie może być określona jawnie.  
  
3.  Typ zmiennej iteracji w `For Each` pętla jest typu anonimowego utworzony w kroku 2. Ponieważ typ nie ma używać nazwy, można niejawnie ustalić typu zmiennej iteracji pętli.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)
