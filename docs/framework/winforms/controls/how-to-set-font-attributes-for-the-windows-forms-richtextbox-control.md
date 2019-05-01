---
title: 'Instrukcje: ustawianie atrybutów czcionki dla kontrolki RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: a6fe5b30c457fae2d53c946092b214f492fe5e9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013273"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="dfddc-102">Instrukcje: ustawianie atrybutów czcionki dla kontrolki RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dfddc-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="dfddc-103">Formularze Windows <xref:System.Windows.Forms.RichTextBox> kontrolka ma wiele opcji formatowania tekstu, zostanie wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="dfddc-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="dfddc-104">Aby włączyć wybranych znaków pogrubienie, podkreślony lub kursywa, przy użyciu <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dfddc-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="dfddc-105">Ta właściwość umożliwia również zmienić rozmiar i krój czcionki wybranych znaków.</span><span class="sxs-lookup"><span data-stu-id="dfddc-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="dfddc-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Właściwości umożliwia zmianę koloru zaznaczonych znaków.</span><span class="sxs-lookup"><span data-stu-id="dfddc-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="dfddc-107">Aby zmienić wygląd znaków</span><span class="sxs-lookup"><span data-stu-id="dfddc-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="dfddc-108">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwość odpowiednią czcionkę.</span><span class="sxs-lookup"><span data-stu-id="dfddc-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="dfddc-109">Aby umożliwić użytkownikom ustawić rodzinę czcionek, rozmiar i krój czcionki w aplikacji, zazwyczaj używasz <xref:System.Windows.Forms.FontDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="dfddc-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="dfddc-110">Aby uzyskać przegląd, zobacz [— informacje o składniku FontDialog](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="dfddc-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="dfddc-111">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> właściwość odpowiedni kolor.</span><span class="sxs-lookup"><span data-stu-id="dfddc-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="dfddc-112">Aby umożliwić użytkownikom ustawić kolor w aplikacji, zazwyczaj używasz <xref:System.Windows.Forms.ColorDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="dfddc-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="dfddc-113">Aby uzyskać przegląd, zobacz [ColorDialog, składnik — omówienie](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="dfddc-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
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
    >  <span data-ttu-id="dfddc-114">Te właściwości mają wpływ tylko na zaznaczony tekst lub, jeśli nie wybrano tekstu, tekst jest wpisane w bieżącej lokalizacji punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="dfddc-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="dfddc-115">Aby uzyskać informacji na temat programowy wybór tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="dfddc-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfddc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfddc-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="dfddc-117">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="dfddc-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="dfddc-118">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dfddc-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
