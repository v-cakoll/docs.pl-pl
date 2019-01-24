---
title: 'Instrukcje: Przerywanie i łączenie instrukcji w Code (Visual Basic)'
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
ms.openlocfilehash: b19c36018a0938b9b6546e5baefbbc3de1e5dd30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619918"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Instrukcje: Przerywanie i łączenie instrukcji w Code (Visual Basic)
Podczas pisania kodu, można utworzyć w czasie długich instrukcji, które wymagają przewijanie w poziomie w edytorze kodu. Mimo że to nie ma wpływu na sposób działania kodu, jego utrudnia nikogo odczytać kodu znajdującego się na monitor. W takich przypadkach należy rozważyć podzielenie pojedynczej instrukcji długich na kilka wierszy.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Aby przerwać pojedynczej instrukcji wiele wierszy  
  
-   Użyj znaku kontynuacji wiersza, który jest znakiem podkreślenia (`_`), w momencie, dla której ma zostać na podział wiersza. Znak podkreślenia należy natychmiast poprzedzone spację i bezpośrednio po nim terminator wiersza (powrót karetki).  
  
    > [!NOTE]
    >  W niektórych przypadkach Jeśli pominięto znak kontynuacji wiersza, kompilator Visual Basic będą nadal w następnym wierszu kodu niejawnie instrukcji. Aby uzyskać listę elementy składni, dla których można pominąć znak kontynuacji wiersza, zobacz "Niejawnej kontynuacji wiersza" w [instrukcji](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     W poniższym przykładzie instrukcja jest dzielony na cztery wiersze ze znakami kontynuacji wiersza przerywa wszystkie, ale ostatni wiersz.  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     Za pomocą tej sekwencji sprawia, że Twój kod łatwiejsza do odczytania, zarówno online, jak i kiedy wydrukowany.  
  
     Znak kontynuacji wiersza musi być ostatnim znakiem w wierszu. Nie można wykonać to z jakichkolwiek innych czynności w tym samym wierszu.  
  
     Istnieje pewne ograniczenia, do których można użyć znaku kontynuacji wiersza; na przykład nie można go użyć w środku nazwę argumentu. Możesz przerwać listy argumentów znakiem kontynuacji wiersza, ale poszczególne nazwy argumentów musi pozostać bez zmian.  
  
     Komentarz nie może kontynuować, za pomocą znaku kontynuacji wiersza. Kompilator nie zbadać znaki w komentarzu do specjalnego znaczenia. Komentarz do wielu linii, powtórz symbol komentarza (`'`) w każdym wierszu.  
  
 Mimo że zaleca się umieszczenie każdej instrukcji w osobnym wierszu, Visual Basic umożliwia również umieścić użycie wielu instrukcji w tym samym wierszu.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Aby umieścić użycie wielu instrukcji w tym samym wierszu  
  
-   Instrukcje należy oddzielić średnikiem (`:`), jak w poniższym przykładzie.  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
