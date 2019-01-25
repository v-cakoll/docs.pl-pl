---
title: 'Instrukcje: Określanie właściwości strony za pomocą składnika PageSetupDialog'
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
ms.openlocfilehash: c72ed5e6db6149f2161e0586c783e041eb0b731b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713541"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Instrukcje: Określanie właściwości strony za pomocą składnika PageSetupDialog
[PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) składnika wyświetlane układ, rozmiar papieru i inne opcje układu strony użytkownika do danego dokumentu.  
  
 Należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy — jest to dokument do wydrukowania. Ponadto użytkownicy muszą mieć zainstalowany na komputerze, lokalnie lub za pośrednictwem sieci, drukarki, jest częściowo sposób, w jaki <xref:System.Windows.Forms.PageSetupDialog> składnika Określa stronę, użytkownik widzi opcji formatowania.  
  
 Praca z ważnym aspektem <xref:System.Windows.Forms.PageSetupDialog> składnik to sposób jej interakcji z <xref:System.Drawing.Printing.PageSettings> klasy. <xref:System.Drawing.Printing.PageSettings> Klasa jest używana do określenia ustawienia umożliwiające modyfikowanie sposobu stronę do wydrukowania, takie jak układ papieru, rozmiar strony i marginesów. Każdy z tych ustawień jest reprezentowany jako właściwość <xref:System.Drawing.Printing.PageSettings> klasy. <xref:System.Windows.Forms.PageSetupDialog> Klasy Modyfikuje wartości tej właściwości dla danego wystąpienia <xref:System.Drawing.Printing.PageSettings> klasę, która jest skojarzona z dokumentu (i jest reprezentowany jako <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> właściwości).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Aby ustawić właściwości strony za pomocą składnika PageSetupDialog  
  
1.  Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe, określając <xref:System.Drawing.Printing.PrintDocument> do użycia.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń otwaiera wystąpienia programu <xref:System.Windows.Forms.PageSetupDialog> składnika. Określono istniejący dokument w <xref:System.Windows.Forms.PageSetupDialog.Document%2A> właściwości, a jego <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> właściwość jest ustawiona na `false`.  
  
     W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli <xref:System.Drawing.Printing.PrintDocument> składnika o nazwie `myDocument`, a <xref:System.Windows.Forms.PageSetupDialog> składnika.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.PageSetupDialog>
- [Instrukcje: Tworzenie zadań drukowania formularzy Windows Standard](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [PageSetupDialog, składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
