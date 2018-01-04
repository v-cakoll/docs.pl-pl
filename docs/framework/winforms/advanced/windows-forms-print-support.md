---
title: "Obsługa drukowania w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81f89ee41eb9f8b492ab12e30ae4580cdffbd8f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-print-support"></a>Obsługa drukowania w formularzach systemu Windows
Drukowanie w formularzach systemu Windows obejmuje głównie przy użyciu [PrintDocument — składnik](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) składnik, aby umożliwić użytkownikowi drukowanie i [printpreviewdialog — formant](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) kontroli, [PrintDialog Składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) i [PageSetupDialog — składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) składniki zapewnienie znanego interfejsu graficznego użytkownikom zapoznanie się z systemu operacyjnego Windows.  
  
 Zwykle, Utwórz nowe wystąpienie klasy <xref:System.Drawing.Printing.PrintDocument> składnika, ustawić właściwości, które opisują wydruku przy użyciu <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings> klasy i wywołanie <xref:System.Drawing.Printing.PrintDocument.Print%2A> metody faktycznie wydrukować dokument.  
  
 Podczas drukowania z aplikacji systemu Windows <xref:System.Drawing.Printing.PrintDocument> składnika wyświetli okno dialogowe drukowania przerwania użytkownikom alertu fakt, że występuje drukowanie i umożliwić zadania drukowania do anulowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 Wyjaśniono, jak używać <xref:System.Drawing.Printing.PrintDocument> składnik do drukowania za pomocą formularza systemu Windows.  
  
 [Instrukcje: przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Wyjaśniono, jak i zmodyfikować wybrane opcje wydruku programowo przy użyciu <xref:System.Windows.Forms.PrintDialog> składnika.  
  
 [Instrukcje: wybieranie w formularzach Windows Forms drukarek podłączonych do komputera użytkownika](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 W tym artykule opisano, zmiana drukarki na drukowanie za pomocą <xref:System.Windows.Forms.PrintDialog> składnika w czasie wykonywania.  
  
 [Instrukcje: drukowanie grafiki w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 Opis wysyłania grafiki do drukarki.  
  
 [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Opis wysyłania tekstu do drukarki.  
  
 [Instrukcje: kończenie zadań drukowania formularzy Windows Forms](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 Wyjaśniono, jak powiadamiania użytkowników do wykonania zadania drukowania.  
  
 [Instrukcje: drukowanie formularza systemu Windows](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 Pokazuje, jak wydrukować kopię bieżącego formularza.  
  
 [Instrukcje: drukowanie w formularzach Windows Forms przy użyciu podglądu wydruku](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.PrintPreviewDialog> do drukowania dokumentu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [PrintDocument, składnik](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 Wyjaśniono, użycie <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
 [PrintDialog, składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 Wyjaśniono, użycie <xref:System.Windows.Forms.PrintDialog> składnika.  
  
 [PrintPreviewDialog, kontrolka](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 Wyjaśniono, użycie <xref:System.Windows.Forms.PrintPreviewDialog> formantu.  
  
 [PageSetupDialog, składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 Wyjaśniono, użycie <xref:System.Windows.Forms.PageSetupDialog> składnika.  
  
 <xref:System.Drawing.Printing>  
 Zawiera opis klas w <xref:System.Drawing.Printing> przestrzeni nazw.
