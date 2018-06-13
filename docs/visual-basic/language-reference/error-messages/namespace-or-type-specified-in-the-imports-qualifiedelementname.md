---
title: Namespace lub typ określony w elemencie Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawierają żadnego członka publicznego lub nie można odnaleźć
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8be0df5cbe4b8d4a640c9b6c2e126b3828254fd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595108"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace lub typ określony w elemencie Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawierają żadnego członka publicznego lub nie można odnaleźć
Namespace lub typ określony w elemencie Imports\<qualifiedelementname >' nie zawierają żadnego członka publicznego lub nie można odnaleźć. Upewnij się, że przestrzeń nazw lub typ są zdefiniowane i zawierają co najmniej jednego członka publicznego. Upewnij się, że nazwa aliasu nie zawiera innych aliasów.  
  
 `Imports` Instrukcji określa zawierający element, który nie może być odnaleziona albo nie definiuje `Public` elementów członkowskich.  
  
 A *zawierającego element* może być w przestrzeni nazw, klasy, struktury, modułu, interfejsu lub wyliczenia. Element zawierający zawiera członków, takie jak zmienne, procedury i innych elementów zawierających.  
  
 Importowanie celem jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez konieczności ich kwalifikacji. Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne. Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Jeśli kompilator nie może znaleźć określonego elementu zawierającego, nie można go rozpoznać odwołań, które go używają. Jeśli znajdzie elementu, ale element nie ujawnia żadnego `Public` elementy członkowskie, a następnie odwołania nie mogą być skutecznie. W obu przypadkach jest bez znaczenia, aby zaimportować element.  
  
 Należy pamiętać, że Jeśli zaimportujesz zawierający element, a następnie przypisać aliasu importu, następnie nie umożliwia tego aliasu importu zaimportować innego elementu. Poniższy kod generuje błąd kompilatora.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **Identyfikator błędu:** BC40056  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy zawierającego element jest dostępny z projektu.  
  
2.  Sprawdź, czy specyfikację elementu zawierającego nie zawiera żadnych aliasu importu z innego importu.  
  
3.  Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
