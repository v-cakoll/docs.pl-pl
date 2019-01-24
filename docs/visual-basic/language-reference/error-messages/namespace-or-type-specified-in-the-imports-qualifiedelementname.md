---
title: Namespace lub typ określony w elemencie Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawiera żadnej publicznej składowej lub nie można odnaleźć
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 21c0794fb4ed6104204fba5d49e37394eff24865
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552141"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace lub typ określony w elemencie Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawiera żadnej publicznej składowej lub nie można odnaleźć
Namespace lub typ określony w elemencie Imports\<qualifiedelementname >' nie zawiera żadnej publicznej składowej lub nie można odnaleźć. Upewnij się, że przestrzeń nazw lub typ zostały zdefiniowane i zawierają co najmniej jednego członka publicznego. Upewnij się, że nazwa aliasu nie zawiera innych aliasów.  
  
 `Imports` Instrukcja określa element zawierający, która nie może być odnaleziona lub nie definiuje `Public` elementów członkowskich.  
  
 A *zawierającego element* może być przestrzeni nazw, klasy, struktury, moduł, interfejs lub wyliczenie. Element zawierający zawiera składniki, takie jak zmienne, procedury lub inne elementy zawierające.  
  
 Celem importowania jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez ich kwalifikowania. Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne. Aby uzyskać więcej informacji, zobacz "Importowanie zawierający elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Jeśli kompilator nie może znaleźć określony element zawierający, nie można go rozpoznać odwołania, które go używają. W przypadku znalezienia elementu, ale nie ujawnia na dowolny element `Public` elementów członkowskich, a następnie Brak odwołania może odnieść sukces. W obu przypadkach jest bez znaczenia, aby zaimportować element.  
  
 Należy pamiętać, że jeśli import — element zawierający i przypisać aliasu importu, następnie nie możesz użyć tego aliasu importu można zaimportować innego elementu. Poniższy kod generuje błąd kompilatora.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **Identyfikator błędu:** BC40056  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy element zawierający jest dostępny z projektu.  
  
2.  Sprawdź specyfikację elementu zawierającą nie zawiera żadnych aliasu importu z innego importu.  
  
3.  Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz także
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Przestrzenie nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
