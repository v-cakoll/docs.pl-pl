---
title: 'Porady: wysyłanie ciągów do portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2051451142a7818a3b7d1bc564c5ae36b2579fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345585"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Porady: wysyłanie ciągów do portów seryjnych w Visual Basic

W tym temacie opisano, jak za pomocą `My.Computer.Ports` wysyłać ciągi do portów szeregowych komputera w Visual Basic.  
  
## <a name="example"></a>Przykład  

 Ten przykład wysyła ciąg do portu szeregowego COM1. Może być konieczne użycie innego portu szeregowego na komputerze.  
  
 Użyj metody `My.Computer.Ports.OpenSerialPort`, aby uzyskać odwołanie do portu. Aby uzyskać więcej informacji, zobacz temat <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 Blok `Using` umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku lub w bloku `Try...Catch...Finally`.  
  
 Metoda <xref:System.IO.Ports.SerialPort.WriteLine%2A> wysyła dane do portu szeregowego.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- W tym przykładzie przyjęto założenie, że komputer używa `COM1`.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  

 W tym przykładzie przyjęto założenie, że komputer używa `COM1`; Aby zapewnić większą elastyczność, kod powinien zezwalać użytkownikowi na wybranie żądanego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie używa bloku `Using`, aby upewnić się, że aplikacja zamknie port nawet wtedy, gdy zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
