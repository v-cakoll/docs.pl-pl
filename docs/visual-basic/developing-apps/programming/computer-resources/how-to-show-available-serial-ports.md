---
title: 'Instrukcje: Pokaż dostępne porty szeregowe w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e8e0f6d63f7135c3bbe24ee6426cd714f2eb275f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956921"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Instrukcje: Pokaż dostępne porty szeregowe w Visual Basic
W tym temacie opisano sposób użycia `My.Computer.Ports` programu w celu wyświetlenia dostępnych portów szeregowych komputera w Visual Basic.  
  
 Aby umożliwić użytkownikowi wybranie portu do użycia, nazwy portów szeregowych są umieszczane w <xref:System.Windows.Forms.ListBox> kontrolce.  
  
## <a name="example"></a>Przykład  
 Ten przykład pętli dla wszystkich ciągów `My.Computer.Ports.SerialPortNames` zwracanych przez właściwość. Te ciągi są nazwami dostępnych portów szeregowych na komputerze.  
  
 Zazwyczaj użytkownik wybiera port szeregowy, który ma być używany przez aplikację z listy dostępnych portów. W tym przykładzie nazwy portów szeregowych są przechowywane w <xref:System.Windows.Forms.ListBox> kontrolce. Aby uzyskać więcej informacji, zobacz [formant ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołanie do projektu do System. Windows. Forms. dll.  
  
- Dostęp do elementów członkowskich <xref:System.Windows.Forms> przestrzeni nazw. `Imports` Dodaj instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie. Aby uzyskać więcej informacji, zobacz Imports — [instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Formularz ma <xref:System.Windows.Forms.ListBox> kontrolkę o nazwie `ListBox1`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Nie trzeba używać <xref:System.Windows.Forms.ListBox> kontrolki do wyświetlania dostępnych nazw portów szeregowych. Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub innej kontrolki. Jeśli aplikacja nie potrzebuje odpowiedzi od użytkownika, można użyć <xref:System.Windows.Forms.TextBox> kontrolki do wyświetlenia informacji.  
  
> [!NOTE]
> Nazwy portów zwracane przez `My.Computer.Ports.SerialPortNames` mogą być nieprawidłowe w przypadku uruchamiania w systemie Windows 98. Aby zapobiec błędom aplikacji, należy użyć obsługi wyjątków, `Try...Catch...Finally` na przykład instrukcji `Using` lub instrukcji, w przypadku używania nazw portów do otwierania portów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Instrukcje: Modemy telefoniczne dołączone do portów szeregowych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Instrukcje: Wyślij ciągi do portów szeregowych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Instrukcje: Odbieraj ciągi z portów szeregowych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
