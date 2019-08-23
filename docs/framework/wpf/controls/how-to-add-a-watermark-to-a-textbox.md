---
title: 'Instrukcje: Dodawanie znaku wodnego do kontrolki TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923576"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="331e5-102">Instrukcje: Dodawanie znaku wodnego do kontrolki TextBox</span><span class="sxs-lookup"><span data-stu-id="331e5-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="331e5-103">Poniższy przykład przedstawia sposób ułatwienia użyteczności <xref:System.Windows.Controls.TextBox> przez wyświetlanie obrazu tła wyjaśniającego wewnątrz <xref:System.Windows.Controls.TextBox> elementu do momentu, w którym użytkownik wprowadza tekst.</span><span class="sxs-lookup"><span data-stu-id="331e5-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="331e5-104">Ponadto obraz tła jest przywracany ponownie, jeśli użytkownik usunie swoje dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="331e5-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="331e5-105">Zobacz ilustrację poniżej.</span><span class="sxs-lookup"><span data-stu-id="331e5-105">See illustration below.</span></span>  
  
 <span data-ttu-id="331e5-106">![Pole tekstowe z obrazem tła](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="331e5-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="331e5-107">Przyczyną tego przykładu jest użycie obrazu tła w tym przykładzie <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox>, a dopiero po prostu manipulowanie właściwością, polega na tym, że obraz tła nie zakłóca powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="331e5-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="331e5-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="331e5-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="331e5-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="331e5-109">See also</span></span>

- [<span data-ttu-id="331e5-110">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="331e5-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="331e5-111">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="331e5-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
