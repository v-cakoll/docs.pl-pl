---
title: 'Instrukcje: pokazywanie listy czcionek przy użyciu składnika FontDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: 40679136ea62a437009b308a8b206cf251b46222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307330"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a><span data-ttu-id="9f687-102">Instrukcje: pokazywanie listy czcionek przy użyciu składnika FontDialog</span><span class="sxs-lookup"><span data-stu-id="9f687-102">How to: Show a Font List with the FontDialog Component</span></span>
<span data-ttu-id="9f687-103">[FontDialog](fontdialog-component-windows-forms.md) składnika pozwala użytkownikom na wybór czcionki, a także zmienić jego aspektach wyświetlania, takie jak rozmiar i grubość.</span><span class="sxs-lookup"><span data-stu-id="9f687-103">The [FontDialog](fontdialog-component-windows-forms.md) component allows users to select a font, as well as change its display aspects, such as its weight and size.</span></span>  
  
 <span data-ttu-id="9f687-104">Czcionka zaznaczona w oknie dialogowym są zwracane w <xref:System.Windows.Forms.FontDialog.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9f687-104">The font selected in the dialog box is returned in the <xref:System.Windows.Forms.FontDialog.Font%2A> property.</span></span> <span data-ttu-id="9f687-105">W związku z tym wykorzystując czcionkę wybrane przez użytkownika jest równie proste jak odczytywanie właściwości.</span><span class="sxs-lookup"><span data-stu-id="9f687-105">Thus, taking advantage of the font selected by the user is as easy as reading a property.</span></span>  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a><span data-ttu-id="9f687-106">Aby wybrać właściwości czcionki przy użyciu składnika FontDialog</span><span class="sxs-lookup"><span data-stu-id="9f687-106">To select font properties using the FontDialog Component</span></span>  
  
1. <span data-ttu-id="9f687-107">Wyświetlane przy użyciu okno dialogowe <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9f687-107">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="9f687-108">Użyj <xref:System.Windows.Forms.DialogResult> właściwości w celu określenia, jak okno dialogowe zostało zamknięte.</span><span class="sxs-lookup"><span data-stu-id="9f687-108">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="9f687-109">Użyj <xref:System.Windows.Forms.FontDialog.Font%2A> właściwość umożliwiająca ustawienie wymaganej czcionki.</span><span class="sxs-lookup"><span data-stu-id="9f687-109">Use the <xref:System.Windows.Forms.FontDialog.Font%2A> property to set the desired font.</span></span>  
  
     <span data-ttu-id="9f687-110">W poniższym przykładzie <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zostanie otwarty program obsługi zdarzeń <xref:System.Windows.Forms.FontDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="9f687-110">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="9f687-111">Gdy czcionka jest wybrana, a użytkownik kliknie **OK**, <xref:System.Windows.Forms.FontDialog.Font%2A> właściwość <xref:System.Windows.Forms.TextBox> formant, który znajduje się w formularzu jest ustawiona na wybranej czcionki.</span><span class="sxs-lookup"><span data-stu-id="9f687-111">When a font is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.FontDialog.Font%2A> property of a <xref:System.Windows.Forms.TextBox> control that is on the form is set to the chosen font.</span></span> <span data-ttu-id="9f687-112">W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli <xref:System.Windows.Forms.TextBox> kontroli i <xref:System.Windows.Forms.FontDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="9f687-112">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a  <xref:System.Windows.Forms.TextBox> control, and a <xref:System.Windows.Forms.FontDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     <span data-ttu-id="9f687-113">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9f687-113">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9f687-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f687-114">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="9f687-115">FontDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="9f687-115">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
