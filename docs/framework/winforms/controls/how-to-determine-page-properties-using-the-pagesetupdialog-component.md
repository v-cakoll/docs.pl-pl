---
title: 'Porady: określanie właściwości strony za pomocą składnika PageSetupDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142046"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Porady: określanie właściwości strony za pomocą składnika PageSetupDialog
[Składnik PageSetupDialog](pagesetupdialog-component-windows-forms.md) przedstawia użytkownikowi wybór układu, rozmiaru papieru i innego układu strony dla dokumentu.  
  
 Należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy — jest to dokument, który ma zostać wydrukowany. Ponadto użytkownicy muszą mieć zainstalowaną drukarkę na swoim komputerze, lokalnie lub za <xref:System.Windows.Forms.PageSetupDialog> pośrednictwem sieci, ponieważ jest to częściowo sposób, w jaki składnik określa opcje formatowania strony prezentowane użytkownikowi.  
  
 Ważnym aspektem pracy <xref:System.Windows.Forms.PageSetupDialog> z komponentem jest sposób <xref:System.Drawing.Printing.PageSettings> interakcji z klasą. Klasa <xref:System.Drawing.Printing.PageSettings> służy do określania ustawień, które modyfikują sposób drukowania strony, takich jak orientacja papieru, rozmiar strony i marginesy. Każde z tych ustawień jest reprezentowane <xref:System.Drawing.Printing.PageSettings> jako właściwość klasy. Klasa <xref:System.Windows.Forms.PageSetupDialog> modyfikuje te wartości właściwości dla <xref:System.Drawing.Printing.PageSettings> danego wystąpienia klasy, która jest skojarzona <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> z dokumentem (i jest reprezentowana jako właściwość).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Aby ustawić właściwości strony przy użyciu składnika PageSetupDialog  
  
1. Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody, aby wyświetlić okno <xref:System.Drawing.Printing.PrintDocument> dialogowe, określając do użycia.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> program <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń formantu otwiera wystąpienie składnika. <xref:System.Windows.Forms.PageSetupDialog> Istniejący dokument jest <xref:System.Windows.Forms.PageSetupDialog.Document%2A> określony we <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> właściwości, a `false`jego właściwość jest ustawiona na .  
  
     W przykładzie przyjęto <xref:System.Windows.Forms.Button> założenie, <xref:System.Drawing.Printing.PrintDocument> że `myDocument`formularz ma <xref:System.Windows.Forms.PageSetupDialog> formant, składnik o nazwie i składnik.  
  
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
  
     (Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.PageSetupDialog>
- [Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [PageSetupDialog, składnik](pagesetupdialog-component-windows-forms.md)
