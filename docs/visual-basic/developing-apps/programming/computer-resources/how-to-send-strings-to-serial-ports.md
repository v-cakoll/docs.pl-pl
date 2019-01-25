---
title: 'Instrukcje: Wysyłanie ciągów do portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2ba25f4ca3f63e1e7831d26745fa35cd337dc48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503030"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Instrukcje: Wysyłanie ciągów do portów seryjnych w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` na wysyłanie ciągów do portów szeregowych komputera w języku Visual Basic.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wysyła ciąg do portu szeregowego COM1. Może być konieczne użycie innego portu szeregowego na tym komputerze.  
  
 Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołanie do tego portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using` Bloku zezwala aplikacji na zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który obsługuje portu szeregowego, powinna zostać wyświetlona w ramach tego bloku lub w ramach `Try...Catch...Finally` bloku.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> Metoda wysyła dane do portu szeregowego.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   W tym przykładzie przyjęto założenie, komputer używa `COM1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie przyjęto założenie, komputer używa `COM1`; większej elastyczności, kod powinien pozwalać użytkownikowi wybrać odpowiedni port szeregowy z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie użyto `Using` bloku, aby upewnić się, że aplikacja zamyka port, nawet wtedy, gdy występuje wyjątek. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: Modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
