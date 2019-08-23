---
title: 'Instrukcje: wyświetlanie podglądu wydruku w aplikacjach formularzy Windows'
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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929005"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Instrukcje: wyświetlanie podglądu wydruku w aplikacjach formularzy Windows
Możesz użyć <xref:System.Windows.Forms.PrintPreviewDialog> kontrolki, aby umożliwić użytkownikom wyświetlanie dokumentu, często przed jego wydrukowaniem.  
  
 W tym celu należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy; jest to dokument do wydrukowania. Aby uzyskać więcej informacji na temat korzystania z podglądu <xref:System.Drawing.Printing.PrintDocument> wydruku ze składnikiem, zobacz [How to: Drukowanie w Windows Forms przy użyciu podglądu](../advanced/how-to-print-in-windows-forms-using-print-preview.md)wydruku.  
  
> [!NOTE]
> Aby można było <xref:System.Windows.Forms.PrintPreviewDialog> korzystać z kontrolki w czasie wykonywania, użytkownicy muszą mieć zainstalowaną na komputerze lokalnie lub za pomocą sieci, ponieważ jest to część określająca <xref:System.Windows.Forms.PrintPreviewDialog> sposób, w jaki ten dokument będzie wyglądał po wydrukowaniu.  
  
 Kontrolka<xref:System.Drawing.Printing.PrinterSettings>używaklasy. <xref:System.Windows.Forms.PrintPreviewDialog> Ponadto kontrolka <xref:System.Drawing.Printing.PageSettings> używa<xref:System.Windows.Forms.PrintPreviewDialog> klasy, tak jak składnik. <xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Windows.Forms.PrintPreviewDialog> Dokument wydruku określony we <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> właściwości kontrolki odwołuje się <xref:System.Drawing.Printing.PrinterSettings> do wystąpień obu klas i <xref:System.Drawing.Printing.PageSettings> i służy do renderowania dokumentu w oknie podglądu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Aby wyświetlić strony przy użyciu kontrolki PrintPreviewDialog  
  
- Użyj metody, aby wyświetlić okno dialogowe, <xref:System.Drawing.Printing.PrintDocument> określając do użycia. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> kodu procedura obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> otwiera wystąpienie kontrolki. Dokument drukowania jest określony we <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwości. W poniższym przykładzie nie określono dokumentu drukowania.  
  
     Przykład wymaga, aby formularz <xref:System.Windows.Forms.Button> miał kontrolkę <xref:System.Drawing.Printing.PrintDocument> , <xref:System.Windows.Forms.PrintPreviewDialog> składnik o nazwie `myDocument`i kontrolkę.  
  
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
