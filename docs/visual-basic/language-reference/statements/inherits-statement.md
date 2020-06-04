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
ms.openlocfilehash: 5d88a01f90bc91a88229d19aa2368f8c71075b2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404502"
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
|`basetypenames`|Wymagany. Nazwa klasy, z której pochodzi ta klasa.<br /><br /> -lub-<br /><br /> Nazwy interfejsów, z których pochodzi ten interfejs. Użyj przecinków, aby rozdzielić wiele nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli jest używana, `Inherits` instrukcja musi być pierwszym niepustym wierszem bez komentarza w definicji klasy lub interfejsu. Należy od razu przestrzegać `Class` instrukcji or `Interface` .  
  
 Można używać `Inherits` tylko w klasie lub interfejsie. Oznacza to, że kontekst deklaracji dziedziczenia nie może być plikiem źródłowym, przestrzenią nazw, strukturą, modułem, procedurą lub blokiem.  
  
## <a name="rules"></a>Reguły  
  
- **Dziedziczenie klas.** Jeśli Klasa używa `Inherits` instrukcji, można określić tylko jedną klasę bazową.  
  
     Klasa nie może dziedziczyć z klasy zagnieżdżonej w tym elemencie.  
  
- **Dziedziczenie interfejsu.** Jeśli interfejs używa `Inherits` instrukcji, można określić jeden lub więcej interfejsów podstawowych. Można dziedziczyć z dwóch interfejsów, nawet jeśli każda z nich definiuje element członkowski o tej samej nazwie. W takim przypadku kod implementujący musi używać kwalifikacji nazw, aby określić, który element członkowski jest wdrażany.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjnym poziomem dostępu. Na przykład `Public` interfejs nie może dziedziczyć z `Friend` interfejsu.  
  
     Interfejs nie może dziedziczyć z interfejsu zagnieżdżonego w nim.  
  
 Przykładem dziedziczenia klasy w .NET Framework jest <xref:System.ArgumentException> Klasa, która dziedziczy z <xref:System.SystemException> klasy. Zapewnia to <xref:System.ArgumentException> wszystkie wstępnie zdefiniowane właściwości i procedury wymagane przez wyjątki systemowe, takie jak <xref:System.Exception.Message%2A> Właściwość i <xref:System.Exception.ToString%2A> Metoda.  
  
 Przykładem dziedziczenia interfejsów w .NET Framework jest <xref:System.Collections.ICollection> interfejs, który dziedziczy z <xref:System.Collections.IEnumerable> interfejsu. Powoduje to <xref:System.Collections.ICollection> dziedziczenie definicji modułu wyliczającego wymaganego do przechodzenia do kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `Inherits` Aby pokazać, jak Klasa o nazwie `thisClass` może dziedziczyć wszystkich elementów członkowskich klasy bazowej o nazwie `anotherClass` .  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje dziedziczenie wielu interfejsów.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 Interfejs o nazwie `thisInterface` teraz zawiera wszystkie definicje w <xref:System.IComparable> , <xref:System.IDisposable> i <xref:System.IFormattable> interfejsy dziedziczonych elementów członkowskich odpowiednio dla porównywania typów dwóch obiektów, zwalniania przyznanych zasobów i wyrażania wartości obiektu jako `String` . Klasa implementująca `thisInterface` musi implementować każdy element członkowski każdego interfejsu podstawowego.  
  
## <a name="see-also"></a>Zobacz też

- [MustInherit](../modifiers/mustinherit.md)
- [NotInheritable](../modifiers/notinheritable.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Podstawowe informacje o dziedziczeniu](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Interfejsy](../../programming-guide/language-features/interfaces/index.md)
