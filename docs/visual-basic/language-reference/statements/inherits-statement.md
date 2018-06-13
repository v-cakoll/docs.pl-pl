---
title: Inherits — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 43a8aa4e9e04ee035cb52e9f829de13e5c022217
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604344"
---
# <a name="inherits-statement"></a>Inherits — Instrukcja
Powoduje, że klasy lub interfejsu dziedziczenie atrybutów, zmiennych, właściwości, procedur i zdarzeń z innej klasy lub zestawu interfejsów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`basetypenames`|Wymagana. Nazwa klasy, z której pochodzi ta klasa.<br /><br /> —lub—<br /><br /> Nazwy interfejsów, spośród których pochodzi ten interfejs. Użyj przecinków do oddzielania wielu nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używana, `Inherits` instrukcji musi być pierwszym wierszem niepustą, komentarza-w definicji klasy lub interfejsu. Należy natychmiast wykonać `Class` lub `Interface` instrukcji.  
  
 Można użyć `Inherits` tylko w klasie lub interfejs. Oznacza to, że w kontekście deklaracja dziedziczenia nie może być plik źródłowy, przestrzeni nazw, struktury, modułu, procedurę lub blok.  
  
## <a name="rules"></a>Reguły  
  
-   **Dziedziczenie klas.** Jeśli używa klasy `Inherits` instrukcji, można określić tylko jedną klasę podstawową.  
  
     Klasa nie dziedziczy z klasy w nim zagnieżdżony.  
  
-   **Interfejs dziedziczenia.** Jeśli używa interfejsu `Inherits` instrukcji, można określić co najmniej jeden interfejsach podstawowych. Może dziedziczyć z dwóch interfejsów, nawet jeśli ich zdefiniować element członkowski o takiej samej nazwie. Jeśli to zrobisz, więc implementującej kodu musi umożliwia określenie, który element członkowski implementuje kwantyfikacja nazwy.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjne poziom dostępu. Na przykład `Public` interfejsu nie może dziedziczyć z `Friend` interfejsu.  
  
     Interfejs nie może dziedziczyć z interfejsu w nim zagnieżdżony.  
  
 Na przykład dziedziczenia klas w programie .NET Framework <xref:System.ArgumentException> klasy, która dziedziczy <xref:System.SystemException> klasy. Zapewnia to do <xref:System.ArgumentException> wszystkich wstępnie zdefiniowanych właściwości i procedur wymaganych przez wyjątki systemu, takich jak <xref:System.Exception.Message%2A> właściwości i <xref:System.Exception.ToString%2A> metody.  
  
 Na przykład z dziedziczenia interfejsu w programie .NET Framework <xref:System.Collections.ICollection> interfejs, który dziedziczy <xref:System.Collections.IEnumerable> interfejsu. Powoduje to <xref:System.Collections.ICollection> dziedziczenia definicji modułu wyliczającego wymagane do przechodzenia kolekcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Inherits` instrukcji, aby pokazać, jak klasa o nazwie `thisClass` może dziedziczyć wszystkich elementów członkowskich klasy podstawowej o nazwie `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dziedziczenia wiele interfejsów.  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 Interfejs o nazwie `thisInterface` teraz obejmuje wszystkie definicje w <xref:System.IComparable>, <xref:System.IDisposable>, i <xref:System.IFormattable> dziedziczone elementy Członkowskie przekaże odpowiednio do określonego typu porównania dwóch obiektów wydanie interfejsy przydzielone zasoby oraz wartości obiektu jako `String`. Klasa, która implementuje `thisInterface` musi implementować każdy element członkowski każdy interfejs podstawowy.  
  
## <a name="see-also"></a>Zobacz też  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
