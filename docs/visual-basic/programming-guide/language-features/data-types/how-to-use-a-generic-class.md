---
title: 'Porady: używanie klasy ogólnej (Visual Basic)'
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
ms.openlocfilehash: 108532e5b765fa918fa894199ef710a9f52db4e4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658577"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Porady: używanie klasy ogólnej (Visual Basic)
Klasa, która przyjmuje *parametry typu* nosi nazwę *klasy generycznej*. Jeśli używasz klasy ogólnej, można wygenerować *skonstruowany klasy* z niego, podając *argument typu* dla każdego z tych parametrów. Następnie można zadeklarować zmienną typu klasy skonstruowany, a następnie można utworzyć wystąpienia klasy skonstruowany i przypisać ją do tej zmiennej.  
  
 Oprócz klas można również zdefiniować i używać struktury ogólne, interfejsy, procedury i delegatów.  
  
 Poniższa procedura ma klasę ogólną zdefiniowane w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i tworzy wystąpienie z niego.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Aby użyć klasy, która przyjmuje parametr typu  
  
1.  Na początku pliku źródłowego, obejmują [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do zaimportowania <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Dzięki temu można odwoływać się do <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy bez konieczności pełnej kwalifikacji je odróżnić go od innych klas kolejki takich jak <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2.  Utwórz obiekt w normalny sposób, ale Dodaj `(Of` `type``)` natychmiast po nazwie klasy.  
  
     W poniższym przykładzie użyto tej samej klasy (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) do utworzenia dwóch obiektów kolejki, zawierających elementy różnych typów danych. Dodaje element do końca każdej kolejki i następnie usuwa i wyświetla elementy z przodu każdej kolejki.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
- [Niezależność od języka i składniki niezależne od języka](../../../../standard/language-independence-and-language-independent-components.md)  
- [z](../../../../visual-basic/language-reference/statements/of-clause.md)  
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
- [Instrukcje: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
- [Iteratory](../../../../visual-basic/programming-guide/concepts/iterators.md)
