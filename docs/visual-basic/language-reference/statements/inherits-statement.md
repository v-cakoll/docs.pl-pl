---
title: Inherits — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 4a98ada39a04730b46f40fe139e72d1855d9b067
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533251"
---
# <a name="inherits-statement"></a>Inherits — Instrukcja
Powoduje, że bieżącą klasę lub interfejs dziedziczy atrybuty, zmiennych, właściwości, procedur i zdarzeń z innej klasy lub zestawu interfejsów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`basetypenames`|Wymagane. Nazwa klasy, z której pochodzi ta klasa.<br /><br /> —lub—<br /><br /> Nazwy interfejsów, z których pochodzi ten interfejs. Użyj przecinków do oddzielenia wielu nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używane, `Inherits` instrukcja musi być pierwszy wiersz nie jest pusty, bez komentarza w definicji klasy lub interfejsu. Należy natychmiast wykonać `Class` lub `Interface` instrukcji.  
  
 Możesz użyć `Inherits` tylko w klasie lub interfejsie. Oznacza to, że kontekst deklaracji dla dziedziczenia nie może być plik źródłowy, przestrzeń nazw, struktury, moduł, procedurę lub blok.  
  
## <a name="rules"></a>reguły  
  
-   **Dziedziczenie klas.** Jeśli korzysta z klasy `Inherits` instrukcji, można określić tylko jedną klasę bazową.  
  
     Klasa nie może też dziedziczyć z klasy w niej zagnieżdżonej.  
  
-   **Interfejs dziedziczenia.** Jeśli korzysta z interfejsu `Inherits` instrukcji, można określić jeden lub więcej podstawowych interfejsów. Dwa interfejsy mogą dziedziczyć, nawet wtedy, gdy każda definiują element członkowski o takiej samej nazwie. Jeśli to zrobisz, więc w kodzie implementującym musi być określona elementu członkowskiego, który implementuje kwantyfikacja nazwy.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjny poziom dostępu. Na przykład `Public` interfejs nie może dziedziczyć `Friend` interfejsu.  
  
     Interfejs nie może dziedziczyć z interfejsu w nim zagnieżdżony.  
  
 Na przykład dziedziczenia klas w programie .NET Framework <xref:System.ArgumentException> klasy, która dziedziczy po elemencie <xref:System.SystemException> klasy. Dzięki temu można <xref:System.ArgumentException> wszystkich wstępnie zdefiniowanych właściwości i procedur wymaganych przez wyjątki systemowe, takie jak <xref:System.Exception.Message%2A> właściwości i <xref:System.Exception.ToString%2A> metody.  
  
 Na przykład dziedziczenia interfejsu w programie .NET Framework <xref:System.Collections.ICollection> interfejs, który dziedziczy z <xref:System.Collections.IEnumerable> interfejsu. Powoduje to, że <xref:System.Collections.ICollection> dziedziczenia definicji enumerator musieli przemierzają kolekcję.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Inherits` instrukcję, aby pokazać, jak klasę o nazwie `thisClass` może dziedziczyć wszystkie elementy członkowskie klasa bazowa o nazwie `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje dziedziczenie z wielu interfejsów.  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 Interfejs o nazwie `thisInterface` zawiera teraz wszystkie definicje w <xref:System.IComparable>, <xref:System.IDisposable>, i <xref:System.IFormattable> interfejsów dziedziczone elementy Członkowskie zapewniają odpowiednio specyficznych dla typu porównanie dwóch obiektów, zwalniając przydzielone zasoby oraz wartość obiektu jako `String`. Klasa, która implementuje `thisInterface` musi implementować każdy członek każdy interfejs podstawowy.  
  
## <a name="see-also"></a>Zobacz też  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
