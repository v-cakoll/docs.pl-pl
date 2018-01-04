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
ms.workload: dotnet
ms.openlocfilehash: d955febe528add4b774766a3b204f96eef5a119d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-the-printdialog-component"></a>Porady: wyświetlanie składnika PrintDialog
<xref:System.Windows.Forms.PrintDialog> Składnik jest standardowe okno dialogowe wydruku systemu Windows, który wielu użytkowników należy zapoznać się z. Ponieważ użytkownicy będą natychmiast doświadczenia z nim, jest przydatne w przypadku użycia <xref:System.Windows.Forms.PrintDialog> składnika.  
  
### <a name="to-display-the-printdialog-component"></a>Aby wyświetlić składnika PrintDialog  
  
-   Wywołanie <xref:System.Windows.Forms.Form.ShowDialog%2A> metodę z kodu aplikacji.  
  
     Gdy składnik jest wyświetlany, użytkowników będzie korzystać z niego, ustawianie właściwości zadania drukowania. Są one zapisane w <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` klasy (i <xref:System.Drawing.Printing.PageSettings> klasy, jeśli użytkownik uzyskuje dostęp do [PageSetupDialog — składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) za pośrednictwem <xref:System.Windows.Forms.PrintDialog> składnika) skojarzony z tym zadania drukowania. Następnie można wprowadzić wywołań właściwości zestawu ustalić szczegółowe informacje na temat zadania drukowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Instrukcje: przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [PrintPreviewDialog, kontrolka](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [PrintDialog, składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)
