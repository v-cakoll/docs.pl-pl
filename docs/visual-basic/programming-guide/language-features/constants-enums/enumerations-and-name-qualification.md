---
title: Wyliczenie i kwantyfikacja nazwy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 0336ac54c6a0dadeb9758bcb15477fe96dbfcc65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513701"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Wyliczenie i kwantyfikacja nazwy (Visual Basic)
Zwykle przy odwoływaniu się do elementu członkowskiego wyliczenia, masz prawo nazwę elementu członkowskiego o nazwie wyliczenia. Na przykład, aby odwołać się do `Sunday` członek Twojego `Days` wyliczenia, należy użyć następującej składni:  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Za pomocą Importy — instrukcja  
 Możesz uniknąć używania w pełni kwalifikowanych nazw, dodając `Imports` instrukcję do sekcji deklaracji przestrzeni nazw w kodzie, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports` Instrukcja importuje nazwy przestrzeni nazw z przywoływane projekty i zespoły i w tym samym projekcie jako moduł, w której występuje instrukcja. Po dodaniu tej instrukcji, możesz zapoznać się z elementów członkowskich wyliczenia bez kwalifikacji, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Organizując zestawów powiązanych stałe wyliczeń, można użyć takich samych nazwach stałej w różnych kontekstach. Na przykład, można użyć tej samej nazwy dla stałych dzień tygodnia, w `Days` i `WorkDays` wyliczenia. Jeśli używasz `Imports` instrukcji związanych z wyliczeniami usługi, należy uważać, aby uniknąć niejednoznacznego odwołania. Rozważmy następujący przykład:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Przy założeniu, że `Monday` jest elementem członkowskim `Days` wyliczenie i `Workdays` wyliczenia, ten kod generuje błąd kompilatora. Aby uniknąć niejednoznacznych odwołań przy odwoływaniu się do poszczególnych stałą, kwalifikują się stałe nazwą jego wyliczenia. Poniższy kod, który odwołuje się do `Saturday` stałe w `Days` i `WorkDays` wyliczenia.  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Instrukcje: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
