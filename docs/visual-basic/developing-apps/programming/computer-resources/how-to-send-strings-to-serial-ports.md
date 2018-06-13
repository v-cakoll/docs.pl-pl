---
title: 'Porady: wysyłanie ciągów do portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: a00306407cfe880ebc915d74a753109cc9696f6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584030"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Porady: wysyłanie ciągów do portów seryjnych w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` na wysyłanie ciągów do portów szeregowych komputera w języku Visual Basic.  
  
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
 [Instrukcje: modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Instrukcje: wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
