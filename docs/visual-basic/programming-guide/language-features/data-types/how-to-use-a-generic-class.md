---
title: 'Porady: używanie klasy ogólnej'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 87ca0da5095484615666cda505b4f7678d8160de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350057"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Porady: używanie klasy ogólnej (Visual Basic)
Klasa, która pobiera *parametry typu* , jest nazywana *klasą rodzajową*. Jeśli używasz klasy generycznej, możesz wygenerować utworzoną *klasę* z niej, dostarczając *argument typu* dla każdego z tych parametrów. Następnie można zadeklarować zmienną typu konstruowanej klasy i można utworzyć wystąpienie klasy skonstruowanej i przypisać ją do tej zmiennej.  
  
 Oprócz klas można także definiować struktury ogólne, interfejsy, procedury i Delegaty oraz korzystać z nich.  
  
 Poniższa procedura przyjmuje klasę generyczną zdefiniowaną w .NET Framework i tworzy dla niej wystąpienie.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Aby użyć klasy, która przyjmuje parametr typu  
  
1. Na początku pliku źródłowego Dołącz [instrukcję Imports (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) , aby zaimportować przestrzeń nazw <xref:System.Collections.Generic?displayProperty=nameWithType>. Dzięki temu można odwołać się do klasy <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> bez konieczności pełnego kwalifikowania go do odróżnienia od innych klas kolejek, takich jak <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2. Utwórz obiekt w normalny sposób, ale Dodaj `(Of type)` natychmiast po nazwie klasy.  
  
     Poniższy przykład używa tej samej klasy (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) do tworzenia dwóch obiektów kolejki, które zawierają elementy o różnych typach danych. Dodaje elementy do końca każdej kolejki, a następnie usuwa i wyświetla elementy z przodu każdej kolejki.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Niezależność od języka i składniki niezależne od języka](../../../../standard/language-independence-and-language-independent-components.md)
- [Z](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Instrukcje: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Iteratory](../../../../visual-basic/programming-guide/concepts/iterators.md)
