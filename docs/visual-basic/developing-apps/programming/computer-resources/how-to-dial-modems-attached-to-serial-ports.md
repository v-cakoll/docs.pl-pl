---
title: 'Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52540ea2962fd6619b205694c444557c283c32e9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` do nawiązywania połączenia z modemem w języku Visual Basic.  
  
 Zazwyczaj modem jest podłączony do jednego z portów szeregowych na komputerze. Aplikacji do komunikowania się z modemu jej wysyłać polecenia do właściwego portu szeregowego.  
  
### <a name="to-dial-a-modem"></a>Aby wybrać modemu  
  
1.  Określ, które portu szeregowego modem jest podłączony do. W tym przykładzie przyjęto założenie, że jest na COM1.  
  
2.  Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołania do portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Bloku umożliwia zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który manipuluje portu szeregowego powinien pojawić się w tym bloku lub poziomu `Try...Catch...Finally` bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Ustaw `DtrEnable` właściwości, aby wskazać, że komputer jest gotowy do akceptowania przychodzących transmisji z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Wysyłanie polecenia wybierania i numer telefonu z modemem za pośrednictwem portu szeregowego za pomocą klasy <xref:System.IO.Ports.SerialPort.Write%2A> metody.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **sieć i łączność**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do <xref:System?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie przyjęto założenie, że modem jest podłączony do COM1. Firma Microsoft zaleca kodu pozwala na wybierz żądany port szeregowy z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [porady: portów seryjnych dostępne Pokaż](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie użyto `Using` bloku, aby się upewnić, że aplikacja zamyka port, nawet jeśli zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 W tym przykładzie aplikacja rozłącza portu szeregowego po wywoływaniu modemu. Realistycznie rzecz biorąc można na przesyłanie danych do i z modemu. Aby uzyskać więcej informacji, zobacz [porady: odbieranie ciągów z portów szeregowych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Instrukcje: wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Instrukcje: odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [Instrukcje: wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
