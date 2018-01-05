---
title: "Porady: wyświetlanie podglądu wydruku w aplikacjach Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2567a564b5769abd91d34696c1a94c21ad2913ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Porady: wyświetlanie podglądu wydruku w aplikacjach Windows Forms
Można użyć <xref:System.Windows.Forms.PrintPreviewDialog> sterowania, aby użytkownicy mogli wyświetlić dokument, często, zanim zostanie do drukowania.  
  
 Aby to zrobić, należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy; to wydrukować dokument. Aby uzyskać więcej informacji o korzystaniu z podglądu wydruku z <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [porady: drukowanie w Windows Forms przy użyciu podglądu wydruku](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Aby użyć <xref:System.Windows.Forms.PrintPreviewDialog> kontroli w czasie wykonywania, użytkownicy muszą mieć zainstalowany na komputerze, lokalnie lub za pośrednictwem sieci, drukarki, jest częściowo jak <xref:System.Windows.Forms.PrintPreviewDialog> składnika określa wygląd dokumentu po wydrukowaniu.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> Kontrolować używa <xref:System.Drawing.Printing.PrinterSettings> klasy. Ponadto <xref:System.Windows.Forms.PrintPreviewDialog> kontrolować używa <xref:System.Drawing.Printing.PageSettings> klasy, podobnie jak <xref:System.Windows.Forms.PrintPreviewDialog> składników. Dokument wydruku określone w <xref:System.Windows.Forms.PrintPreviewDialog> formantu <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> właściwość odwołuje się do wystąpienia obu <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings> klasy i te, które są używane do renderowania dokumentu w oknie Podgląd.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Aby wyświetlić strony za pomocą printpreviewdialog — formant  
  
-   Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe, określając <xref:System.Drawing.Printing.PrintDocument> do użycia.  
  
     W poniższym przykładzie kodu <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń otwiera wystąpienia <xref:System.Windows.Forms.PrintPreviewDialog> formantu. Dokument wydruku jest określona w <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwości. W poniższym przykładzie jest określony żaden dokument wydruku.  
  
     Przykład wymaga, aby miało formularza <xref:System.Windows.Forms.Button> kontroli, <xref:System.Drawing.Printing.PrintDocument> składnika o nazwie `myDocument`i <xref:System.Windows.Forms.PrintPreviewDialog> formantu.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [PrintDocument, składnik](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [PrintPreviewDialog, kontrolka](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
