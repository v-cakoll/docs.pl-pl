---
title: Obsługa drukowania
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732490"
---
# <a name="windows-forms-print-support"></a>Obsługa drukowania w formularzach systemu Windows
Drukowanie w Windows Forms składa się głównie z używania składnika [składnika PrintDocument](../controls/printdocument-component-windows-forms.md) , aby umożliwić użytkownikowi drukowanie oraz kontrolki [sterowania PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md) , [składnik PrintDialog](../controls/printdialog-component-windows-forms.md) i składnik [składnika PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) , aby zapewnić znany interfejs graficzny dla użytkowników przyzwyczajonych do systemu operacyjnego Windows.  
  
 Zazwyczaj tworzysz nowe wystąpienie składnika <xref:System.Drawing.Printing.PrintDocument>, ustaw właściwości opisujące, co należy wydrukować przy użyciu klas <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings>, a następnie Wywołaj metodę <xref:System.Drawing.Printing.PrintDocument.Print%2A>, aby rzeczywiście wydrukować dokument.  
  
 W trakcie drukowania z aplikacji opartej na systemie Windows, składnik <xref:System.Drawing.Printing.PrintDocument> wyświetli okno dialogowe przerwania drukowania, aby ostrzec użytkowników o tym, że drukowanie odbywa się i aby umożliwić anulowanie zadania drukowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms](how-to-create-standard-windows-forms-print-jobs.md)  
 Wyjaśnia, jak używać składnika <xref:System.Drawing.Printing.PrintDocument> do drukowania z formularza systemu Windows.  
  
 [Instrukcje: przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Wyjaśnia, jak modyfikować wybrane opcje drukowania programowo przy użyciu składnika <xref:System.Windows.Forms.PrintDialog>.  
  
 [Instrukcje: wybieranie w formularzach Windows Forms drukarek podłączonych do komputera użytkownika](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Opisuje zmianę drukarki do drukowania przy użyciu składnika <xref:System.Windows.Forms.PrintDialog> w czasie wykonywania.  
  
 [Instrukcje: drukowanie grafiki w formularzach Windows Forms](how-to-print-graphics-in-windows-forms.md)  
 Opisuje wysyłanie grafiki do drukarki.  
  
 [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Opisuje wysyłanie tekstu do drukarki.  
  
 [Instrukcje: kończenie zadań drukowania formularzy Windows Forms](how-to-complete-windows-forms-print-jobs.md)  
 Wyjaśnia, jak wysyłać alerty użytkowników do ukończenia zadania drukowania.  
  
 [Instrukcje: drukowanie formularza systemu Windows](how-to-print-a-windows-form.md)  
 Pokazuje, jak drukować kopię bieżącego formularza.  
  
 [Instrukcje: drukowanie w formularzach Windows Forms przy użyciu podglądu wydruku](how-to-print-in-windows-forms-using-print-preview.md)  
 Pokazuje, w jaki sposób używać <xref:System.Windows.Forms.PrintPreviewDialog> do drukowania dokumentu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [PrintDocument, składnik](../controls/printdocument-component-windows-forms.md)  
 Wyjaśnia użycie składnika <xref:System.Drawing.Printing.PrintDocument>.  
  
 [PrintDialog, składnik](../controls/printdialog-component-windows-forms.md)  
 Wyjaśnia użycie składnika <xref:System.Windows.Forms.PrintDialog>.  
  
 [PrintPreviewDialog, kontrolka](../controls/printpreviewdialog-control-windows-forms.md)  
 Wyjaśnia użycie kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
 [PageSetupDialog, składnik](../controls/pagesetupdialog-component-windows-forms.md)  
 Wyjaśnia użycie składnika <xref:System.Windows.Forms.PageSetupDialog>.  
  
 <xref:System.Drawing.Printing>  
 Opisuje klasy w przestrzeni nazw <xref:System.Drawing.Printing>.
