---
title: Namespace lub typ określony w elemencie Imports na poziomie projektu &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawiera żadnej publicznej składowej lub nie można odnaleźć
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 215d8d301317f711aecb88167030e70ed01408aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552466"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace lub typ określony w elemencie Imports na poziomie projektu &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawiera żadnej publicznej składowej lub nie można odnaleźć
Namespace lub typ określony w elemencie Imports na poziomie projektu\<qualifiedelementname >' nie zawiera żadnej publicznej składowej lub nie można odnaleźć. Upewnij się, że przestrzeń nazw lub typ zostały zdefiniowane i zawierają co najmniej jednego członka publicznego. Upewnij się, że nazwa aliasu nie zawiera innych aliasów.  
  
 Właściwość importowania projektu określa element zawierający, która nie może być odnaleziona lub nie definiuje `Public` elementów członkowskich.  
  
 A *zawierającego element* może być przestrzeni nazw, klasy, struktury, moduł, interfejs lub wyliczenie. Element zawierający zawiera składniki, takie jak zmienne, procedury lub inne elementy zawierające.  
  
 Celem importowania jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez ich kwalifikowania. Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne. Aby uzyskać więcej informacji, zobacz "Importowanie zawierający elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Jeśli kompilator nie może znaleźć określony element zawierający, nie można go rozpoznać odwołania, które go używają. W przypadku znalezienia elementu, ale nie ujawnia na dowolny element `Public` elementów członkowskich, a następnie Brak odwołania może odnieść sukces. W obu przypadkach jest bez znaczenia, aby zaimportować element.  
  
 Możesz użyć **projektanta projektu** do określania elementów do zaimportowania. Użyj **zaimportowane przestrzenie nazw** części **odwołania** strony. Aby przejść do **projektanta projektu** przez dwukrotne kliknięcie **mój projekt** ikony w **Eksploratora rozwiązań**.  
  
 **Identyfikator błędu:** BC40057  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Otwórz **projektanta projektu** i przełącz się do **odwołania** strony.  
  
2.  W **zaimportowane przestrzenie nazw** sekcji, upewnij się, że element zawierający jest dostępny z projektu.  
  
3.  Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz także
- [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Przestrzenie nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
