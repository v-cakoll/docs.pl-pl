---
title: 'Porady: określanie właściwości strony za pomocą składnika PageSetupDialog'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52ef02ccfe6586f89adabb30187aa48e5fe87349
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Porady: określanie właściwości strony za pomocą składnika PageSetupDialog
[PageSetupDialog —](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) składnika wyświetla układ, rozmiar papieru i inne opcje układ strony użytkownikowi dla dokumentu.  
  
 Należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy — jest to wydrukować dokument. Ponadto użytkownicy muszą mieć zainstalowany na komputerze, lokalnie lub za pośrednictwem sieci, drukarki, jest częściowo jak <xref:System.Windows.Forms.PageSetupDialog> składnika Określa strony, użytkownik widzi opcji formatowania.  
  
 Praca z ważnym aspektem <xref:System.Windows.Forms.PageSetupDialog> składnik jest sposób interakcji z <xref:System.Drawing.Printing.PageSettings> klasy. <xref:System.Drawing.Printing.PageSettings> Klasa jest używana do określenia ustawień, które modyfikują sposób stronę wydruku, takich jak układ papieru, rozmiar strony i marginesów. Każdy z tych ustawień jest reprezentowany jako właściwość <xref:System.Drawing.Printing.PageSettings> klasy. <xref:System.Windows.Forms.PageSetupDialog> Klasy Modyfikuje wartości tych właściwości dla danego wystąpienia <xref:System.Drawing.Printing.PageSettings> klasy, która jest skojarzona z dokumentu (i jest reprezentowany jako <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> właściwości).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Aby ustawić właściwości strony za pomocą składnika PageSetupDialog  
  
1.  Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe, określając <xref:System.Drawing.Printing.PrintDocument> do użycia.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń otwiera wystąpienia <xref:System.Windows.Forms.PageSetupDialog> składnika. Istniejący dokument jest określona w <xref:System.Windows.Forms.PageSetupDialog.Document%2A> właściwości oraz jego <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> właściwość jest ustawiona na `false`.  
  
     W przykładzie założono formularz zawiera <xref:System.Windows.Forms.Button> kontroli, <xref:System.Drawing.Printing.PrintDocument> składnika o nazwie `myDocument`, a <xref:System.Windows.Forms.PageSetupDialog> składnika.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [PageSetupDialog, składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
