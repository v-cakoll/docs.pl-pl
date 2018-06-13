---
title: Jak zmienić właściwość TextWrapping za pomocą programowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 1b0f039f0484d1d1e73c3c12af06e0faffbce1cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543332"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="c897c-102">Jak zmienić właściwość TextWrapping za pomocą programowania</span><span class="sxs-lookup"><span data-stu-id="c897c-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="c897c-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="c897c-103">Example</span></span>  
 <span data-ttu-id="c897c-104">Poniższy przykładowy kod przedstawia sposób zmień wartość <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> właściwości programowo.</span><span class="sxs-lookup"><span data-stu-id="c897c-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="c897c-105">Trzy <xref:System.Windows.Controls.Button> elementy są umieszczane w <xref:System.Windows.Controls.StackPanel> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c897c-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="c897c-106">Każdy <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia dla <xref:System.Windows.Controls.Button> odpowiada program obsługi zdarzeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c897c-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="c897c-107">Programy obsługi zdarzeń, użyj takiej samej nazwie jak <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> wartość będzie dotyczyć `txt2` po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="c897c-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="c897c-108">Ponadto tekst w `txt1` ( <xref:System.Windows.Controls.TextBlock> nie są wyświetlane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) jest aktualizowana w celu odzwierciedlenia zmian we właściwości.</span><span class="sxs-lookup"><span data-stu-id="c897c-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c897c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c897c-109">See Also</span></span>  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
