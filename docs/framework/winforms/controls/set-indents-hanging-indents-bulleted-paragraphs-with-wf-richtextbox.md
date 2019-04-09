---
title: 'Instrukcje: ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą kontrolki RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: 4cb9b351b5ed1ab9cd05be0763d967000791fb46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140650"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="ca016-102">Instrukcje: ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą kontrolki RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ca016-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="ca016-103">Formularze Windows <xref:System.Windows.Forms.RichTextBox> kontrolka ma wiele opcji formatowania tekstu, zostanie wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="ca016-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="ca016-104">Możesz sformatować zaznaczonych akapitów jako listy punktowane, ustawiając <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ca016-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="ca016-105">Można również użyć <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, i <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwości, aby ustawić wcięcia akapitów względem lewej i prawej krawędzi formantu a lewą krawędzią innych wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="ca016-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="ca016-106">Aby sformatować akapitu jako listy punktowane</span><span class="sxs-lookup"><span data-stu-id="ca016-106">To format a paragraph as a bulleted list</span></span>  
  
1.  <span data-ttu-id="ca016-107">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="ca016-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="ca016-108">Wcięcia akapitu</span><span class="sxs-lookup"><span data-stu-id="ca016-108">To indent a paragraph</span></span>  
  
1.  <span data-ttu-id="ca016-109">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędzią kontrolki a lewą krawędzią tekstu.</span><span class="sxs-lookup"><span data-stu-id="ca016-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2.  <span data-ttu-id="ca016-110">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędzią pierwszy wiersz tekstu akapitu a lewą krawędzią kolejne wiersze, w tym samym akapicie.</span><span class="sxs-lookup"><span data-stu-id="ca016-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="ca016-111">Wartość <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwość ma zastosowanie tylko do wierszy w akapicie, które zostały opakowane poniżej pierwszego wiersza.</span><span class="sxs-lookup"><span data-stu-id="ca016-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3.  <span data-ttu-id="ca016-112">Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między prawą krawędzią kontrolki a prawej krawędzi tekstu.</span><span class="sxs-lookup"><span data-stu-id="ca016-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
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
    >  <span data-ttu-id="ca016-113">Te właściwości mają wpływ na wszystkie akapitów, zawierające zaznaczony tekst i tekst, który bezpośrednio po bieżącym punkcie wstawiania.</span><span class="sxs-lookup"><span data-stu-id="ca016-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="ca016-114">Na przykład gdy użytkownik zaznacza słowo akapitu, a następnie dopasowuje wcięcie, nowe ustawienia zostaną zastosowane cały akapit, który zawiera słowo, a także wszelkie akapitów, następnie wprowadzone po akapitów.</span><span class="sxs-lookup"><span data-stu-id="ca016-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="ca016-115">Aby dowiedzieć się, jak programowy wybór tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca016-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca016-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca016-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="ca016-117">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ca016-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="ca016-118">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ca016-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
