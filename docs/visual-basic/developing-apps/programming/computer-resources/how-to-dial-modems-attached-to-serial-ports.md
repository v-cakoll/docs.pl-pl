---
title: 'Porady: modemy dostępowe powiązane z portami seryjnymi'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345638"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic

W tym temacie opisano sposób użycia `My.Computer.Ports` do nawiązywania połączenia z modemem w programie Visual Basic.  
  
 Zwykle modem jest podłączony do jednego z portów szeregowych na komputerze. Aby aplikacja mogła komunikować się z modemem, musi wysłać polecenia do odpowiedniego portu szeregowego.  
  
### <a name="to-dial-a-modem"></a>Aby nawiązać połączenie z modemem  
  
1. Określ port szeregowy, z którym jest połączony modem. W tym przykładzie przyjęto założenie, że modem jest na COM1.  
  
2. Użyj metody `My.Computer.Ports.OpenSerialPort`, aby uzyskać odwołanie do portu. Aby uzyskać więcej informacji, zobacz temat <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Blok `Using` umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku lub w bloku `Try...Catch...Finally`.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Ustaw właściwość `DtrEnable` tak, aby wskazywała, że komputer jest gotowy do akceptowania przychodzącej transmisji z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Wyślij polecenie wybierania numeru i numer telefonu do modemu przez port szeregowy za pomocą metody <xref:System.IO.Ports.SerialPort.Write%2A>.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Ten przykład wymaga odwołania do przestrzeni nazw <xref:System?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  

 W tym przykładzie przyjęto założenie, że modem jest połączony z COM1. Zalecamy, aby Twój kod umożliwiał użytkownikowi wybranie żądanego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie używa bloku `Using`, aby upewnić się, że aplikacja zamknie port nawet wtedy, gdy zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 W tym przykładzie aplikacja rozłącza port szeregowy po nawiązaniu połączenia z modemem. Realistycznie można przesłać dane do i z modemu. Aby uzyskać więcej informacji, zobacz [jak to zrobić: otrzymywanie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Instrukcje: wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
