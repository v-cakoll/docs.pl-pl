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
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414508"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Wyliczenie i kwantyfikacja nazwy (Visual Basic)
Zwykle w przypadku odwoływania się do elementu członkowskiego wyliczenia należy zakwalifikować nazwę elementu członkowskiego o nazwie wyliczenia. Na przykład, aby odwołać się do `Sunday` elementu członkowskiego `Days` wyliczenia, należy użyć następującej składni:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Korzystanie z instrukcji Imports  
 Można uniknąć używania w pełni kwalifikowanych nazw, dodając `Imports` instrukcję do sekcji deklaracji przestrzeni nazw kodu, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 `Imports`Instrukcja importuje nazwy przestrzeni nazw z przywoływanych projektów i zestawów oraz z tego samego projektu, co moduł, w którym znajduje się instrukcja. Po dodaniu tej instrukcji można odwołać się do członków wyliczenia bez kwalifikacji, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Organizując zestawy powiązanych stałych w wyliczeniach, można użyć tych samych stałych nazw w różnych kontekstach. Na przykład można użyć tych samych nazw dla stałych dni tygodnia w `Days` `WorkDays` wyliczeniach i. Jeśli używasz `Imports` instrukcji z wyliczeniami, należy zachować ostrożność, aby uniknąć niejednoznacznych odwołań. Rozpatrzmy następujący przykład:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Przy założeniu `Monday` , że jest składową zarówno `Days` wyliczenia, jak i `Workdays` wyliczenia, ten kod generuje błąd kompilatora. Aby uniknąć niejednoznacznych odwołań podczas odwoływania się do pojedynczej stałej, należy zakwalifikować stałą nazwę z wyliczeniem. Poniższy kod odwołuje się do `Saturday` stałych w `Days` `WorkDays` wyliczeniach i.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Zobacz też

- [Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)
- [Instrukcje: deklarowanie wyliczenia](how-to-declare-enumerations.md)
- [Porady: odwoływanie się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md)
- [Porady: iterowanie za pomocą wyliczania w Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)
- [Stała i typy literałów](constant-and-literal-data-types.md)
- [Enum, instrukcja](../../../language-reference/statements/enum-statement.md)
- [Imports — Instrukcja (.NET Namespace i Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Typy danych](../../../language-reference/data-types/index.md)
