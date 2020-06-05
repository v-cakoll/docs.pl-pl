---
title: 'Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 9ebbbe9d2e6d36f5ab2bc7f7c916d18c9240a06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404891"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)

Typy anonimowe nie zapewniają mechanizmu bezpośredniego określania typów danych właściwości. Typy wszystkich właściwości są wywnioskowane. W poniższym przykładzie typy `Name` i `Price` są wywnioskowane bezpośrednio z wartości, które są używane do ich zainicjowania.

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

Typy anonimowe mogą również wywnioskować nazwy właściwości i typy z innych źródeł. Poniższe sekcje zawierają listę warunków, w których można wywnioskować, oraz przykłady sytuacji, w których nie jest.

## <a name="successful-inference"></a>Pomyślne wnioskowanie

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Typy anonimowe mogą wywnioskować nazwy właściwości i typy z następujących źródeł:

- Z nazw zmiennych. Typ anonimowy `anonProduct` ma dwie właściwości `productName` i `productPrice` . Ich typy danych będą tymi samymi oryginalnymi zmiennymi, `String` a `Double` odpowiednio.

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- Z nazw właściwości lub pól innych obiektów. Rozważmy na przykład `car` obiekt `CarClass` typu, który zawiera `Name` `ID` właściwości i. Aby utworzyć nowe wystąpienie typu anonimowego, `car1` z `Name` i `ID` właściwości, które są inicjowane za pomocą wartości z `car` obiektu, można napisać następujące elementy:

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  Poprzednia deklaracja jest równoznaczna z dłuższym wierszem kodu, który definiuje typ anonimowy `car2` .

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- Z nazw elementów członkowskich XML.

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  Typ otrzymany dla elementu `anon` zostałby mieć jedną właściwość, `Book` typu <xref:System.Collections.IEnumerable> (of XElement).

- Z funkcji, która nie ma parametrów, takich jak `SomeFunction` w poniższym przykładzie.

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  Zmienna `anon2` w poniższym kodzie jest typem anonimowym, który ma jedną właściwość, znak o nazwie `First` . Ten kod będzie wyświetlał literę "E", która jest zwracana przez funkcję <xref:System.Linq.Enumerable.First%2A> .

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a>Błędy wnioskowania

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Wnioskowanie o nazwach zakończy się niepowodzeniem w wielu sytuacjach, w tym:

- Wnioskowanie pochodzi z wywołania metody, konstruktora lub właściwości sparametryzowanej, która wymaga argumentów. Poprzednia Deklaracja elementu `anon1` kończy się niepowodzeniem, jeśli `someFunction` ma jeden lub więcej argumentów.

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  Przypisanie do nowej nazwy właściwości rozwiązuje problem.

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- Wnioskowanie pochodzi z wyrażenia złożonego.

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  Błąd można rozwiązać, przypisując wynik wyrażenia do nazwy właściwości.

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- Wnioskowanie dla wielu właściwości tworzy dwie lub więcej właściwości, które mają taką samą nazwę. Odwołując się do deklaracji we wcześniejszych przykładach, nie można wyświetlać jednocześnie `product.Name` i `car1.Name` jako właściwości tego samego typu anonimowego. Wynika to z faktu, że został wywnioskowany identyfikator dla każdego z nich `Name` .

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  Problem można rozwiązać, przypisując wartości do nazw odrębnych właściwości.

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  Należy pamiętać, że zmiany w wielkości liter (zmiany między dużymi i małymi literami) nie tworzą odrębnych nazw.

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- Typ początkowy i wartość jednej właściwości zależy od innej właściwości, która nie została jeszcze ustanowiona. Na przykład, `.IDName = .LastName` nie jest prawidłowy w deklaracji typu anonimowego, chyba że `.LastName` jest już zainicjowany.

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  W tym przykładzie można rozwiązać ten problem, odwracając kolejność, w której są zadeklarowane właściwości.

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- Nazwa właściwości typu anonimowego jest taka sama jak nazwa elementu członkowskiego <xref:System.Object> . Na przykład następująca deklaracja kończy się niepowodzeniem, ponieważ `Equals` jest metodą <xref:System.Object> .

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  Problem można rozwiązać, zmieniając nazwę właściwości:

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a>Zobacz też

- [Inicjatory obiektów: typy nazwane i anonimowe](object-initializers-named-and-anonymous-types.md)
- [Wnioskowanie o typie lokalnym](../variables/local-type-inference.md)
- [Typy anonimowe](anonymous-types.md)
- [Klucz](../../../language-reference/modifiers/key.md)
