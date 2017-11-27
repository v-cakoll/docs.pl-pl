---
title: "Porady: wyświetlanie składnika PrintDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e1162a4e926d5be35f8f7bb7cdeb92264f293aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-the-printdialog-component"></a>Porady: wyświetlanie składnika PrintDialog
<xref:System.Windows.Forms.PrintDialog> Składnik jest standardowe okno dialogowe wydruku systemu Windows, który wielu użytkowników należy zapoznać się z. Ponieważ użytkownicy będą natychmiast doświadczenia z nim, jest przydatne w przypadku użycia <xref:System.Windows.Forms.PrintDialog> składnika.  
  
### <a name="to-display-the-printdialog-component"></a>Aby wyświetlić składnika PrintDialog  
  
-   Wywołanie <xref:System.Windows.Forms.Form.ShowDialog%2A> metodę z kodu aplikacji.  
  
     Gdy składnik jest wyświetlany, użytkowników będzie korzystać z niego, ustawianie właściwości zadania drukowania. Są one zapisane w <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` klasy (i <xref:System.Drawing.Printing.PageSettings> klasy, jeśli użytkownik uzyskuje dostęp do [PageSetupDialog — składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) za pośrednictwem <xref:System.Windows.Forms.PrintDialog> składnika) skojarzony z tym zadania drukowania. Następnie można wprowadzić wywołań właściwości zestawu ustalić szczegółowe informacje na temat zadania drukowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie zadań drukowania formularzy standardowego systemu Windows](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Porady: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [Printpreviewdialog — formant](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Printdialog — składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Obsługa drukowania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Formanty formularzy systemu Windows](../../../../docs/framework/winforms/controls/index.md)
