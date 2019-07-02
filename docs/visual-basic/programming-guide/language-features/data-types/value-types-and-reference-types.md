---
title: Typy wartości i odwołań
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: f25caec43b7118b7b64db1b14516b0c5ea80f4f6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504878"
---
# <a name="value-types-and-reference-types"></a>Typy wartości i odwołań
Istnieją dwa rodzaje typów w języku Visual Basic: typy referencyjne i typy wartości. W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane. W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna. Z typami wartości każda zmienna ma własną kopię danych i nie jest możliwe dla operacji na jednej zmiennej miały wpływ na inne (z wyjątkiem w przypadku właściwości [ByRef modyfikator parametrów](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Typy wartości  
 Typ danych jest *typu wartości* Jeśli przechowuje dane w obrębie własnej alokacji pamięci. Typy wartości są następujące:  
  
- Wszystkie typy danych numerycznych  
  
- `Boolean`, `Char`, i `Date`  
  
- Wszystkie struktury, nawet jeśli ich elementy członkowskie są typami odwołań  
  
- Wyliczenia, ponieważ jego typ podstawowy jest zawsze `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, lub `ULong`  
  
 Co struktura jest typem wartości, nawet wtedy, gdy zawiera on elementy członkowskie typu odwołania. Z tego powodu wartość typy takie jak `Char` i `Integer` są implementowane przez struktury .NET Framework.  
  
 Typ wartości można zadeklarować za pomocą zastrzeżonego słowa kluczowego, na przykład `Decimal`. Można również użyć `New` — słowo kluczowe można zainicjować typu wartości. Jest to szczególnie przydatne, jeśli typ ma konstruktora przyjmującego parametry. Na przykład <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktora, który tworzy nową `Decimal` wartości z części podane.  
  
## <a name="reference-types"></a>Typy odwołań  
 A *odwołania do typu* przechowuje odwołania do jego danych. Typy odwołań są następujące:  
  
- `String`  
  
- Wszystkie tablice, nawet jeśli ich elementy są typami wartości  
  
- Klasa typów, takich jak <xref:System.Windows.Forms.Form>  
  
- Delegaty  
  
 Klasa jest *odwołania do typu*. Należy pamiętać, że każda tablica typu odwołania, nawet jeśli jego członkowie są typami wartości.  
  
 Ponieważ każdy typ odniesienia reprezentuje podstawowej klasy .NET Framework, należy użyć [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe, podczas jego inicjowania. Poniższa instrukcja inicjuje tablicę.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementy, które nie są typami  
 Następujące elementy programowania nie kwalifikują się jako typów, ponieważ nie można określić dowolny z nich jako element zadeklarowany typ danych:  
  
- Namespaces  
  
- Moduły  
  
- Zdarzenia  
  
- Właściwości i procedury  
  
- Zmienne, stałe i pola  
  
## <a name="working-with-the-object-data-type"></a>Praca z typem danych obiektu  
 Można przypisać do zmiennej typu odwołania lub typu wartościowego `Object` typu danych. `Object` Zmiennej zawsze zawiera odwołanie do danych, nigdy nie dane. Jednak jeśli przypisujesz typ wartości do `Object` zmiennej działa tak, jakby posiada własnych danych. Aby uzyskać więcej informacji, zobacz [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Można dowiedzieć się, czy `Object` zmiennej działa jako typu odwołania lub typu wartościowego przez przekazanie jej do <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in Class metoda <xref:Microsoft.VisualBasic.Information> klasy <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Zwraca `True` Jeśli zawartość `Object` zmienna reprezentuje typ odwołania.  
  
## <a name="see-also"></a>Zobacz także

- [Typy wartości dopuszczających wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
