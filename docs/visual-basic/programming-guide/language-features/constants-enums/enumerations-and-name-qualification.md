---
title: Wyliczenie i kwantyfikacja nazwy
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
ms.openlocfilehash: 4121266447b771ba954ad52a46e0d8b88de3f9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347495"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Wyliczenie i kwantyfikacja nazwy (Visual Basic)
Zwykle w przypadku odwoływania się do elementu członkowskiego wyliczenia należy zakwalifikować nazwę elementu członkowskiego o nazwie wyliczenia. Na przykład, aby odwołać się do `Sunday` elementu członkowskiego wyliczenia `Days`, należy użyć następującej składni:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Korzystanie z instrukcji Imports  
 Można uniknąć używania w pełni kwalifikowanych nazw przez dodanie instrukcji `Imports` do sekcji deklaracji przestrzeni nazw kodu, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 Instrukcja `Imports` importuje nazwy przestrzeni nazw z przywoływanych projektów i zestawów oraz z tego samego projektu, co moduł, w którym znajduje się instrukcja. Po dodaniu tej instrukcji można odwołać się do członków wyliczenia bez kwalifikacji, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Organizując zestawy powiązanych stałych w wyliczeniach, można użyć tych samych stałych nazw w różnych kontekstach. Na przykład można użyć tych samych nazw dla stałych dni tygodnia w `Days` i `WorkDays` wyliczeń. Jeśli używasz instrukcji `Imports` z wyliczeniami, musisz zachować ostrożność, aby uniknąć niejednoznacznych odwołań. Rozważmy następujący przykład:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Przy założeniu, że `Monday` jest członkiem zarówno wyliczenia `Days`, jak i wyliczenia `Workdays`, ten kod generuje błąd kompilatora. Aby uniknąć niejednoznacznych odwołań podczas odwoływania się do pojedynczej stałej, należy zakwalifikować stałą nazwę z wyliczeniem. Poniższy kod odnosi się do `Saturday` stałych w wyliczeniach `Days` i `WorkDays`.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Zobacz także

- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Instrukcje: deklarowanie wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Instrukcje: Iterowanie przez Wyliczenie w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
