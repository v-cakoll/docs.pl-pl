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
ms.openlocfilehash: 0bda03d3c01356317fbcc56d44199ff4f9484b5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053941"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Określa, że klasa może być używana tylko jako klasa bazowa i że nie można utworzyć obiektu bezpośrednio z niej.  
  
## <a name="remarks"></a>Uwagi  
 Celem *klasy bazowej* (znany także jako *abstrakcyjna klasa*) polega na zdefiniowaniu funkcji, które są wspólne dla wszystkich klas, które są od niego pochodzi. Spowoduje to zapisanie klasy pochodne od konieczności przedefiniować wspólne elementy. W niektórych przypadkach wspólnej nie jest to kompletny, aby wprowadzić użytecznej obiektu, a każda klasa pochodna definiuje brakującej funkcji. W takim przypadku należy kod konsumencki do tworzenia obiektów tylko z klas pochodnych. Możesz użyć `MustInherit` w klasie bazowej do wyegzekwowania tego.  
  
 Używanie innego `MustInherit` klasy jest ograniczenie zmienną do zestawu powiązanych klas. Można zdefiniować klasę bazową i pochodną te klasy pokrewne. Klasa bazowa trzeba podawać żadnych funkcji, które są wspólne dla wszystkich klas pochodnych, ale może służyć jako filtr do przypisywania wartości do zmiennych. Jeśli Twój kod konsumencki deklaruje zmienną jako klasa bazowa, Visual Basic umożliwia przypisywanie tylko obiekt z jednej z klas pochodnych do tej zmiennej.  
  
 .NET Framework definiuje kilka `MustInherit` klas między nimi <xref:System.Array>, <xref:System.Enum>, i <xref:System.ValueType>. <xref:System.ValueType> jest przykładem klasę bazową, która ogranicza zmienną. Wszystkie typy wartości wywodzą się z <xref:System.ValueType>. Jeśli zadeklarujesz zmienną <xref:System.ValueType>, tylko typy wartości można przypisać do zmiennej.  
  
## <a name="rules"></a>reguły  
  
- **Kontekst deklaracji.** Możesz użyć `MustInherit` tylko w `Class` instrukcji.  
  
- **Modyfikatory połączone.** Nie można określić `MustInherit` wraz z `NotInheritable` w tej samej deklaracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje wymuszonego dziedziczenia i zastępowania wymuszone. Klasa bazowa `shape` definiuje zmienną `acrossLine`. Klasy `circle` i `square` dziedziczyć `shape`. Dziedziczą definicji `acrossLine`, ale one należy zdefiniować funkcję `area` ponieważ to obliczenie jest inna dla każdego rodzaju kształtu.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 Można zadeklarować `shape1` i `shape2` typu `shape`. Jednak nie można utworzyć obiektu z `shape` ponieważ brakuje funkcjonalność funkcji `area` i jest oznaczony jako `MustInherit`.  
  
 Ponieważ są one zadeklarowane jako `shape`, zmienne `shape1` i `shape2` są ograniczone do obiektów z klas pochodnych `circle` i `square`. Visual Basic nie umożliwić przypisanie jakiegokolwiek innego obiektu do tych zmiennych, który zapewnia wysoki poziom bezpieczeństwa typu.  
  
## <a name="usage"></a>Użycie  
 `MustInherit` Modyfikatora można używać w tym kontekście:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
