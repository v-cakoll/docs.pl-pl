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
ms.openlocfilehash: f823d9e80eb644487eab1ed84345dd8bdc10efc2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600942"
---
# <a name="value-types-and-reference-types"></a>Typy wartości i odwołań
W języku Visual Basic typy danych są implementowane w na podstawie ich klasyfikacji. Typy danych Visual Basic mogą być klasyfikowane według tego, czy zmienna określonego typu przechowuje własnych danych lub wskaźnik do danych. Jeśli przechowuje swoje własne dane *typu wartości*; Jeśli przechowuje wskaźnik do danych w pamięci jest *odwołania do typu*.  
  
## <a name="value-types"></a>Typy wartości  
 Typ danych jest *typu wartości* Jeśli przechowuje dane w obrębie własnej alokacji pamięci. Typy wartości są następujące:  
  
- Wszystkie typy danych numerycznych  
  
- `Boolean`, `Char`, i `Date`  
  
- Wszystkie struktury, nawet jeśli ich elementy członkowskie są typami odwołań  
  
- Wyliczenia, ponieważ jego typ podstawowy jest zawsze `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, lub `ULong`  
  
 Co struktura jest typem wartości, nawet wtedy, gdy zawiera on elementy członkowskie typu odwołania. Z tego powodu wartość typy takie jak `Char` i `Integer` są implementowane przez struktury .NET Framework.  
  
 Typ wartości można zadeklarować za pomocą zastrzeżonego słowa kluczowego, na przykład `Decimal`. Można również użyć `New` — słowo kluczowe można zainicjować typu wartości. Jest to szczególnie przydatne, jeśli typ ma konstruktora przyjmującego parametry. Na przykład <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktora, który tworzy nową `Decimal` wartości z części podane.  
  
## <a name="reference-types"></a>Typy odwołań  
 A *odwołania do typu* zawiera wskaźnik do innej lokalizacji w pamięci, która przechowuje dane. Typy odwołań są następujące:  
  
- `String`  
  
- Wszystkie tablice, nawet jeśli ich elementy są typami wartości  
  
- Klasa typów, takich jak <xref:System.Windows.Forms.Form>  
  
- Delegaty  
  
 Klasa jest *odwołania do typu*. Z tego powodu typy odwołań takich jak `Object` i `String` są obsługiwane przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy. Należy pamiętać, że każda tablica typu odwołania, nawet jeśli jego członkowie są typami wartości.  
  
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
 Można przypisać do zmiennej typu odwołania lub typu wartościowego `Object` typu danych. `Object` Zawsze zmienna przechowuje wskaźnik do danych, nigdy nie dane. Jednak jeśli przypisujesz typ wartości do `Object` zmiennej działa tak, jakby posiada własnych danych. Aby uzyskać więcej informacji, zobacz [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Można dowiedzieć się, czy `Object` zmiennej działa jako typu odwołania lub typu wartościowego przez przekazanie jej do <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in Class metoda <xref:Microsoft.VisualBasic.Information> klasy <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Zwraca `True` Jeśli zawartość `Object` zmienna reprezentuje typ odwołania.  
  
## <a name="see-also"></a>Zobacz także

- [Typy wartości dopuszczających wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
