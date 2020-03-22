---
title: 'Porady: odbieranie ciągów z portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345595"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Porady: odbieranie ciągów z portów seryjnych w Visual Basic

W tym temacie `My.Computer.Ports` opisano sposób odbierania ciągów z portów szeregowych komputera w języku Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Aby odbierać ciągi z portu szeregowego  
  
1. Zainicjować ciąg zwrotny.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Określ, który port szeregowy powinien dostarczać ciągi. W tym przykładzie `COM1`przyjęto założenie, że jest .  
  
3. Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Blok `Try...Catch...Finally` umożliwia aplikacji, aby zamknąć port szeregowy, nawet jeśli generuje wyjątek. Cały kod, który manipuluje portem szeregowym powinny pojawić się w tym bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Utwórz `Do` pętlę do czytania wierszy tekstu, dopóki nie będzie dostępnych więcej wierszy.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Użyj <xref:System.IO.Ports.SerialPort.ReadLine> tej metody, aby odczytać następny dostępny wiersz tekstu z portu szeregowego.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. Użyj `If` instrukcji, aby <xref:System.IO.Ports.SerialPort.ReadLine> ustalić, `Nothing` czy metoda zwraca (co oznacza, że nie ma więcej tekstu). Jeśli `Nothing`powróci, wyjdź z `Do` pętli.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Dodaj `Else` blok do `If` instrukcji do obsługi sprawy, jeśli ciąg jest rzeczywiście odczytywany. Blok dołącza ciąg z portu szeregowego do ciągu zwracany.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Zwraca ciąg.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **sekcji Łączność i sieć**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 W tym przykładzie przyjęto założenie, że komputer jest używany `COM1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 W tym przykładzie przyjęto założenie, że komputer jest używany `COM1`. Aby uzyskać większą elastyczność, kod powinien umożliwić użytkownikowi wybranie żądanego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [Jak: Pokaż dostępne porty szeregowe](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 W tym przykładzie `Try...Catch...Finally` użyto bloku, aby upewnić się, że aplikacja zamyka port i przechwytują wszelkie wyjątki limitu czasu. Aby uzyskać więcej informacji, zobacz [Try... Złapać... Wreszcie Oświadczenie](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
