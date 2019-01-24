---
title: 'Instrukcje: Odbieranie ciągów z portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: f87ff7e621d241a94dae444bc156502ee86b36b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521611"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Instrukcje: Odbieranie ciągów z portów seryjnych w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` na odbieranie ciągów z portów szeregowych komputera w języku Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Aby odbieranie ciągów z portu szeregowego  
  
1.  Inicjuje ciąg zwracany.  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  Określ port szeregowy, który powinien zapewnić ciągi. W tym przykładzie przyjęto założenie, jest `COM1`.  
  
3.  Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołanie do tego portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Bloku zezwala aplikacji na zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który obsługuje portu szeregowego powinna zostać wyświetlona w ramach tego bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  Utwórz `Do` pętli do odczytywania wierszy tekstu, dopóki nie ma więcej wierszy są dostępne.  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  Użyj <xref:System.IO.Ports.SerialPort.ReadLine> metodę w celu odczytania następnego dostępnego wiersza tekstu z portu szeregowego.  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  Użyj `If` instrukcję, aby określić, czy <xref:System.IO.Ports.SerialPort.ReadLine> metoda zwraca `Nothing` (co oznacza brak więcej tekstu jest dostępna). Jeśli jest on zwrócić `Nothing`, Zamknij `Do` pętli.  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  Dodaj `Else` za pomocą bloku `If` instrukcję, aby obsłużyć przypadek, jeśli ciąg jest faktycznie do odczytu. Blok dołącza ciąg z portu szeregowego do zwracanego ciągu.  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  Zwraca ciąg.  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie przyjęto założenie, komputer używa `COM1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie przyjęto założenie, komputer używa `COM1`. W celu zwiększenia elastyczności kod powinien pozwalać użytkownikowi wybrać odpowiedni port szeregowy z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie użyto `Try...Catch...Finally` bloku, aby upewnić się, że aplikacja zostanie zamknięty port i przechwycić wyjątków przekroczenia limitu czasu. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: Modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: Wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
