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
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582646"
---
# <a name="value-types-and-reference-types"></a>Typy wartości i odwołań
Istnieją dwa rodzaje typów w Visual Basic: typy referencyjne i typy wartości. W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane. W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna. W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem przypadków [modyfikatora ByRef w przypadku parametrów](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Typy wartości  
 Typ danych jest *typem wartości* , jeśli przechowuje dane w ramach alokacji pamięci. Dostępne są następujące typy wartości:  
  
- Wszystkie typy danych liczbowych  
  
- `Boolean`, `Char` i `Date`  
  
- Wszystkie struktury, nawet jeśli ich składowe są typami odwołań  
  
- Wyliczenia, ponieważ ich typ podstawowy jest zawsze `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` lub `ULong`  
  
 Każda struktura jest typem wartości, nawet jeśli zawiera elementy członkowskie typu referencyjnego. Z tego powodu typy wartości, takie jak `Char` i `Integer`, są implementowane przez .NET Framework struktur.  
  
 Typ wartości można zadeklarować przy użyciu zastrzeżonego słowa kluczowego, na przykład `Decimal`. Możesz również użyć słowa kluczowego `New`, aby zainicjować typ wartości. Jest to szczególnie przydatne, jeśli typ ma konstruktora, który pobiera parametry. Przykładem jest Konstruktor <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>, który kompiluje nową wartość `Decimal` z dostarczonych części.  
  
## <a name="reference-types"></a>Typy odwołań  
 *Typ referencyjny* przechowuje odwołanie do swoich danych. Typy odwołań obejmują następujące elementy:  
  
- `String`  
  
- Wszystkie tablice, nawet jeśli ich elementy są typami wartości  
  
- Typy klas, takie jak <xref:System.Windows.Forms.Form>  
  
- Delegaty  
  
 Klasa jest *typem referencyjnym*. Należy zauważyć, że każda tablica jest typem referencyjnym, nawet jeśli jego elementy członkowskie są typami wartości.  
  
 Ponieważ każdy typ referencyjny reprezentuje bazową klasę .NET Framework, należy użyć słowa kluczowego [New](../../../../visual-basic/language-reference/operators/new-operator.md) podczas inicjowania. Poniższa instrukcja Inicjuje tablicę.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementy, które nie są typami  
 Następujące elementy programistyczne nie kwalifikują się jako typy, ponieważ nie można określić żadnego z nich jako typu danych dla zadeklarowanego elementu:  
  
- Namespaces  
  
- Moduły  
  
- Zdarzenia  
  
- Właściwości i procedury  
  
- Zmienne, stałe i pola  
  
## <a name="working-with-the-object-data-type"></a>Praca z typem danych obiektu  
 Do zmiennej typu danych `Object` można przypisać typ referencyjny lub typ wartości. Zmienna `Object` zawsze przechowuje odwołanie do danych, nigdy nie same same dane. Jeśli jednak przypiszesz typ wartości do zmiennej `Object`, zachowuje się tak, jakby przechowywać własne dane. Aby uzyskać więcej informacji, zobacz [Typ danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Można dowiedzieć się, czy zmienna `Object` działa jako typ referencyjny czy typ wartości poprzez przekazanie go do metody <xref:Microsoft.VisualBasic.Information.IsReference%2A> w klasie <xref:Microsoft.VisualBasic.Information> <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> zwraca `True`, jeśli zawartość zmiennej `Object` reprezentuje typ referencyjny.  
  
## <a name="see-also"></a>Zobacz także

- [Typy wartości dopuszczających wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
