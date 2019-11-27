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
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353227"
---
# <a name="inherits-statement"></a>Inherits — Instrukcja
Powoduje, że bieżąca Klasa lub interfejs dziedziczy atrybuty, zmienne, właściwości, procedury i zdarzenia z innej klasy lub zestawu interfejsów.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`basetypenames`|Wymagana. Nazwa klasy, z której pochodzi ta klasa.<br /><br /> —lub—<br /><br /> Nazwy interfejsów, z których pochodzi ten interfejs. Użyj przecinków, aby rozdzielić wiele nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli jest używana, instrukcja `Inherits` musi być pierwszym niepustym wierszem bez komentarza w definicji klasy lub interfejsu. Należy od razu przestrzegać instrukcji `Class` lub `Interface`.  
  
 `Inherits` można użyć tylko w klasie lub interfejsie. Oznacza to, że kontekst deklaracji dziedziczenia nie może być plikiem źródłowym, przestrzenią nazw, strukturą, modułem, procedurą lub blokiem.  
  
## <a name="rules"></a>Reguły  
  
- **Dziedziczenie klas.** Jeśli Klasa używa instrukcji `Inherits`, można określić tylko jedną klasę bazową.  
  
     Klasa nie może też dziedziczyć z klasy w niej zagnieżdżonej.  
  
- **Dziedziczenie interfejsu.** Jeśli interfejs używa instrukcji `Inherits`, można określić jeden lub więcej interfejsów podstawowych. Można dziedziczyć z dwóch interfejsów, nawet jeśli każda z nich definiuje element członkowski o tej samej nazwie. W takim przypadku kod implementujący musi używać kwalifikacji nazw, aby określić, który element członkowski jest wdrażany.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjnym poziomem dostępu. Na przykład interfejs `Public` nie może dziedziczyć po interfejsie `Friend`.  
  
     Interfejs nie może dziedziczyć z interfejsu zagnieżdżonego w nim.  
  
 Przykładem dziedziczenia klasy w .NET Framework jest Klasa <xref:System.ArgumentException>, która dziedziczy z klasy <xref:System.SystemException>. Dzięki temu <xref:System.ArgumentException> wszystkie wstępnie zdefiniowane właściwości i procedury wymagane przez wyjątki systemowe, takie jak Właściwość <xref:System.Exception.Message%2A> i Metoda <xref:System.Exception.ToString%2A>.  
  
 Przykładem dziedziczenia interfejsów w .NET Framework jest interfejs <xref:System.Collections.ICollection>, który dziedziczy po interfejsie <xref:System.Collections.IEnumerable>. Powoduje to, że <xref:System.Collections.ICollection> dziedziczyć definicję modułu wyliczającego wymaganego do przechodzenia do kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Inherits`, aby pokazać, jak Klasa o nazwie `thisClass` może odziedziczyć wszystkie elementy członkowskie klasy bazowej o nazwie `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje dziedziczenie wielu interfejsów.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 Interfejs o nazwie `thisInterface` obejmuje teraz wszystkie definicje w interfejsach <xref:System.IComparable>, <xref:System.IDisposable>i <xref:System.IFormattable> dziedziczone elementy członkowskie są odpowiednio przeznaczone do porównywania typów dwóch obiektów, zwalniania przydziałów zasobów i wyrażania wartości obiektu jako `String`. Klasa implementująca `thisInterface` musi implementować każdy element członkowski każdego z interfejsów podstawowych.  
  
## <a name="see-also"></a>Zobacz także

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
