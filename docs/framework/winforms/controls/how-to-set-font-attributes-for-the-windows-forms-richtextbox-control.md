---
title: 'Porady: ustawianie atrybutów czcionki dla formantu RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: 7c4c9362bb5a32bd8d5afc2b1edeb935d505fd19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533646"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="345ae-102">Porady: ustawianie atrybutów czcionki dla formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="345ae-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="345ae-103">Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant ma wiele opcji formatowania tekstu Wyświetla.</span><span class="sxs-lookup"><span data-stu-id="345ae-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="345ae-104">Możesz wprowadzić wybranych znaków pogrubiony, podkreślony lub kursywą, przy użyciu <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="345ae-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="345ae-105">Ta właściwość umożliwia również zmienić rozmiar i krój wybranych znaków.</span><span class="sxs-lookup"><span data-stu-id="345ae-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="345ae-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Właściwości umożliwia zmianę koloru wybranych znaków.</span><span class="sxs-lookup"><span data-stu-id="345ae-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="345ae-107">Aby zmienić wygląd znaków</span><span class="sxs-lookup"><span data-stu-id="345ae-107">To change the appearance of characters</span></span>  
  
1.  <span data-ttu-id="345ae-108">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości odpowiednią czcionkę.</span><span class="sxs-lookup"><span data-stu-id="345ae-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="345ae-109">Aby umożliwić użytkownikom ustawić rodziny czcionek, rozmiar i krój czcionki w aplikacji, należy zwykle użyć <xref:System.Windows.Forms.FontDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="345ae-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="345ae-110">Aby uzyskać ogólne informacje, zobacz [informacje o składniku FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="345ae-110">For an overview, see [FontDialog Component Overview](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="345ae-111">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> kolor odpowiedniej dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="345ae-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="345ae-112">Aby umożliwić użytkownikom ustawić kolor w aplikacji, należy zwykle użyć <xref:System.Windows.Forms.ColorDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="345ae-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="345ae-113">Aby uzyskać ogólne informacje, zobacz [colordialog — informacje o składniku](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="345ae-113">For an overview, see [ColorDialog Component Overview](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span></span>  
  
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
    >  <span data-ttu-id="345ae-114">Te właściwości mają wpływ tylko na zaznaczony tekst lub, w przypadku żaden tekst nie jest zaznaczony, tekst, który jest wpisany w bieżącej lokalizacji punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="345ae-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="345ae-115">Aby uzyskać informacje na programowy wybór tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="345ae-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345ae-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="345ae-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="345ae-117">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="345ae-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="345ae-118">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="345ae-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
