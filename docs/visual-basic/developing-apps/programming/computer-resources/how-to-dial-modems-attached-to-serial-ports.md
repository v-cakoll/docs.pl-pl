---
title: 'Porady: modemy dostępowe powiązane z portami seryjnymi'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345638"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic

W tym temacie `My.Computer.Ports` opisano sposób wybierania numeru modemu w języku Visual Basic.  
  
 Zazwyczaj modem jest podłączony do jednego z portów szeregowych na komputerze. Aby aplikacja komunikuje się z modemem, musi wysyłać polecenia do odpowiedniego portu szeregowego.  
  
### <a name="to-dial-a-modem"></a>Aby wybrać modem  
  
1. Określ, do którego portu szeregowego jest podłączony modem. W tym przykładzie przyjęto założenie, że modem jest na COM1.  
  
2. Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Blok `Using` umożliwia aplikacji, aby zamknąć port szeregowy, nawet jeśli generuje wyjątek. Cały kod, który manipuluje portem szeregowym `Try...Catch...Finally` powinny pojawić się w tym bloku lub w bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Ustaw `DtrEnable` właściwość, aby wskazać, że komputer jest gotowy do zaakceptowania przychodzącej transmisji z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Wyślij polecenie wybierania numeru i numer telefonu do modemu <xref:System.IO.Ports.SerialPort.Write%2A> za pośrednictwem portu szeregowego za pomocą metody.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **sekcji Łączność i sieć**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 W tym przykładzie <xref:System?displayProperty=nameWithType> wymaga odwołania do obszaru nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 W tym przykładzie przyjęto założenie, że modem jest podłączony do com1. Zaleca się, aby kod umożliwiał użytkownikowi wybranie żądanego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [Jak: Pokaż dostępne porty szeregowe](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie `Using` użyto bloku, aby upewnić się, że aplikacja zamyka port, nawet jeśli zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [Korzystanie z instrukcji](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 W tym przykładzie aplikacja rozłącza port szeregowy po wybraniu modemu. Realistycznie, będziesz chciał przesyłać dane do i z modemu. Aby uzyskać więcej informacji, zobacz [Jak: Odbieranie ciągów z portów szeregowych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Instrukcje: wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
