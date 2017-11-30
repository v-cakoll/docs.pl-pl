---
title: "Porady: wysyłanie ciągów do portów seryjnych w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95c67b344572d21f418cbc14d350e6ff28611bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Porady: wysyłanie ciągów do portów seryjnych w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` na wysyłanie ciągów do portów szeregowych komputera w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wysyła ciąg do portu szeregowego COM1. Może być konieczne użycie innego portu szeregowego na tym komputerze.  
  
 Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołania do portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using` Bloku umożliwia zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który manipuluje portu szeregowego powinien pojawić się w tym bloku lub poziomu `Try...Catch...Finally` bloku.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> Metoda wysyła dane do portu szeregowego.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   W tym przykładzie założono komputer korzysta z `COM1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie założono komputer korzysta z `COM1`; w celu zapewnienia większej elastyczności, kod pozwolić użytkownikowi na wybranie wybranego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [porady: portów seryjnych dostępne Pokaż](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie użyto `Using` bloku, aby się upewnić, że aplikacja zamyka port, nawet jeśli zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Porady: modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Porady: wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
