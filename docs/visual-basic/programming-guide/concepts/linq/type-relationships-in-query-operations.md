---
title: Relacje typu w operacjach zapytań (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 14f17e89e2a4143580b4a2ca7f9d30013ded58f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053187"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacje typu w operacjach zapytań (Visual Basic)
Zmienne używane w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] zapytania operacje są silnie typizowane i muszą być zgodne ze sobą. Silne wpisywanie jest używany w źródle danych, samo zapytanie i wykonywania zapytań. Na poniższej ilustracji identyfikuje terminy używane do opisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Aby uzyskać więcej informacji na temat części zapytania zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Zrzut ekranu przedstawiający zapytania pseudokodzie z elementami wyróżnione.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 Rodzaj zmiennej zakresu w zapytaniu musi być zgodny z typem elementów w źródle danych. Typ zmiennej zapytania musi być zgodny z elementem sekwencji zdefiniowane w `Select` klauzuli. Wreszcie, typ elementów sekwencji również musi być zgodny z typem zmienna sterująca pętli, który jest używany w `For Each` instrukcję, która wykonuje zapytanie. To pogrubione wpisywanie ułatwia identyfikację błędów typu w czasie kompilacji.  
  
 Visual Basic sprawia, że silne wpisywanie wygodne implementując wnioskowanie o typie lokalnym, znany także jako *niejawnego wpisywania*. Czy funkcja jest używana w poprzednim przykładzie, a będzie ono używane w całym widoczne [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i dokumentację. W języku Visual Basic wnioskowanie o typie lokalnym odbywa się przy użyciu `Dim` instrukcję bez `As` klauzuli. W poniższym przykładzie `city` jest silnie typizowane jako ciąg.  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Wnioskowanie o typie lokalnym działa tylko wtedy, gdy `Option Infer` ustawiono `On`. Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Jednak nawet wtedy, gdy używasz wnioskowanie o typie lokalnym w zapytaniu tego samego relacje typów znajdują się między zmiennymi w źródle danych, zmienna zapytania i pętli wykonania zapytania. Warto mieć podstawową wiedzę na temat relacji tych typów, gdy tworzysz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania lub pracy z przykładami i przykłady kodu w dokumentacji.  
  
 Może być konieczne określenie jawnego typu zmiennej zakresu, który nie jest zgodny z typem zwracanym ze źródła danych. Rodzaj zmiennej zakresu można określić za pomocą `As` klauzuli. Jednak powoduje to błąd, jeśli konwersja jest [konwersja zawężająca](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i `Option Strict` ustawiono `On`. Dlatego zaleca się wykonania konwersji na wartościach pobranych ze źródła danych. Można przekonwertować wartości ze źródła danych do typu zmiennej zakresu jawne przy użyciu <xref:System.Linq.Enumerable.Cast%2A> metody. Można również rzutować wartości wybranych w `Select` klauzuli w celu jawnego typu, która różni się od typu zmiennej zakresu. Te punkty zostały zilustrowane w poniższym kodzie.  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Zapytania, które zwracają elementy całego źródła danych  
 W poniższym przykładzie przedstawiono [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania operacji, która zwraca sekwencję elementów wybranych z danymi źródłowymi. Źródło, `names`, zawiera tablicę ciągów i wynik zapytania jest sekwencja zawierających ciągi rozpoczynające się od litery M.  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 To jest odpowiednikiem następującego kodu, ale jest znacznie krótsze i łatwiejsze do zapisania. Poleganie na wnioskowanie o typie lokalnym w zapytaniach jest preferowany styl w języku Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 W obu poprzednich przykładach kodu istnieją następujące relacje, czy typy są określone jawnie lub niejawnie.  
  
1. Typ elementów w źródle danych `names`, to rodzaj zmiennej zakresu `name`, w zapytaniu.  
  
2. Typ obiektu, który jest wybrany, `name`, określa typ zmiennej zapytania `mNames`. W tym miejscu `name` jest ciągiem, dzięki czemu zmienna zapytania jest IEnumerable (Of String) w języku Visual Basic.  
  
3. Zapytanie zdefiniowane w `mNames` jest wykonywany w `For Each` pętli. Pętla wykonuje iterację na wynik wykonania zapytania. Ponieważ `mNames`, gdy jest ono wykonywane, zwróci sekwencją ciągów, zmienną iteracji pętli `nm`, również jest ciągiem.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Zapytania, które zwraca jedno pole z wybranych elementów  
 W poniższym przykładzie przedstawiono [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację, która zwraca sekwencję zawierającą tylko jednej części każdy element wybranych ze źródła danych zapytania. Zapytanie zabiera zbiór `Customer` obiektów jako źródło danych i wyłącznie dla projektów `Name` właściwości w wyniku. Ponieważ nazwa klienta jest ciągiem, zapytanie generuje sekwencji ciągów jako dane wyjściowe.  
  
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
  
 Relacje między zmienne są podobne do tych w przykładzie prostsze.  
  
1. Typ elementów w źródle danych `customers`, to rodzaj zmiennej zakresu `cust`, w zapytaniu. W tym przykładzie, który jest typem `Customer`.  
  
2. `Select` Instrukcja zwraca `Name` właściwości każdego `Customer` obiekt, a nie cały obiekt. Ponieważ `Name` jest ciągiem, zmienna zapytania `custNames`, ponownie IEnumerable (Of String), nie będzie z `Customer`.  
  
3. Ponieważ `custNames` reprezentuje sekwencję ciągów, `For Each` Zmienna iteracji pętli, `custName`, musi być ciągiem.  
  
 Bez wnioskowanie o typie lokalnym byłoby bardziej skomplikowane, zapisu i dowiedzieć się, jak w poniższym przykładzie przedstawiono poprzedniego przykładu.  
  
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
  
## <a name="queries-that-require-anonymous-types"></a>Zapytania, które wymagają typów anonimowych  
 Poniższy przykład przedstawia bardziej złożona sytuacja. W poprzednim przykładzie był wygodne, aby jawnie określić typy dla wszystkich zmiennych. W tym przykładzie jest niemożliwe. Zamiast zaznaczania całego `Customer` elementy ze źródła danych lub jedno pole z każdego elementu `Select` klauzuli w tym zapytaniu zwraca dwie właściwości oryginalny `Customer` obiektu: `Name` i `City`. W odpowiedzi na `Select` klauzuli, kompilator Określa typ anonimowy, który zawiera te dwie właściwości. Wynik wykonania `nameCityQuery` w `For Each` pętla jest kolekcją wystąpień nowym typem anonimowym. Ponieważ typ anonimowy nie ma użytecznych nazw, nie można określić typ `nameCityQuery` lub `custInfo` jawnie. Oznacza to, za pomocą typu anonimowego masz bez nazwy typu, aby użyć zamiast `String` w `IEnumerable(Of String)`. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
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
  
1. Typ elementów w źródle danych jest ponownie rodzaj zmiennej zakresu w zapytaniu. W tym przykładzie `cust` jest wystąpieniem `Customer`.  
  
2. Ponieważ `Select` instrukcja generuje typ anonimowy, zmienna zapytania `nameCityQuery`, musi być wpisana niejawnie jako typu anonimowego. Typ anonimowy nie ma użytecznych nazw i dlatego nie może być jawnie określone.  
  
3. Typ zmiennej iteracji w `For Each` pętla jest typu anonimowego, utworzony w kroku 2. Ponieważ typ nie ma użytecznych nazw, można niejawnie określić typu Zmienna iteracji pętli.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
