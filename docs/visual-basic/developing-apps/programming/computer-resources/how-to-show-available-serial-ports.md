---
title: 'Instrukcje: wyświetlanie dostępnych portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345573"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Porady: wyświetlanie dostępnych portów seryjnych w Visual Basic

W tym temacie opisano sposób użycia `My.Computer.Ports` programu w celu wyświetlenia dostępnych portów szeregowych komputera w Visual Basic.  
  
 Aby umożliwić użytkownikowi wybranie portu do użycia, nazwy portów szeregowych są umieszczane w <xref:System.Windows.Forms.ListBox> kontrolce.  
  
## <a name="example"></a>Przykład  

 Ten przykład pętli dla wszystkich ciągów zwracanych przez `My.Computer.Ports.SerialPortNames` właściwość. Te ciągi są nazwami dostępnych portów szeregowych na komputerze.  
  
 Zazwyczaj użytkownik wybiera port szeregowy, który ma być używany przez aplikację z listy dostępnych portów. W tym przykładzie nazwy portów szeregowych są przechowywane w <xref:System.Windows.Forms.ListBox> kontrolce. Aby uzyskać więcej informacji, zobacz [formant ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Ten przykład wymaga:  
  
- Odwołanie do projektu do System. Windows. Forms. dll.  
  
- Dostęp do elementów członkowskich <xref:System.Windows.Forms> przestrzeni nazw. Dodaj `Imports` instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Formularz ma <xref:System.Windows.Forms.ListBox> kontrolkę o nazwie `ListBox1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Nie trzeba używać <xref:System.Windows.Forms.ListBox> kontrolki do wyświetlania dostępnych nazw portów szeregowych. Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub innej kontrolki. Jeśli aplikacja nie potrzebuje odpowiedzi od użytkownika, można użyć <xref:System.Windows.Forms.TextBox> kontrolki do wyświetlenia informacji.  
  
> [!NOTE]
> Nazwy portów zwracane przez `My.Computer.Ports.SerialPortNames` mogą być nieprawidłowe w przypadku uruchamiania w systemie Windows 98. Aby zapobiec błędom aplikacji, należy użyć obsługi wyjątków, na `Try...Catch...Finally` przykład instrukcji lub `Using` instrukcji, w przypadku używania nazw portów do otwierania portów.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Instrukcje: modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
