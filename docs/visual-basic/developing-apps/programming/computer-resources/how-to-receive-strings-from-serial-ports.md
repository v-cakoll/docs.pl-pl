---
title: 'Instrukcje: Odbieranie ciągów z portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 9c5fc0e9ddd42543d2f1e0b92c818b22909d50d7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971666"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Instrukcje: Odbieranie ciągów z portów seryjnych w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` na odbieranie ciągów z portów szeregowych komputera w języku Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Aby odbieranie ciągów z portu szeregowego  
  
1.  Inicjuje ciąg zwracany.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2.  Określ port szeregowy, który powinien zapewnić ciągi. W tym przykładzie przyjęto założenie, jest `COM1`.  
  
3.  Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołanie do tego portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Bloku zezwala aplikacji na zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który obsługuje portu szeregowego powinna zostać wyświetlona w ramach tego bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4.  Utwórz `Do` pętli do odczytywania wierszy tekstu, dopóki nie ma więcej wierszy są dostępne.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5.  Użyj <xref:System.IO.Ports.SerialPort.ReadLine> metodę w celu odczytania następnego dostępnego wiersza tekstu z portu szeregowego.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6.  Użyj `If` instrukcję, aby określić, czy <xref:System.IO.Ports.SerialPort.ReadLine> metoda zwraca `Nothing` (co oznacza brak więcej tekstu jest dostępna). Jeśli jest on zwrócić `Nothing`, Zamknij `Do` pętli.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7.  Dodaj `Else` za pomocą bloku `If` instrukcję, aby obsłużyć przypadek, jeśli ciąg jest faktycznie do odczytu. Blok dołącza ciąg z portu szeregowego do zwracanego ciągu.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8.  Zwraca ciąg.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
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
