---
title: Wyświetlanie podglądu wydruku w aplikacjach Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745571"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Porady: wyświetlanie podglądu wydruku w aplikacjach formularzy Windows
Można użyć kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>, aby umożliwić użytkownikom wyświetlanie dokumentu, często przed jego wydrukowaniem.  
  
 W tym celu należy określić wystąpienie klasy <xref:System.Drawing.Printing.PrintDocument>; jest to dokument do wydrukowania. Aby uzyskać więcej informacji o korzystaniu z podglądu wydruku w składniku <xref:System.Drawing.Printing.PrintDocument>, zobacz [How to: Print in Windows Forms using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
> Aby można było korzystać z kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> w czasie wykonywania, użytkownicy muszą mieć zainstalowaną na komputerze lokalnie lub za pomocą sieci, ponieważ w ten sposób składnik <xref:System.Windows.Forms.PrintPreviewDialog> określa sposób, w jaki dokument będzie wyglądał po wydrukowaniu.  
  
 Kontrolka <xref:System.Windows.Forms.PrintPreviewDialog> używa klasy <xref:System.Drawing.Printing.PrinterSettings>. Ponadto formant <xref:System.Windows.Forms.PrintPreviewDialog> używa klasy <xref:System.Drawing.Printing.PageSettings>, tak jak składnik <xref:System.Windows.Forms.PrintPreviewDialog>. Dokument drukowania określony we właściwości <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> odwołuje się do wystąpień obu klas <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings>, które są używane do renderowania dokumentu w oknie podglądu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Aby wyświetlić strony przy użyciu kontrolki PrintPreviewDialog  
  
- Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe, określając <xref:System.Drawing.Printing.PrintDocument> do użycia.  
  
     W poniższym przykładzie kodu <xref:System.Windows.Forms.Button> kontrolka <xref:System.Windows.Forms.Control.Click> do obsługi zdarzeń otwiera wystąpienie kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>. Dokument drukowania jest określony we właściwości <xref:System.Windows.Forms.PrintDialog.Document%2A>. W poniższym przykładzie nie określono dokumentu drukowania.  
  
     Przykład wymaga, aby formularz miał formant <xref:System.Windows.Forms.Button>, składnik <xref:System.Drawing.Printing.PrintDocument> o nazwie `myDocument`i formant <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [PrintDocument, składnik](printdocument-component-windows-forms.md)
- [PrintPreviewDialog, kontrolka](printpreviewdialog-control-windows-forms.md)
- [Obsługa drukowania w formularzach Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
