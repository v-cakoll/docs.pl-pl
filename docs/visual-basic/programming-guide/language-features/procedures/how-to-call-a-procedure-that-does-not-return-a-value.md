---
title: "Porady: wywoływanie procedury, która nie zwraca wartości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbea50132d1110b38bf9b01397795a2cd51f86d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Porady: wywoływanie procedury, która nie zwraca wartości (Visual Basic)
A `Sub` procedury nie zwraca wartości do wywołującego kodu. Należy wywołać ją jawnie autonomicznej instrukcją wywołującego. Nie można wywołać go, używając po prostu swojej nazwy w wyrażeniu.  
  
### <a name="to-call-a-sub-procedure"></a>Aby wywołać procedurę Sub  
  
1.  Określ nazwę `Sub` procedury.  
  
2.  Po nazwie procedury nawiasami ujmij listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów. Jednak za pomocą nawiasów ułatwia kodu do odczytu.  
  
3.  Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty. Należy podać argumenty w tej samej kolejności, która `Sub` procedury definiuje odpowiednich parametrów.  
  
     Następujące przykładowe wywołania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkcji, aby aktywować okna aplikacji. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>pobiera tytuł okna jako jedynego argumentu. Zwraca wartość do wywołującego kodu. Jeśli nie jest uruchomiony proces Notatnik, zgłasza przykładzie <xref:System.ArgumentException>. `Shell` Procedurze przyjęto założenie, znajdują się w określonej ścieżce.  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [Procedury](./index.md)  
 [Sub — procedury](./sub-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Porady: Tworzenie procedury](./how-to-create-a-procedure.md)  
 [Porady: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)  
 [Porady: wywoływanie procedury obsługi zdarzeń w Visual Basic](./how-to-call-an-event-handler.md)
