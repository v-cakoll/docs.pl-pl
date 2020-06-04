---
title: 'Instrukcje: modemy dostępowe powiązane z portami seryjnymi'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: e55ce6399dae435fbd5b2f730d4d0848c98d8955
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363270"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic

W tym temacie opisano sposób użycia `My.Computer.Ports` programu do nawiązywania połączenia z modemem w Visual Basic.  
  
 Zwykle modem jest podłączony do jednego z portów szeregowych na komputerze. Aby aplikacja mogła komunikować się z modemem, musi wysłać polecenia do odpowiedniego portu szeregowego.  
  
### <a name="to-dial-a-modem"></a>Aby nawiązać połączenie z modemem  
  
1. Określ port szeregowy, z którym jest połączony modem. W tym przykładzie przyjęto założenie, że modem jest na COM1.  
  
2. Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using`Blok umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku lub w `Try...Catch...Finally` bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Ustaw `DtrEnable` Właściwość, aby wskazać, że komputer jest gotowy do akceptowania przychodzącej transmisji z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Wyślij polecenie wybierania numeru i numer telefonu do modemu przez port szeregowy przy użyciu <xref:System.IO.Ports.SerialPort.Write%2A> metody.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Ten przykład wymaga odwołania do <xref:System?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 W tym przykładzie przyjęto założenie, że modem jest połączony z COM1. Zalecamy, aby Twój kod umożliwiał użytkownikowi wybranie żądanego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](how-to-show-available-serial-ports.md).  
  
 W tym przykładzie używa `Using` bloku, aby upewnić się, że aplikacja zamknie port nawet wtedy, gdy zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../language-reference/statements/using-statement.md).  
  
 W tym przykładzie aplikacja rozłącza port szeregowy po nawiązaniu połączenia z modemem. Realistycznie można przesłać dane do i z modemu. Aby uzyskać więcej informacji, zobacz [jak to zrobić: otrzymywanie ciągów z portów seryjnych](how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: wysyłanie ciągów do portów seryjnych](how-to-send-strings-to-serial-ports.md)
- [Instrukcje: odbieranie ciągów z portów seryjnych](how-to-receive-strings-from-serial-ports.md)
- [Instrukcje: wyświetlanie dostępnych portów seryjnych](how-to-show-available-serial-ports.md)
