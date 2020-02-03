---
title: Ustawianie atrybutów czcionki dla kontrolki RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: f27256c155223df576ee3c42e6bf65270c870b0f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744855"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="abb60-102">Porady: ustawianie atrybutów czcionki dla formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="abb60-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="abb60-103">Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms ma wiele opcji formatowania wyświetlanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="abb60-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="abb60-104">Można wybrać pogrubienie, podkreślenie lub kursywę przy użyciu właściwości <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>.</span><span class="sxs-lookup"><span data-stu-id="abb60-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="abb60-105">Można także użyć tej właściwości, aby zmienić rozmiar i krój czcionki wybranych znaków.</span><span class="sxs-lookup"><span data-stu-id="abb60-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="abb60-106">Właściwość <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> umożliwia zmianę koloru wybranych znaków.</span><span class="sxs-lookup"><span data-stu-id="abb60-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="abb60-107">Aby zmienić wygląd znaków</span><span class="sxs-lookup"><span data-stu-id="abb60-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="abb60-108">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> na odpowiednią czcionkę.</span><span class="sxs-lookup"><span data-stu-id="abb60-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="abb60-109">Aby umożliwić użytkownikom ustawianie rodziny czcionek, rozmiaru i kroju czcionki w aplikacji, zazwyczaj używany jest składnik <xref:System.Windows.Forms.FontDialog>.</span><span class="sxs-lookup"><span data-stu-id="abb60-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="abb60-110">Aby zapoznać się z omówieniem, zobacz [Omówienie składnika FontDialog](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="abb60-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="abb60-111">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> na odpowiedni kolor.</span><span class="sxs-lookup"><span data-stu-id="abb60-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="abb60-112">Aby umożliwić użytkownikom ustawianie koloru w aplikacji, zazwyczaj używany jest składnik <xref:System.Windows.Forms.ColorDialog>.</span><span class="sxs-lookup"><span data-stu-id="abb60-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="abb60-113">Aby zapoznać się z omówieniem, zobacz [Omówienie składnika ColorDialog](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="abb60-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="abb60-114">Te właściwości mają wpływ tylko na zaznaczony tekst lub, jeśli nie wybrano tekstu, tekst, który jest wpisywany w bieżącej lokalizacji punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="abb60-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="abb60-115">Aby uzyskać informacje na temat wybierania tekstu programowo, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="abb60-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb60-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abb60-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="abb60-117">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="abb60-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="abb60-118">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="abb60-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
