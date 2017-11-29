---
title: "Porady: uruchamianie aplikacji i wysyłanie do niej uderzeń w klawisze (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bf92a74bc1b60ea3213d80e4df373936c65d89e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Porady: uruchamianie aplikacji i wysyłanie do niej uderzeń w klawisze (Visual Basic)
W tym przykładzie użyto `Shell` działać do uruchomienia aplikacji Kalkulator, a następnie mnoży dwie liczby wysyła naciśnięcia klawiszy `My.Computer.Keyboard.SendKeys` metody.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 A <xref:System.ArgumentException> wyjątek jest zgłaszany, jeśli nie można odnaleźć aplikacji przy użyciu identyfikatora procesu żądanej.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywołanie `Shell` funkcja wymaga pełnego zaufania (<xref:System.Security.SecurityException> klasy).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
