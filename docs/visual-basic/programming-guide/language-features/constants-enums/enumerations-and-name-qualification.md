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
ms.openlocfilehash: f0a806b040720cf6682f8a72025a0590dd4d91f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818439"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Wyliczenie i kwantyfikacja nazwy (Visual Basic)
Zwykle przy odwoływaniu się do elementu członkowskiego wyliczenia, masz prawo nazwę elementu członkowskiego o nazwie wyliczenia. Na przykład, aby odwołać się do `Sunday` członek Twojego `Days` wyliczenia, należy użyć następującej składni:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Za pomocą Importy — instrukcja  
 Możesz uniknąć używania w pełni kwalifikowanych nazw, dodając `Imports` instrukcję do sekcji deklaracji przestrzeni nazw w kodzie, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 `Imports` Instrukcja importuje nazwy przestrzeni nazw z przywoływane projekty i zespoły i w tym samym projekcie jako moduł, w której występuje instrukcja. Po dodaniu tej instrukcji, możesz zapoznać się z elementów członkowskich wyliczenia bez kwalifikacji, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Organizując zestawów powiązanych stałe wyliczeń, można użyć takich samych nazwach stałej w różnych kontekstach. Na przykład, można użyć tej samej nazwy dla stałych dzień tygodnia, w `Days` i `WorkDays` wyliczenia. Jeśli używasz `Imports` instrukcji związanych z wyliczeniami usługi, należy uważać, aby uniknąć niejednoznacznego odwołania. Rozważmy następujący przykład:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Przy założeniu, że `Monday` jest elementem członkowskim `Days` wyliczenie i `Workdays` wyliczenia, ten kod generuje błąd kompilatora. Aby uniknąć niejednoznacznych odwołań przy odwoływaniu się do poszczególnych stałą, kwalifikują się stałe nazwą jego wyliczenia. Poniższy kod, który odwołuje się do `Saturday` stałe w `Days` i `WorkDays` wyliczenia.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
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
