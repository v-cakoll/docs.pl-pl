---
title: 'Instrukcje: Wyświetlanie dostępnych portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 57b3a33fecb6128a10ce903fd26724de98acb8c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834650"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Instrukcje: Wyświetlanie dostępnych portów seryjnych w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` Aby wyświetlić dostępne porty szeregowe komputera w języku Visual Basic.  
  
 Aby zezwolić na port, który umożliwia wybranie użytkownika, nazwy portów szeregowych są umieszczane w <xref:System.Windows.Forms.ListBox> kontroli.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pętli wszystkich ciągów, `My.Computer.Ports.SerialPortNames` zwraca właściwości. Te ciągi są nazwy dostępnych portów szeregowych na komputerze.  
  
 Zazwyczaj użytkownik wybierze które portu szeregowego, należy użyć aplikacji z listy dostępnych portów. W tym przykładzie nazwy portu szeregowego są przechowywane w <xref:System.Windows.Forms.ListBox> kontroli. Aby uzyskać więcej informacji, zobacz [kontrolki ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie projektu do pliku System.Windows.Forms.dll.  
  
-   Dostęp do elementów członkowskich <xref:System.Windows.Forms> przestrzeni nazw. Dodaj `Imports` instrukcji, jeśli użytkownik są nie pełni kwalifikujących się nazwy elementów członkowskich w kodzie. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   Mających formularza <xref:System.Windows.Forms.ListBox> formantu o nazwie `ListBox1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Nie trzeba używać <xref:System.Windows.Forms.ListBox> formantu, aby wyświetlić nazwy dostępnych portu szeregowego. Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub inny formant. Jeśli aplikacja nie wymaga odpowiedź od użytkownika, możesz użyć <xref:System.Windows.Forms.TextBox> formantu, aby wyświetlić informacje.  
  
> [!NOTE]
>  Nazwy portu zwrócony przez `My.Computer.Ports.SerialPortNames` mogą być niepoprawne uruchamiania Windows 98. Aby uniknąć błędów aplikacji, należy użyć obsługi wyjątków, takie jak `Try...Catch...Finally` instrukcji lub `Using` instrukcji, gdy używane są nazwy portu umożliwiające otwarcie portów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Instrukcje: Modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: Wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: Odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
