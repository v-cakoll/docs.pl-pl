---
title: 'Porady: pokazywanie palety kolorów przy użyciu składnika ColorDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141786"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="f61af-102">Porady: pokazywanie palety kolorów przy użyciu składnika ColorDialog</span><span class="sxs-lookup"><span data-stu-id="f61af-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="f61af-103">Składnik [ColorDialog](colordialog-component-windows-forms.md) wyświetla paletę kolorów i zwraca właściwość zawierającą kolor wybrany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f61af-103">The [ColorDialog](colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="f61af-104">Aby wybrać kolor przy użyciu składnika ColorDialog</span><span class="sxs-lookup"><span data-stu-id="f61af-104">To choose a color using the ColorDialog component</span></span>  
  
1. <span data-ttu-id="f61af-105">Wyświetl okno dialogowe <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="f61af-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="f61af-106">Użyj <xref:System.Windows.Forms.DialogResult> właściwości, aby określić, jak okno dialogowe zostało zamknięte.</span><span class="sxs-lookup"><span data-stu-id="f61af-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="f61af-107">Użyj <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwości komponentu, <xref:System.Windows.Forms.ColorDialog> aby ustawić wybrany kolor.</span><span class="sxs-lookup"><span data-stu-id="f61af-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="f61af-108">W poniższym przykładzie <xref:System.Windows.Forms.Button> program <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń <xref:System.Windows.Forms.ColorDialog> formantu otwiera składnik.</span><span class="sxs-lookup"><span data-stu-id="f61af-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="f61af-109">Po wybraniu koloru i kliknięciu **przycisku OK**kolor tła <xref:System.Windows.Forms.Button> formantu jest ustawiony na wybrany kolor.</span><span class="sxs-lookup"><span data-stu-id="f61af-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="f61af-110">W przykładzie przyjęto <xref:System.Windows.Forms.Button> założenie, <xref:System.Windows.Forms.ColorDialog> że formularz ma formant i składnik.</span><span class="sxs-lookup"><span data-stu-id="f61af-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     <span data-ttu-id="f61af-111">(Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f61af-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f61af-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f61af-112">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="f61af-113">ColorDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="f61af-113">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
