---
title: 'Instrukcje: Używanie klasy ogólnej'
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
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393847"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Porady: używanie klasy ogólnej (Visual Basic)
Klasa, która pobiera *parametry typu* , jest nazywana *klasą rodzajową*. Jeśli używasz klasy generycznej, możesz wygenerować utworzoną *klasę* z niej, dostarczając *argument typu* dla każdego z tych parametrów. Następnie można zadeklarować zmienną typu konstruowanej klasy i można utworzyć wystąpienie klasy skonstruowanej i przypisać ją do tej zmiennej.  
  
 Oprócz klas można także definiować struktury ogólne, interfejsy, procedury i Delegaty oraz korzystać z nich.  
  
 Poniższa procedura przyjmuje klasę generyczną zdefiniowaną w .NET Framework i tworzy dla niej wystąpienie.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Aby użyć klasy, która przyjmuje parametr typu  
  
1. Na początku pliku źródłowego Dołącz [instrukcję Imports (przestrzeń nazw i typ platformy .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) , aby zaimportować <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeń nazw. Pozwala to na odwoływanie się do <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy bez konieczności pełnego kwalifikowania go do odróżnienia od innych klas kolejek, takich jak <xref:System.Collections.Queue?displayProperty=nameWithType> .  
  
2. Utwórz obiekt w normalny sposób, ale Dodaj `(Of type)` natychmiast po nazwie klasy.  
  
     Poniższy przykład używa tej samej klasy ( <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> ) do tworzenia dwóch obiektów kolejki, które zawierają elementy o różnych typach danych. Dodaje elementy do końca każdej kolejki, a następnie usuwa i wyświetla elementy z przodu każdej kolejki.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Typy ogólne w Visual Basic](generic-types.md)
- [Niezależność od języka i składniki niezależne od języka](../../../../standard/language-independence-and-language-independent-components.md)
- [Z](../../../language-reference/statements/of-clause.md)
- [Imports — Instrukcja (.NET Namespace i Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Iteratory](../../concepts/iterators.md)
