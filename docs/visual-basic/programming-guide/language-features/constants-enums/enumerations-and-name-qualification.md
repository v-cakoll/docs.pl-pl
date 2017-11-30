---
title: Wyliczenie i kwantyfikacja nazwy (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb97d6a8f4b7e81f2b759010214e200ec63ff21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Wyliczenie i kwantyfikacja nazwy (Visual Basic)
Zwykle podczas odwoływania się do elementu członkowskiego wyliczenia, muszą kwalifikować się nazwę elementu członkowskiego o nazwie wyliczenia. Na przykład, aby odwołać się do `Sunday` członka Twojej `Days` wyliczenia, należy użyć następującej składni:  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Przy użyciu Importy — instrukcja  
 Możesz uniknąć używania w pełni kwalifikowane nazwy przez dodanie `Imports` instrukcji w sekcji deklaracji przestrzeni nazw kodu, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports` Instrukcji imports nazwy przestrzeni nazw z przywoływane projekty i zestawy, a za pomocą tego samego projektu jako moduł, w której występuje instrukcja. Po dodaniu tej instrukcji można odwołać się do członków wyliczenia bez kwalifikacji, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Poprzez organizowanie zestawów powiązanych stałe w wyliczenia, można użyć tych samych nazw stałej w różnych kontekstach. Na przykład można użyć tych samych nazw stałe dzień tygodnia w `Days` i `WorkDays` wyliczenia. Jeśli używasz `Imports` instrukcji z Twojej wyliczenia, należy zachować ostrożność uniknąć niejednoznacznych odwołań. Rozważmy następujący przykład:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Przy założeniu, że `Monday` jest elementem członkowskim `Days` wyliczenie i `Workdays` wyliczenia, ten kod generowany jest błąd kompilatora. Aby uniknąć niejednoznacznych odwołań podczas odwoływania się do poszczególnych stała, Zakwalifikuj nazwę przez stałej z jego wyliczenia. Poniższy kod odwołuje się do `Saturday` stałe w `Days` i `WorkDays` wyliczenia.  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Porady: odwołuje się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Porady: iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Porady: Określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Stała i typy literałów](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Enum — instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Imports — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
