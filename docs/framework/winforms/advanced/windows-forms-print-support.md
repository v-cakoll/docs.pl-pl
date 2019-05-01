---
title: Obsługa drukowania w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011856"
---
# <a name="windows-forms-print-support"></a>Obsługa drukowania w formularzach systemu Windows
Drukowanie w formularzach Windows Forms składa się przede wszystkim za pomocą [PrintDocument, składnik](../controls/printdocument-component-windows-forms.md) składnik, aby umożliwić użytkownikowi drukowanie i [PrintPreviewDialog, kontrolka](../controls/printpreviewdialog-control-windows-forms.md) kontroli [PrintDialog Składnik](../controls/printdialog-component-windows-forms.md) i [PageSetupDialog, składnik](../controls/pagesetupdialog-component-windows-forms.md) składniki zapewnienie znanego interfejsu graficznego użytkownikom zapoznanie się z systemu operacyjnego Windows.  
  
 Zwykle, Utwórz nowe wystąpienie klasy <xref:System.Drawing.Printing.PrintDocument> składnika, ustawić właściwości, które opisują, jakie drukowanie przy użyciu <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings> klasy i wywołania <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby faktycznie wydrukować dokument.  
  
 W trakcie drukowaniem z aplikacji z systemem Windows <xref:System.Drawing.Printing.PrintDocument> składnika pokaże dialogowe przerwania ostrzegać użytkowników fakt, że jest wykonywane drukowanie i umożliwić zadania drukowania, zostaną anulowane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie zadań drukowania formularzy Windows Standard](how-to-create-standard-windows-forms-print-jobs.md)  
 Opis sposobu użycia <xref:System.Drawing.Printing.PrintDocument> składnik do drukowania z formularza Windows.  
  
 [Instrukcje: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Wyjaśnia sposób modyfikowania wybranych opcji drukowania, programowo przy użyciu <xref:System.Windows.Forms.PrintDialog> składnika.  
  
 [Instrukcje: Wybieranie drukarek podłączonych do komputera użytkownika w formularzach Windows Forms](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 W tym artykule opisano, zmienianie drukarki do wydrukowania za pomocą <xref:System.Windows.Forms.PrintDialog> składnika w czasie wykonywania.  
  
 [Instrukcje: Drukowanie grafiki w formularzach Windows Forms](how-to-print-graphics-in-windows-forms.md)  
 W tym artykule opisano wysyłanie grafiki do drukarki.  
  
 [Instrukcje: Podglądu wydruku w formularzach Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 W tym artykule opisano wysyłanie tekstu do drukarki.  
  
 [Instrukcje: Zadań drukowania formularzy Windows ukończone](how-to-complete-windows-forms-print-jobs.md)  
 Wyjaśnia, jak powiadamia użytkowników do wykonania zadania drukowania.  
  
 [Instrukcje: Drukowanie formularza Windows](how-to-print-a-windows-form.md)  
 Pokazuje jak drukować kopię bieżącego formularza.  
  
 [Instrukcje: Drukowanie w formularzach Windows Forms przy użyciu podglądu wydruku](how-to-print-in-windows-forms-using-print-preview.md)  
 Ilustruje sposób używania <xref:System.Windows.Forms.PrintPreviewDialog> do drukowania dokumentu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [PrintDocument, składnik](../controls/printdocument-component-windows-forms.md)  
 Wyjaśnia, użycie <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
 [PrintDialog, składnik](../controls/printdialog-component-windows-forms.md)  
 Wyjaśnia, użycie <xref:System.Windows.Forms.PrintDialog> składnika.  
  
 [PrintPreviewDialog, kontrolka](../controls/printpreviewdialog-control-windows-forms.md)  
 Wyjaśnia, użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontroli.  
  
 [PageSetupDialog, składnik](../controls/pagesetupdialog-component-windows-forms.md)  
 Wyjaśnia, użycie <xref:System.Windows.Forms.PageSetupDialog> składnika.  
  
 <xref:System.Drawing.Printing>  
 Opisuje klasy w <xref:System.Drawing.Printing> przestrzeni nazw.
