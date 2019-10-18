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
ms.openlocfilehash: 6d5d13064cceba10d27901ee95aa8b6731620dbb
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524112"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacje typu w operacjach zapytań (Visual Basic)

Zmienne używane w operacjach zapytania [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] są silnie wpisane i muszą być zgodne ze sobą. W źródle danych jest używane silne wpisywanie, w samej kwerendzie i w wykonaniu zapytania. Na poniższej ilustracji przedstawiono terminy używane do opisywania zapytania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Aby uzyskać więcej informacji na temat części zapytania, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).

![Zrzut ekranu przedstawiający zapytanie pseudokodzie z wyróżnionymi elementami.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Typ zmiennej zakresu w zapytaniu musi być zgodny z typem elementów w źródle danych. Typ zmiennej zapytania musi być zgodny z elementem sekwencji zdefiniowanym w klauzuli `Select`. Na koniec typ elementów sekwencji musi być zgodny z typem zmiennej sterującej pętli, która jest używana w instrukcji `For Each`, która wykonuje zapytanie. To silne pisanie ułatwia identyfikację błędów typu w czasie kompilacji.

Visual Basic sprawia, że silne wpisywanie jest wygodne przez implementację lokalnego wnioskowania o typie, znanego również jako *niejawne wpisywanie*. Ta funkcja jest używana w poprzednim przykładzie i zostanie wyświetlona w całym [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i dokumentacja. W Visual Basic, wnioskowanie typu lokalnego jest wykonywane po prostu przy użyciu instrukcji `Dim` bez klauzuli `As`. W poniższym przykładzie `city` jest silnie wpisana jako ciąg.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> Wnioskowanie o typie lokalnym działa tylko wtedy, gdy `Option Infer` jest ustawiony na `On`. Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../../visual-basic/language-reference/statements/option-infer-statement.md).

Jednak nawet jeśli używasz wnioskowania typu lokalnego w zapytaniu, te same relacje typu są obecne między zmiennymi w źródle danych, zmienną zapytania i pętlą wykonywania zapytania. Warto zapoznać się z podstawowymi informacjami o tych relacjach typu podczas pisania zapytań [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] lub pracy z przykładami i przykłady kodu w dokumentacji.

Może być konieczne określenie typu jawnego dla zmiennej zakresu, która nie jest zgodna z typem zwracanym ze źródła danych. Możesz określić typ zmiennej zakresu przy użyciu klauzuli `As`. Powoduje to jednak błąd, jeśli konwersja jest [konwersją zawężania](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) , a `Option Strict` jest ustawiona na `On`. Dlatego zalecamy przeprowadzenie konwersji na wartości pobrane ze źródła danych. Możesz przekonwertować wartości ze źródła danych na jawny typ zmiennej zakresu przy użyciu metody <xref:System.Linq.Enumerable.Cast%2A>. Możesz również rzutować wartości wybrane w klauzuli `Select` na jawny typ, który jest inny niż typ zmiennej zakresu. Te punkty są zilustrowane w poniższym kodzie.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Zapytania, które zwracają wszystkie elementy danych źródłowych

Poniższy przykład pokazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operacji zapytania, która zwraca sekwencję elementów wybranych z danych źródłowych. Źródło, `names`, zawiera tablicę ciągów, a dane wyjściowe zapytania są sekwencją zawierającą ciągi, które zaczynają się literą M.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

Jest to odpowiednik poniższego kodu, ale jest znacznie krótszy i łatwiejszy do zapisu. Zależność od lokalnego wnioskowania typu w zapytaniach jest preferowanym stylem w Visual Basic.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Poniższe relacje istnieją w obu powyższych przykładach kodu, niezależnie od tego, czy typy są określane niejawnie czy jawnie.

1. Typ elementów w źródle danych `names`, jest typem zmiennej zakresu, `name` w zapytaniu.

2. Typ obiektu, który jest zaznaczony, `name` określa typ zmiennej zapytania, `mNames`. W tym miejscu `name` jest ciągiem, więc zmienna zapytania to IEnumerable (Of String) w Visual Basic.

3. Zapytanie zdefiniowane w `mNames` jest wykonywane w pętli `For Each`. Pętla wykonuje iterację w wyniku wykonywania zapytania. Ponieważ `mNames`, gdy jest wykonywane, zwróci sekwencję ciągów, Zmienna iteracji pętli, `nm`, również jest ciągiem.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Zapytania zwracające jedno pole z wybranych elementów

Poniższy przykład pokazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operacji zapytania, która zwraca sekwencję zawierającą tylko jedną część każdego elementu wybranego ze źródła danych. Zapytanie pobiera kolekcję `Customer` obiektów jako źródła danych i projektuje tylko Właściwość `Name` w wyniku. Ponieważ nazwa klienta jest ciągiem, zapytanie tworzy sekwencję ciągów jako dane wyjściowe.

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

1. Typ elementów w źródle danych `customers`, jest typem zmiennej zakresu, `cust` w zapytaniu. W tym przykładzie ten typ jest `Customer`.

2. Instrukcja `Select` zwraca właściwość `Name` każdego obiektu `Customer` zamiast całego obiektu. Ponieważ `Name` jest ciągiem, zmienna zapytania, `custNames`, ponownie będzie IEnumerable (Of String), a nie `Customer`.

3. Ponieważ `custNames` reprezentuje sekwencję ciągów, Zmienna iteracji pętli `For Each`, `custName`, musi być ciągiem.

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

Poniższy przykład przedstawia bardziej skomplikowaną sytuację. W poprzednim przykładzie było to wygodne do określenia typów dla wszystkich zmiennych jawnie. W tym przykładzie jest to niemożliwe. Zamiast wybierać całe `Customer` elementy ze źródła danych lub pojedyncze pole z każdego elementu, klauzula `Select` w tym zapytaniu zwraca dwie właściwości oryginalnego obiektu `Customer`: `Name` i `City`. W odpowiedzi na klauzulę `Select`, kompilator definiuje typ anonimowy, który zawiera te dwie właściwości. Wynikiem wykonywania `nameCityQuery` w pętli `For Each` jest kolekcja wystąpień nowego typu anonimowego. Ponieważ typ anonimowy nie ma użytecznych nazw, nie można jawnie określić typu `nameCityQuery` lub `custInfo`. Oznacza to, że z typem anonimowym nie ma nazwy typu do użycia zamiast `String` w `IEnumerable(Of String)`. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

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

1. Typ elementów w źródle danych jest ponownie typem zmiennej zakresu w zapytaniu. W tym przykładzie `cust` jest wystąpieniem `Customer`.

2. Ponieważ instrukcja `Select` generuje typ anonimowy, zmienna zapytania, `nameCityQuery`, musi być jawnie wpisana jako typ anonimowy. Typ anonimowy nie ma użytecznych nazw i dlatego nie może być określony jawnie.

3. Typ zmiennej iteracji w pętli `For Each` jest typem anonimowym utworzonym w kroku 2. Ponieważ typ nie ma użytecznych nazw, typ zmiennej iteracji pętli musi być określony niejawnie.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie ze składnikami LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
