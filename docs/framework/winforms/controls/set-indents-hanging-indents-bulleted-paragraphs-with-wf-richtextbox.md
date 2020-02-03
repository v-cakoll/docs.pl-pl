---
title: Ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą kontrolki RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743014"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="963fb-102">Porady: ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="963fb-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="963fb-103">Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms ma wiele opcji formatowania wyświetlanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="963fb-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="963fb-104">Można sformatować wybrane akapity jako listy punktowane przez ustawienie właściwości <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>.</span><span class="sxs-lookup"><span data-stu-id="963fb-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="963fb-105">Można również użyć właściwości <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>i <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>, aby ustawić wcięcia akapitów względem lewej i prawej krawędzi kontrolki oraz lewą krawędź tekstu.</span><span class="sxs-lookup"><span data-stu-id="963fb-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="963fb-106">Aby sformatować akapit jako listę punktowaną</span><span class="sxs-lookup"><span data-stu-id="963fb-106">To format a paragraph as a bulleted list</span></span>  
  
1. <span data-ttu-id="963fb-107">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="963fb-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="963fb-108">Aby zwiększyć wcięcie akapitu</span><span class="sxs-lookup"><span data-stu-id="963fb-108">To indent a paragraph</span></span>  
  
1. <span data-ttu-id="963fb-109">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> na liczbę całkowitą reprezentującą odległość (w pikselach) między lewą krawędzią kontrolki a lewą krawędzią tekstu.</span><span class="sxs-lookup"><span data-stu-id="963fb-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2. <span data-ttu-id="963fb-110">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędzią pierwszego wiersza tekstu w akapicie a lewą krawędzią kolejnych wierszy w tym samym akapicie.</span><span class="sxs-lookup"><span data-stu-id="963fb-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="963fb-111">Wartość właściwości <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> dotyczy tylko wierszy w akapicie, które zostały opakowane poniżej pierwszego wiersza.</span><span class="sxs-lookup"><span data-stu-id="963fb-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3. <span data-ttu-id="963fb-112">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> na liczbę całkowitą reprezentującą odległość w pikselach między prawą krawędzią kontrolki a prawą krawędzią tekstu.</span><span class="sxs-lookup"><span data-stu-id="963fb-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="963fb-113">Wszystkie te właściwości mają wpływ na wszystkie akapity, które zawierają zaznaczony tekst, a także tekst, który jest wpisywany po bieżącym punkcie wstawiania.</span><span class="sxs-lookup"><span data-stu-id="963fb-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="963fb-114">Na przykład gdy użytkownik wybierze wyraz w akapicie, a następnie dostosowuje wcięcia, nowe ustawienia zostaną zastosowane do całego akapitu zawierającego ten wyraz, a także do każdego akapitu wprowadzonego po wybranym akapicie.</span><span class="sxs-lookup"><span data-stu-id="963fb-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="963fb-115">Aby uzyskać informacje na temat programistycznego wybierania tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="963fb-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963fb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="963fb-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="963fb-117">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="963fb-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="963fb-118">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="963fb-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
