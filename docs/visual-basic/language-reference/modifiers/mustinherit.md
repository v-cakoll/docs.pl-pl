---
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 84df7a5cfdad3b5bc6764675725a5d0cb402b0b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396210"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Określa, że Klasa może być używana tylko jako klasa bazowa i że nie można bezpośrednio z niej tworzyć obiektów.  
  
## <a name="remarks"></a>Uwagi  
 Celem *klasy podstawowej* (znanej również jako *Klasa abstrakcyjna*) jest zdefiniowanie funkcji, która jest wspólna dla wszystkich klas pochodnych. Spowoduje to zapisanie klas pochodnych przed koniecznością ponownego definiowania elementów wspólnych. W niektórych przypadkach ta wspólna funkcja nie jest wystarczająca do tworzenia użytecznego obiektu, a każda klasa pochodna definiuje brakującą funkcję. W takim przypadku kod zużywający ma tworzyć obiekty tylko z klas pochodnych. `MustInherit`Aby wymusić to, użyj klasy bazowej.  
  
 Innym zastosowaniem `MustInherit` klasy jest ograniczenie zmiennej do zestawu powiązanych klas. Można zdefiniować klasę bazową i utworzyć wszystkie powiązane z nią klasy. Klasa bazowa nie musi udostępniać żadnych funkcji wspólnych dla wszystkich klas pochodnych, ale może być jako filtr do przypisywania wartości do zmiennych. Jeśli kod zużywający deklaruje zmienną jako klasę bazową, Visual Basic umożliwia przypisanie tylko obiektu z jednej z klas pochodnych do tej zmiennej.  
  
 .NET Framework definiuje kilka `MustInherit` klas, <xref:System.Array> <xref:System.Enum> , i <xref:System.ValueType> . <xref:System.ValueType>jest przykładem klasy bazowej, która ogranicza zmienną. Wszystkie typy wartości pochodzą od <xref:System.ValueType> . Jeśli zadeklarujesz zmienną jako <xref:System.ValueType> , można przypisać tylko typy wartości do tej zmiennej.  
  
## <a name="rules"></a>Reguły  
  
- **Kontekst deklaracji.** Można użyć `MustInherit` tylko w `Class` instrukcji.  
  
- **Połączone modyfikatory.** Nie można określić `MustInherit` razem z `NotInheritable` w tej samej deklaracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje zarówno wymuszone dziedziczenie, jak i wymuszone przesłanianie. Klasa bazowa `shape` definiuje zmienną `acrossLine` . Klasy `circle` i `square` pochodzą od `shape` . Dziedziczą one definicję `acrossLine` , ale muszą definiować funkcję, `area` ponieważ obliczenia różnią się w zależności od typu kształtu.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 Można zadeklarować `shape1` `shape2` Typ `shape` . Nie można jednak utworzyć obiektu, ponieważ nie ma `shape` on funkcjonalności funkcji `area` i jest oznaczony `MustInherit` .  
  
 Ponieważ są one deklarowane jako `shape` , zmienne `shape1` i `shape2` są ograniczone do obiektów z klas pochodnych `circle` i `square` . Visual Basic nie pozwala na przypisanie żadnych innych obiektów do tych zmiennych, co zapewnia wysoki poziom bezpieczeństwa typów.  
  
## <a name="usage"></a>Użycie  
 `MustInherit`Modyfikator może być używany w tym kontekście:  
  
 [Class, instrukcja](../statements/class-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [Inherits — Instrukcja](../statements/inherits-statement.md)
- [NotInheritable](notinheritable.md)
- [Słowa kluczowe](../keywords/index.md)
- [Podstawowe informacje o dziedziczeniu](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
