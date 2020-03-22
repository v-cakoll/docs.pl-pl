---
title: 'Porady: wyświetlanie dostępnych portów seryjnych'
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

W tym temacie `My.Computer.Ports` opisano sposób używania do pokazywalenia dostępnych portów szeregowych komputera w języku Visual Basic.  
  
 Aby umożliwić użytkownikowi wybranie portu, którego ma być używany, <xref:System.Windows.Forms.ListBox> nazwy portów szeregowych są umieszczane w formancie.  
  
## <a name="example"></a>Przykład  

 W tym przykładzie pętli na `My.Computer.Ports.SerialPortNames` wszystkie ciągi, które zwraca właściwość. Te ciągi są nazwami dostępnych portów szeregowych na komputerze.  
  
 Zazwyczaj użytkownik wybiera port szeregowy, którego aplikacja powinna używać z listy dostępnych portów. W tym przykładzie nazwy portów <xref:System.Windows.Forms.ListBox> szeregowych są przechowywane w formancie. Aby uzyskać więcej informacji, zobacz [Formant pola list](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **sekcji Łączność i sieć**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Ten przykład wymaga:  
  
- Odwołanie do projektu system.Windows.Forms.dll.  
  
- Dostęp do członków <xref:System.Windows.Forms> obszaru nazw. Dodaj `Imports` instrukcję, jeśli nie są w pełni kwalifikujące się nazwy członków w kodzie. Aby uzyskać więcej informacji, zobacz [Oświadczenie importu (.NET Obszar nazw i Typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Aby formularz miał <xref:System.Windows.Forms.ListBox> formant o nazwie `ListBox1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Nie trzeba używać formantu do <xref:System.Windows.Forms.ListBox> wyświetlania dostępnych nazw portów szeregowych. Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub innego formantu. Jeśli aplikacja nie potrzebuje odpowiedzi od użytkownika, można <xref:System.Windows.Forms.TextBox> użyć formantu do wyświetlania informacji.  
  
> [!NOTE]
> Nazwy portów `My.Computer.Ports.SerialPortNames` zwrócone przez mogą być niepoprawne podczas uruchamiania w systemie Windows 98. Aby zapobiec błędom aplikacji, należy użyć `Try...Catch...Finally` obsługi `Using` wyjątków, takich jak instrukcja lub instrukcja, podczas używania nazw portów do otwierania portów.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Instrukcje: modemy dostępowe powiązane z portami seryjnymi](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: wysyłanie ciągów do portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
