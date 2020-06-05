---
title: Przestrzeń nazw lub typ określony w elemencie Imports „<qualifiedelementname>” na poziomie projektu nie zawierają żadnego członka publicznego lub nie można go odnaleźć
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 0ee235252d69e6f77ce53b048f45e73d0969e864
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409455"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Przestrzeń nazw lub typ określony w elemencie Imports „\<qualifiedelementname>” na poziomie projektu nie zawierają żadnego członka publicznego lub nie można go odnaleźć
Przestrzeń nazw lub typ określony w elemencie Imports "" na poziomie projektu \<qualifiedelementname> nie zawiera żadnej publicznej składowej lub nie można jej znaleźć. Upewnij się, że przestrzeń nazw lub typ jest zdefiniowany i zawiera co najmniej jedną publiczną składową. Upewnij się, że Nazwa aliasu nie zawiera innych aliasów.  
  
 Właściwość Import projektu określa element zawierający, którego nie można odnaleźć lub nie definiuje żadnych `Public` elementów członkowskich.  
  
 *Element zawierający* może być przestrzenią nazw, klasą, strukturą, modułem, interfejsem lub wyliczeniem. Element zawierający zawiera elementy członkowskie, takie jak zmienne, procedury lub inne elementy zawierające.  
  
 Celem importowania jest umożliwienie kodowi dostępu do przestrzeni nazw lub typów elementów członkowskich bez konieczności kwalifikowania się do nich. W projekcie może być również konieczne dodanie odwołania do przestrzeni nazw lub typu. Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odniesieniu do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Jeśli kompilator nie może znaleźć określonego elementu zawierającego, wówczas nie może rozpoznać odwołań, które go używają. Jeśli odnajdzie element, ale element nie ujawnia żadnych `Public` elementów członkowskich, odwołanie nie może się powieść. W obu przypadkach nie ma znaczenia, aby zaimportować element.  
  
 Możesz użyć **projektanta projektu** , aby określić elementy do zaimportowania. Użyj sekcji **zaimportowane przestrzenie nazw** na stronie **odwołania** . Aby uzyskać dostęp do **projektanta projektu** , kliknij dwukrotnie ikonę **mój projekt** w **Eksplorator rozwiązań**.  
  
 **Identyfikator błędu:** BC40057  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Otwórz **projektanta projektu** i przejdź do strony **referencyjnej** .  
  
2. W sekcji **zaimportowane przestrzenie nazw** Sprawdź, czy element zawierający jest dostępny z projektu.  
  
3. Sprawdź, czy zawierający element uwidacznia co najmniej jeden `Public` element członkowski.  
  
## <a name="see-also"></a>Zobacz też

- [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
- [Społeczeństwo](../modifiers/public.md)
- [Przestrzenie nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Odwołania do elementów zadeklarowanych](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
