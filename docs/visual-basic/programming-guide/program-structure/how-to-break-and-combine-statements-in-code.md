---
title: 'Porady: przerywanie i łączenie instrukcji w Code (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 6bca3d62cb3e886ee08b9169d63d4c3a38247f3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651021"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Porady: przerywanie i łączenie instrukcji w Code (Visual Basic)
Podczas pisania kodu, można utworzyć w czasie długich instrukcji, które wymagają przewijanie w poziomie w edytorze kodu. Mimo że to nie wpływa na sposób działania kodu, go utrudnia nikogo odczytać kodu znajdującego się na monitora. W takim przypadku należy rozważyć dzielenie jednej instrukcji długa na kilka wierszy.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Aby podzielić jednej instrukcji na wiele wierszy  
  
-   Użyj znaku kontynuacji wiersza jest to znak podkreślenia (`_`), w momencie, w którym ma zostać na podział wiersza. Podkreślenie musi być natychmiast poprzedzone spację i od razu następuje terminator wiersza (powrotu karetki).  
  
    > [!NOTE]
    >  W niektórych przypadkach w przypadku pominięcia znak kontynuacji wiersza kompilator Visual Basic niejawnie będzie instrukcji w następnym wierszu kodu. Aby uzyskać listę elementy składni, w których można pominąć znak kontynuacji wiersza, zobacz "Niejawne kontynuacji wiersza" w [instrukcje](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     W poniższym przykładzie instrukcja jest dzielony na cztery wiersze z przerywa wszystkie znaki kontynuacji wiersza, ale ostatniego wiersza.  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     Przy użyciu tej sekwencji ułatwia kodu do odczytu, online i po drukowaniu.  
  
     Znak kontynuacji wiersza musi być ostatnim znakiem w wierszu. Nie można wykonać jego się inaczej w tym samym wierszu.  
  
     Istnieją pewne ograniczenia klienckiemu, których można użyć znaku kontynuacji wiersza; na przykład nie można go użyć w środku nazwy argumentu. Lista argumentów znak kontynuacji wiersza mogą być dzielone, ale nazwy poszczególnych argumenty muszą pozostać bez zmian.  
  
     Nie można kontynuować komentarz przy użyciu znak kontynuacji wiersza. Kompilator nie Sprawdź, czy znaki w komentarz dotyczący specjalnego znaczenia. Komentarz wielu linii, powtórz symbol komentarza (`'`) w każdym wierszu.  
  
 Jednak zaleca się umieszczenie każdej instrukcji w osobnym wierszu, Visual Basic umożliwia również umieścić użycie wielu instrukcji w tym samym wierszu.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Aby umieścić użycie wielu instrukcji w tym samym wierszu  
  
-   Instrukcje należy oddzielić średnikiem (`:`), jak w poniższym przykładzie.  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
