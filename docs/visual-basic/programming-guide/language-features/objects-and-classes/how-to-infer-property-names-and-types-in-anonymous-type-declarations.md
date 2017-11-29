---
title: "Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 66b9f8c0346f74ff631969bda122de7913a551c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)
Typy anonimowe nie zawierają mechanizmu bezpośrednio określająca typy danych właściwości. Typy wszystkich właściwości są wywnioskować. W poniższym przykładzie typy `Name` i `Price` są wywnioskować bezpośrednio z wartości, które są używane do ich inicjowania.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 Typy anonimowe można również wnioskowanie nazw właściwości i typów z innych źródeł. W kolejnych sekcjach zawierają listę okoliczności, w którym możliwe jest wnioskowania i przykłady sytuacji, gdy nie jest.  
  
## <a name="successful-inference"></a>Pomyślne wnioskowania  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Typy anonimowe można wnioskowanie nazw właściwości i typów z następujących źródeł:  
  
-   Z nazwy zmiennej. Typ anonimowy `anonProduct` będzie mieć dwie właściwości `productName` i `productPrice`. Typy danych będą te oryginalnego zmiennych `String` i `Double`odpowiednio.  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   Właściwość lub pole nazw innych obiektów. Rozważmy na przykład `car` obiektu `CarClass` typ zawierający `Name` i `ID` właściwości. Aby utworzyć nowe wystąpienie typu anonimowego, `car1`, z `Name` i `ID` właściwości, które są inicjowane z wartościami z `car` obiektu, można wpisać następujące:  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     Poprzednia deklaracja jest odpowiednikiem dłużej wiersz kodu, który definiuje typ anonimowy `car2`.  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   Od nazw elementów członkowskich XML.  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     Wynikowy typ dla `anon` byłyby jedną właściwość `Book`, typu <xref:System.Collections.IEnumerable>(z klasy XElement).  
  
-   Z funkcji, która nie ma parametrów, takich jak `SomeFunction` w poniższym przykładzie.  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     Zmienna `anon2` w poniższym kodzie jest typu anonimowego, który ma właściwość jeden znak o nazwie `First`. Ten kod będzie wyświetlana litery "E","literą, która jest zwracana przez funkcję <xref:System.Linq.Enumerable.First%2A>.  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a>Błędy wnioskowania  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Wnioskowanie nazw zakończy się niepowodzeniem w wielu sytuacjach, w tym następujące:  
  
-   Wnioskowanie pochodzi z wywołania metody, konstruktora lub sparametryzowane, który wymaga argumentów. Z poprzednią deklaracją elementu `anon1` zakończy się niepowodzeniem, jeśli `someFunction` ma co najmniej jeden argument.  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     Przypisanie na nową nazwę właściwości rozwiązuje problem.  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   Wnioskowanie pochodzi z wyrażenia złożone.  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     Ten błąd można rozwiązać, przypisując wynik wyrażenia do nazwy właściwości.  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   Wnioskowanie dla wielu właściwości tworzy dwa lub więcej właściwości, które mają taką samą nazwę. Przywołuje deklaracje w przykładach wcześniej, nie możesz wystawiać zarówno `product.Name` i `car1.Name` jako właściwości tego samego typu anonimowego. Wynika to z faktu wnioskowany identyfikator dla każdego z nich będzie `Name`.  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     Problem można rozwiązać przez przypisywanie wartości do właściwości unikatowe nazwy.  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     Należy pamiętać, że zmiany w przypadku (zmiany między wielkie i małe litery) nie należy wprowadzać dwie nazwy distinct.  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   Początkowa typu i wartości jedną właściwość zależy od innej właściwości, która nie jest jeszcze ustalony. Na przykład `.IDName = .LastName` nie jest prawidłowy w deklaracji typu anonimowego, chyba że `.LastName` jest już zainicjowany.  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     W tym przykładzie można naprawić ten problem, odwracanie kolejności, w którym są zadeklarowane właściwości.  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   Nazwa właściwości typu anonimowego jest taka sama jak nazwa elementu członkowskiego <xref:System.Object>. Na przykład następujące oświadczenie nie powiedzie się, ponieważ `Equals` jest metoda <xref:System.Object>.  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     Aby rozwiązać ten problem, należy zmienić nazwę właściwości:  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjatory obiektów: Typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Klucz](../../../../visual-basic/language-reference/modifiers/key.md)
