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
ms.openlocfilehash: 3a1de120f5f97ba93939f332f121d70cd3091216
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392977"
---
# <a name="value-types-and-reference-types"></a>Typy wartości i odwołań
Istnieją dwa rodzaje typów w Visual Basic: typy referencyjne i typy wartości. W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane. W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna. W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem przypadków [modyfikatora ByRef w przypadku parametrów](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Typy wartości  
 Typ danych jest *typem wartości* , jeśli przechowuje dane w ramach alokacji pamięci. Dostępne są następujące typy wartości:  
  
- Wszystkie typy danych liczbowych  
  
- `Boolean`, `Char` i`Date`  
  
- Wszystkie struktury, nawet jeśli ich składowe są typami odwołań  
  
- Wyliczenia, ponieważ ich typ podstawowy ma zawsze,,,,,, `SByte` `Short` `Integer` `Long` `Byte` `UShort` `UInteger` , lub`ULong`  
  
 Każda struktura jest typem wartości, nawet jeśli zawiera elementy członkowskie typu referencyjnego. Z tego powodu typy wartości, takie jak `Char` i, `Integer` są implementowane przez struktury .NET Framework.  
  
 Typ wartości można zadeklarować przy użyciu zastrzeżonego słowa kluczowego, na przykład `Decimal` . Możesz również użyć `New` słowa kluczowego, aby zainicjować typ wartości. Jest to szczególnie przydatne, jeśli typ ma konstruktora, który pobiera parametry. Przykładem jest <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> Konstruktor, który kompiluje nową `Decimal` wartość z dostarczonych części.  
  
## <a name="reference-types"></a>Typy odwołań  
 *Typ referencyjny* przechowuje odwołanie do swoich danych. Typy odwołań obejmują następujące elementy:  
  
- `String`  
  
- Wszystkie tablice, nawet jeśli ich elementy są typami wartości  
  
- Typy klas, takie jak<xref:System.Windows.Forms.Form>  
  
- Delegaci  
  
 Klasa jest *typem referencyjnym*. Należy zauważyć, że każda tablica jest typem referencyjnym, nawet jeśli jego elementy członkowskie są typami wartości.  
  
 Ponieważ każdy typ referencyjny reprezentuje bazową klasę .NET Framework, należy użyć słowa kluczowego [New](../../../language-reference/operators/new-operator.md) podczas inicjowania. Poniższa instrukcja Inicjuje tablicę.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementy, które nie są typami  
 Następujące elementy programistyczne nie kwalifikują się jako typy, ponieważ nie można określić żadnego z nich jako typu danych dla zadeklarowanego elementu:  
  
- Przestrzenie nazw  
  
- Moduły  
  
- Zdarzenia  
  
- Właściwości i procedury  
  
- Zmienne, stałe i pola  
  
## <a name="working-with-the-object-data-type"></a>Praca z typem danych obiektu  
 Do zmiennej typu danych można przypisać typ referencyjny lub typ wartości `Object` . `Object`Zmienna zawsze przechowuje odwołanie do danych, nigdy same same dane. Jeśli jednak typ wartości zostanie przypisany do `Object` zmiennej, zachowuje się tak, jakby przechowywać własne dane. Aby uzyskać więcej informacji, zobacz [Typ danych obiektu](../../../language-reference/data-types/object-data-type.md).  
  
 Można dowiedzieć się, czy `Object` zmienna działa jako typ referencyjny, czy typ wartości poprzez przekazanie go do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metody w <xref:Microsoft.VisualBasic.Information> klasie <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>zwraca `True` czy zawartość `Object` zmiennej reprezentuje typ referencyjny.  
  
## <a name="see-also"></a>Zobacz też

- [Typy wartości null](nullable-value-types.md)
- [Konwersje plików w Visual Basic](type-conversions.md)
- [Structure — Instrukcja](../../../language-reference/statements/structure-statement.md)
- [Skuteczne stosowanie typów danych](efficient-use-of-data-types.md)
- [Object — typ danych](../../../language-reference/data-types/object-data-type.md)
- [Typy danych](index.md)
