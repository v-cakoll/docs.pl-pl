---
title: 'Porady: etykietowanie instrukcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-label-statements-visual-basic"></a>Porady: etykietowanie instrukcji (Visual Basic)
Bloki instrukcji składają się z wierszy kodu rozdzielone dwukropkiem. Wiersze kodu poprzedzone identyfikujący ciąg lub liczba całkowita są określane jako *etykietą*. Etykiety instrukcji są używane do oznaczenia wiersz kodu, aby zidentyfikować go do użytku w instrukcjach takich jak `On Error Goto`.  
  
 Etykiety mogą być albo prawidłowych identyfikatorów języka Visual Basic — takich jak te, które identyfikują programistyczny — lub literały całkowite. Etykiety musi znajdować się na początku wiersza kodu źródłowego i musi być z dwukropkiem, niezależnie od tego, czy występuje po nim instrukcji w tym samym wierszu.  
  
 Kompilator identyfikuje etykiety przez sprawdzenie, czy początek wiersza odpowiada żadnego identyfikatora już zdefiniowany. Jeśli nie, kompilator przyjęto założenie, że jest etykiety.  
  
 Etykiety ma miejsce ich własnych deklaracji i nie zakłóca innych identyfikatorów. Zakres etykiety jest treści metody. Deklaracja etykieta ma pierwszeństwo w każdej sytuacji niejednoznaczne.  
  
> [!NOTE]
>  Etykiety może być używany tylko instrukcje wykonywalne wewnątrz metody.  
  
### <a name="to-label-a-line-of-code"></a>Aby dodać etykietę wiersza kodu  
  
-   Umieść identyfikator i dwukropek, na początku wiersza kodu źródłowego.  
  
     Na przykład etykietą następujące wiersze kodu `Jump` i `120`odpowiednio:  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
