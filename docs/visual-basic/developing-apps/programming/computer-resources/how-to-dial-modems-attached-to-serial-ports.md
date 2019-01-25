---
title: 'Instrukcje: Modemy dostępowe powiązane z portami seryjnymi w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db99f94d27235a7c9dca4fc5339854a39147b585
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490616"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Instrukcje: Modemy dostępowe powiązane z portami seryjnymi w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` należy regulować w modem w języku Visual Basic.  
  
 Zazwyczaj modem jest podłączony do jednego z portów szeregowych na komputerze. Dla aplikacji do komunikowania się za pomocą modemu jest w stanie wysyłać polecenia do odpowiedniego portu szeregowego.  
  
### <a name="to-dial-a-modem"></a>Aby wybrać modemu  
  
1.  Określ, które portu szeregowego, modem jest podłączony do. W tym przykładzie przyjęto założenie, że jest na COM1.  
  
2.  Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołanie do tego portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Bloku zezwala aplikacji na zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który obsługuje portu szeregowego, powinna zostać wyświetlona w ramach tego bloku lub w ramach `Try...Catch...Finally` bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Ustaw `DtrEnable` właściwości, aby wskazać, że komputer jest gotowy do akceptowania przychodzących transmisji z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Wyślij polecenie wybierania i numer telefonu z modemem za pośrednictwem portu szeregowego przez <xref:System.IO.Ports.SerialPort.Write%2A> metody.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do <xref:System?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie przyjęto założenie, że modem jest podłączony do portu COM1. Zaleca się, że kod umożliwia użytkownikowi wybrać odpowiedni port szeregowy z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie użyto `Using` bloku, aby upewnić się, że aplikacja zamyka port, nawet wtedy, gdy występuje wyjątek. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 W tym przykładzie aplikacja odłącza portu szeregowego, po wywoływaniu modemu. Realistycznie rzecz biorąc należy przenieść dane do i z modemu. Aby uzyskać więcej informacji, zobacz [jak: Odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: Wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: Odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Instrukcje: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
