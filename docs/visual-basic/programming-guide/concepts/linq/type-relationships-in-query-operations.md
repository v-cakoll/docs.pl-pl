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
ms.openlocfilehash: 4851d0a74de38f0fb6b6deee34cf7b3e66eb11b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937479"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacje typu w operacjach zapytań (Visual Basic)
Zmienne używane w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] operacjach zapytania są silnie wpisywane i muszą być zgodne ze sobą. W źródle danych jest używane silne wpisywanie, w samej kwerendzie i w wykonaniu zapytania. Na poniższej ilustracji przedstawiono terminy używane do opisywania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Aby uzyskać więcej informacji na temat części zapytania, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Zrzut ekranu przedstawiający zapytanie pseudokodzie z wyróżnionymi elementami.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 Typ zmiennej zakresu w zapytaniu musi być zgodny z typem elementów w źródle danych. Typ zmiennej zapytania musi być zgodny z elementem sekwencji zdefiniowanym w `Select` klauzuli. Na koniec typ elementów sekwencji musi być zgodny z typem zmiennej sterującej pętli, która jest używana w `For Each` instrukcji, która wykonuje zapytanie. To silne pisanie ułatwia identyfikację błędów typu w czasie kompilacji.  
  
 Visual Basic sprawia, że silne wpisywanie jest wygodne przez implementację lokalnego wnioskowaniao typie, znanego również jako niejawne wpisywanie. Ta funkcja jest używana w poprzednim przykładzie i zostanie wyświetlona w całej [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] próbce i dokumentacji. W Visual Basic, wnioskowanie o typie lokalnym jest wykonywane po prostu przy użyciu `Dim` instrukcji `As` bez klauzuli. W poniższym przykładzie `city` jest silnie wpisana jako ciąg.  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
> Wnioskowanie o typie lokalnym działa tylko `Option Infer` wtedy, gdy `On`jest ustawione na. Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Jednak nawet jeśli używasz wnioskowania typu lokalnego w zapytaniu, te same relacje typu są obecne między zmiennymi w źródle danych, zmienną zapytania i pętlą wykonywania zapytania. Warto zapoznać się z podstawowymi informacjami o tych relacjach typu podczas pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań lub pracy z przykładami i przykłady kodu w dokumentacji.  
  
 Może być konieczne określenie typu jawnego dla zmiennej zakresu, która nie jest zgodna z typem zwracanym ze źródła danych. Możesz określić typ zmiennej zakresu przy użyciu `As` klauzuli. Jednak spowoduje to błąd, jeśli konwersja jest konwersją `Option Strict` zawężania i jest ustawiona na. [](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) `On` Dlatego zalecamy przeprowadzenie konwersji na wartości pobrane ze źródła danych. Możesz przekonwertować wartości ze źródła danych na jawny typ zmiennej zakresu przy użyciu <xref:System.Linq.Enumerable.Cast%2A> metody. Możesz również rzutować wartości wybrane w `Select` klauzuli na jawny typ, który jest inny niż typ zmiennej zakresu. Te punkty są zilustrowane w poniższym kodzie.  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Zapytania, które zwracają wszystkie elementy danych źródłowych  
 Poniższy przykład pokazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację zapytania, która zwraca sekwencję elementów wybranych z danych źródłowych. Źródło, `names`,, zawiera tablicę ciągów, a dane wyjściowe zapytania są sekwencją zawierającą ciągi, które zaczynają się literą M.  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 Jest to odpowiednik poniższego kodu, ale jest znacznie krótszy i łatwiejszy do zapisu. Zależność od lokalnego wnioskowania typu w zapytaniach jest preferowanym stylem w Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 Poniższe relacje istnieją w obu powyższych przykładach kodu, niezależnie od tego, czy typy są określane niejawnie czy jawnie.  
  
1. Typ elementów w źródle `names`danych, jest typem `name`zmiennej zakresu w zapytaniu.  
  
2. Typ wybranego `name`obiektu,, określa typ zmiennej zapytania, `mNames`. Oto `name` ciąg, więc zmienna zapytania to IEnumerable (Of String) w Visual Basic.  
  
3. Zapytanie zdefiniowane w `mNames` elemencie jest wykonywane `For Each` w pętli. Pętla wykonuje iterację w wyniku wykonywania zapytania. Ponieważ `mNames`, gdy jest wykonywany, zwróci sekwencję ciągów, `nm`Zmienna iteracji pętli, również jest ciągiem.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Zapytania zwracające jedno pole z wybranych elementów  
 Poniższy przykład pokazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację zapytania, która zwraca sekwencję zawierającą tylko jedną część każdego elementu wybranego ze źródła danych. Zapytanie pobiera kolekcję `Customer` obiektów jako źródło danych i projektuje `Name` tylko właściwość w wyniku. Ponieważ nazwa klienta jest ciągiem, zapytanie tworzy sekwencję ciągów jako dane wyjściowe.  
  
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
  
 Relacje między zmiennymi są podobne do tych w prostszym przykładzie.  
  
1. Typ elementów w źródle `customers`danych, jest typem `cust`zmiennej zakresu w zapytaniu. Ten typ jest `Customer`w tym przykładzie.  
  
2. Instrukcja zwraca właściwość każdego`Customer` obiektu, a nie cały obiekt. `Name` `Select` Ponieważ `Name` jest ciągiem, `custNames`zmienna zapytania, ponownie będzie IEnumerable (of `Customer`String), a nie.  
  
3. Ponieważ `custNames` reprezentuje sekwencję ciągów `For Each` , zmienna `custName`iteracji pętli, musi być ciągiem.  
  
 Bez wnioskowania o typie lokalnym poprzedni przykład będzie bardziej skomplikowany do pisania i zrozumienia, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy przykład przedstawia bardziej skomplikowaną sytuację. W poprzednim przykładzie było to wygodne do określenia typów dla wszystkich zmiennych jawnie. W tym przykładzie jest to niemożliwe. Zamiast `Customer` wybierać całe elementy ze źródła danych lub pojedyncze pole z każdego elementu `Customer` `Select` , klauzula w tej kwerendzie zwraca dwie właściwości oryginalnego obiektu: `Name` i `City`. W odpowiedzi na `Select` klauzulę, kompilator definiuje typ anonimowy, który zawiera te dwie właściwości. Wynikiem wykonywania `nameCityQuery` `For Each` w pętli jest kolekcja wystąpień nowego typu anonimowego. Ponieważ typ anonimowy nie ma użytecznych nazw, nie można określić typu `nameCityQuery` ani `custInfo` jawnie. Oznacza to, że z typem anonimowym nie ma nazwy typu do użycia `String` zamiast w. `IEnumerable(Of String)` Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
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
  
1. Typ elementów w źródle danych jest ponownie typem zmiennej zakresu w zapytaniu. W tym przykładzie `cust` jest `Customer`wystąpieniem.  
  
2. Ponieważ instrukcja generuje typ anonimowy, zmienna zapytania, `nameCityQuery`musi być jawnie wpisana jako typ anonimowy. `Select` Typ anonimowy nie ma użytecznych nazw i dlatego nie może być określony jawnie.  
  
3. Typ zmiennej iteracji w `For Each` pętli jest typu anonimowego utworzonego w kroku 2. Ponieważ typ nie ma użytecznych nazw, typ zmiennej iteracji pętli musi być określony niejawnie.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie ze składnikami LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
