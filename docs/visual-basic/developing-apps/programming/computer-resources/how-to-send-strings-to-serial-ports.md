---
title: 'Instrukcje: wysyłanie ciągów do portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: f78df9cf1bd75432ea645c4dcc06498915ceee49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360296"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Porady: wysyłanie ciągów do portów seryjnych w Visual Basic

W tym temacie opisano, jak za pomocą `My.Computer.Ports` programu wysyłać ciągi do portów szeregowych komputera w Visual Basic.  
  
## <a name="example"></a>Przykład  

 Ten przykład wysyła ciąg do portu szeregowego COM1. Może być konieczne użycie innego portu szeregowego na komputerze.  
  
 Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using`Blok umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku lub w `Try...Catch...Finally` bloku.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A>Metoda wysyła dane do portu szeregowego.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- W tym przykładzie przyjęto założenie, że komputer korzysta z programu `COM1` .  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 W tym przykładzie przyjęto założenie, że komputer jest używany `COM1` ; w celu uzyskania większej elastyczności kod powinien zezwalać użytkownikowi na wybranie żądanego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](how-to-show-available-serial-ports.md).  
  
 W tym przykładzie używa `Using` bloku, aby upewnić się, że aplikacja zamknie port nawet wtedy, gdy zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: modemy dostępowe powiązane z portami seryjnymi](how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: wyświetlanie dostępnych portów seryjnych](how-to-show-available-serial-ports.md)
