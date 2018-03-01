---
title: Nazwa &#39; &lt;nazwa&gt;&#39; nie jest zadeklarowana
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a63ae74c7179d71756e2b9b4bf6b41a71ce12a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Nazwa &#39; &lt;nazwa&gt;&#39; nie jest zadeklarowana
Oświadczenie odnosi się do elementu programistycznego, ale kompilator nie można odnaleźć elementu o takiej samej nazwie.  
  
 **Identyfikator błędu:** BC30451  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź pisownię nazwy w instrukcji zawierających odwołania. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]nie uwzględnia wielkości liter, ale inne zmiany w pisowni jest traktowany jako całkowicie inną nazwę. Należy pamiętać, że znak podkreślenia (`_`) jest częścią nazwy, a w związku z tym częścią pisowni.  
  
2.  Sprawdź, czy masz operatora dostępu do elementu członkowskiego (`.`) między obiektem i jego elementów członkowskich. Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formantu o nazwie `TextBox1`, aby uzyskać dostęp do jego <xref:System.Windows.Forms.TextBoxBase.Text%2A> właściwości, należy wpisać `TextBox1.Text`. Jeśli zamiast tego wpisz `TextBox1Text`, utworzono inną nazwę.  
  
3.  Jeśli pisownia jest poprawna oraz składni dostępu do dowolnego obiektu elementu członkowskiego jest poprawny, sprawdź, czy element został zadeklarowany. Aby uzyskać więcej informacji, zobacz [zadeklarowane elementy](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Jeśli programowania element został zadeklarowany, sprawdź, czy znajduje się w zakresie. W przypadku instrukcji odwołujących się poza obszarem deklarowanie elementu programistycznego, konieczne może być nazwy elementu. Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i stałe — podsumowanie](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
