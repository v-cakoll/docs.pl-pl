---
title: 'Instrukcje: odbieranie ciągów z portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 93b6b47d89d05331c85a6459bba7d6fd5e2e3377
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401839"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Porady: odbieranie ciągów z portów seryjnych w Visual Basic

W tym temacie opisano, jak używać `My.Computer.Ports` programu do odbierania ciągów z portów szeregowych komputera w Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Aby odbierać ciągi z portu szeregowego  
  
1. Zainicjuj ciąg Return.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Ustal, który port szeregowy powinien dostarczać ciągi. W tym przykładzie założono, że jest to `COM1` .  
  
3. Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally`Blok umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek. Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Utwórz `Do` pętlę do czytania wierszy tekstu, dopóki nie będzie dostępnych więcej wierszy.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Użyj <xref:System.IO.Ports.SerialPort.ReadLine> metody, aby odczytać następny dostępny wiersz tekstu z portu szeregowego.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. Użyj `If` instrukcji, aby określić, czy <xref:System.IO.Ports.SerialPort.ReadLine> Metoda zwraca `Nothing` (co oznacza, że nie jest dostępny żaden tekst). Jeśli jest zwracana `Nothing` , Zamknij `Do` pętlę.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Dodaj `Else` blok do instrukcji, `If` Aby obsłużyć przypadek, jeśli ciąg jest faktycznie odczytywany. Blok dołącza ciąg z portu szeregowego do zwracanego ciągu.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Zwraca ciąg.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 W tym przykładzie przyjęto założenie, że komputer korzysta z programu `COM1` .  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 W tym przykładzie przyjęto założenie, że komputer korzysta z programu `COM1` . Aby zapewnić większą elastyczność, kod powinien zezwalać użytkownikowi na wybranie żądanego portu szeregowego z listy dostępnych portów. Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](how-to-show-available-serial-ports.md).  
  
 W tym przykładzie używa `Try...Catch...Finally` bloku, aby upewnić się, że aplikacja zamknie port i przechwytuje wszystkie wyjątki limitów czasu. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Instrukcje: modemy dostępowe powiązane z portami seryjnymi](how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: wysyłanie ciągów do portów seryjnych](how-to-send-strings-to-serial-ports.md)
- [Instrukcje: wyświetlanie dostępnych portów seryjnych](how-to-show-available-serial-ports.md)
