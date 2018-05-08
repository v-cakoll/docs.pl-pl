---
title: MustInherit (Visual Basic)
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
ms.openlocfilehash: 5d622c1cff77a45c8de7772af7efbb73586f4400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Określa, że klasa może być używana tylko jako klasa bazowa i że nie można utworzyć obiektu bezpośrednio z niej.  
  
## <a name="remarks"></a>Uwagi  
 Celem *klasa podstawowa* (znanej także jako *klasy abstrakcyjnej*) jest określenie funkcje, które są wspólne dla wszystkich klas pochodnych. Spowoduje to zapisanie klasy pochodnej z konieczności ponownego zdefiniowania wspólne elementy. W niektórych przypadkach wspólnej nie jest to pełny, aby używać obiektu, a każda klasa pochodna definiuje brakującej funkcjonalności. W takim przypadku ma zostać odbierającą do tworzenia obiektów tylko z klasy pochodnej. Możesz użyć `MustInherit` w klasie podstawowej tego wymusić.  
  
 Użycie innego `MustInherit` klasy jest ograniczenie zmienną do zestawu powiązanymi klasami. Można zdefiniować klasę podstawową i pochodną te klasy pokrewne. Klasa podstawowa nie trzeba podać żadnej funkcji, które są wspólne dla wszystkich klas pochodnych, ale może służyć jako filtr dla przypisywanie wartości do zmiennych. Jeśli odbierającą kod deklaruje zmienną jako klasę podstawową, Visual Basic umożliwia przypisanie tylko obiekt z jednej z klas pochodnych do tej zmiennej.  
  
 .NET Framework definiuje kilka `MustInherit` klas między nimi <xref:System.Array>, <xref:System.Enum>, i <xref:System.ValueType>. <xref:System.ValueType> jest to przykład klasy podstawowej, która ogranicza zmiennej. Wszystkie typy wartości pochodzi od <xref:System.ValueType>. Deklarowanie zmiennej jako <xref:System.ValueType>, tylko typy wartości można przypisać do tej zmiennej.  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `MustInherit` tylko w `Class` instrukcji.  
  
-   **Łączna modyfikatorów.** Nie można określić `MustInherit` razem z `NotInheritable` w tej samej deklaracji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono wymuszone dziedziczenia i zastępowanie wymuszone. Klasa podstawowa `shape` definiuje zmienną `acrossLine`. Klasy `circle` i `square` pochodzi od `shape`. Dziedziczą definicji `acrossLine`, ale zdefiniować funkcję `area` to obliczenie różni się dla każdego rodzaju kształtu.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Można zadeklarować `shape1` i `shape2` typu `shape`. Jednak nie można utworzyć obiektu z `shape` ponieważ brakuje w nim funkcje funkcji `area` i jest oznaczony jako `MustInherit`.  
  
 Ponieważ zostały zgłoszone jako `shape`, zmienne `shape1` i `shape2` są ograniczone do obiektów z klasy pochodnej `circle` i `square`. Visual Basic nie umożliwiają przypisywanie drugi obiekt do tych zmiennych zapewniający wysokiego poziomu zabezpieczeń.  
  
## <a name="usage"></a>Użycie  
 `MustInherit` Modyfikatora można używać w tym kontekście:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
