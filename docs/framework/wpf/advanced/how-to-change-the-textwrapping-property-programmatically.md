---
title: 'Instrukcje: Zmień właściwość TextWrapping za pomocą programowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 70dc73fe16ebb98e466c4363e5ac26562329dcd4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362269"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="55974-102">Instrukcje: Zmień właściwość TextWrapping za pomocą programowania</span><span class="sxs-lookup"><span data-stu-id="55974-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="55974-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="55974-103">Example</span></span>  
 <span data-ttu-id="55974-104">Poniższy przykład kodu pokazuje, jak zmienić wartość <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> właściwość programowo.</span><span class="sxs-lookup"><span data-stu-id="55974-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="55974-105">Trzy <xref:System.Windows.Controls.Button> elementy są umieszczane w ramach <xref:System.Windows.Controls.StackPanel> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55974-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="55974-106">Każdy <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie <xref:System.Windows.Controls.Button> odpowiada za pomocą programu obsługi zdarzeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="55974-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="55974-107">Programy obsługi zdarzeń Użyj taką samą nazwę jak <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> wartości będą one dotyczyć `txt2` po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="55974-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="55974-108">Ponadto tekstu w `txt1` ( <xref:System.Windows.Controls.TextBlock> nie są wyświetlane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) zostanie zaktualizowany w celu odzwierciedlenia zmiany we właściwości.</span><span class="sxs-lookup"><span data-stu-id="55974-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="55974-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55974-109">See also</span></span>
- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
