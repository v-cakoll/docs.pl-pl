---
title: 'Instrukcje: Zapisz, ładuj i drukuj zawartość RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- saving RichTextBox controls [WPF]
- printing RichTextBox controls [WPF]
- loading RichTextBox controls [WPF]
- RichTextBox control [WPF], saving
- RichTextBox control [WPF], printing
- RichTextBox control [WPF], loading
ms.assetid: ffb113d3-c68a-47ca-8ac0-882283f38326
ms.openlocfilehash: 90581bee7815dafd44c3cae18a8af7394fee1e9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072467"
---
# <a name="how-to-save-load-and-print-richtextbox-content"></a><span data-ttu-id="cb4a7-102">Instrukcje: Zapisz, ładuj i drukuj zawartość RichTextBox</span><span class="sxs-lookup"><span data-stu-id="cb4a7-102">How to: Save, Load, and Print RichTextBox Content</span></span>
<span data-ttu-id="cb4a7-103">Poniższy przykład pokazuje, jak można zapisać zawartości <xref:System.Windows.Controls.RichTextBox> do pliku, należy załadować tej zawartości wstecz do <xref:System.Windows.Controls.RichTextBox>i Drukuj zawartość.</span><span class="sxs-lookup"><span data-stu-id="cb4a7-103">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb4a7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb4a7-104">Example</span></span>  
 <span data-ttu-id="cb4a7-105">Oto znaczniki dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="cb4a7-105">Below is the markup for the example.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="cb4a7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb4a7-106">Example</span></span>  
 <span data-ttu-id="cb4a7-107">Poniżej znajduje się kod w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cb4a7-107">Below is the code behind for the example.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="cb4a7-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb4a7-108">See also</span></span>

- [<span data-ttu-id="cb4a7-109">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="cb4a7-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="cb4a7-110">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="cb4a7-110">TextBox Overview</span></span>](textbox-overview.md)
