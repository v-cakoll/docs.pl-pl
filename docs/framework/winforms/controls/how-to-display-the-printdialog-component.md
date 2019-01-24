---
title: 'Instrukcje: Wyświetlanie składnika PrintDialog'
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 5315dc8b47c8ca846376ac6d1da5a0bf46fd6241
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544000"
---
# <a name="how-to-display-the-printdialog-component"></a>Instrukcje: Wyświetlanie składnika PrintDialog
<xref:System.Windows.Forms.PrintDialog> Składnik to standardowe okno dialogowe drukowania Windows wielu użytkowników należy zapoznać się z. Ponieważ użytkownicy będą natychmiast doświadczenia z nią, korzystne byłoby do użycia <xref:System.Windows.Forms.PrintDialog> składnika.  
  
### <a name="to-display-the-printdialog-component"></a>Aby Wyświetlanie składnika PrintDialog  
  
-   Wywołaj <xref:System.Windows.Forms.Form.ShowDialog%2A> metody z kodem aplikacji.  
  
     Gdy składnik zostanie wyświetlone, użytkownicy będą korzystać z niego, ustawienie właściwości zadania drukowania. Są one zapisywane w <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` klasy (i <xref:System.Drawing.Printing.PageSettings> klasy, jeśli użytkownik uzyskuje dostęp do [PageSetupDialog, składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) za pośrednictwem <xref:System.Windows.Forms.PrintDialog> składnika) skojarzonego z tym zadaniem drukowania. Następnie można prowadzić rozmowy właściwości zestawu określić szczegóły zadania drukowania.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie zadań drukowania formularzy Windows Standard](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Instrukcje: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [PrintPreviewDialog, kontrolka](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)
- [PrintDialog, składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
- [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
- [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)
