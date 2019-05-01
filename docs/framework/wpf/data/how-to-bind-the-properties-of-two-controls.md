---
title: 'Instrukcje: Powiązywanie właściwości dwóch kontrolek'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 332e8e0dfa30ff7aff27c95652f07446baf6511a
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809564"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="354d5-102">Instrukcje: Powiązywanie właściwości dwóch kontrolek</span><span class="sxs-lookup"><span data-stu-id="354d5-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="354d5-103">W tym przykładzie pokazano, jak powiązać z innego przy użyciu właściwości jeden formant skonkretyzowany <xref:System.Windows.Data.Binding.ElementName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="354d5-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="354d5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="354d5-104">Example</span></span>  
 <span data-ttu-id="354d5-105">Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Canvas> do <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="354d5-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="354d5-106">Właściwość <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="354d5-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="354d5-107">Podczas renderowania w tym przykładzie wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="354d5-107">When this example is rendered it looks like the following:</span></span>  
  
![Zrzut ekranu przedstawiający kombi zaznaczone pole z wartością zielony i zielony kwadrat.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="354d5-109">Właściwość target powiązania (w tym przykładzie <xref:System.Windows.Controls.Panel.Background%2A> właściwość) musi mieć właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="354d5-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="354d5-110">Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="354d5-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354d5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="354d5-111">See also</span></span>

- [<span data-ttu-id="354d5-112">Określanie obiektu źródłowego powiązania</span><span class="sxs-lookup"><span data-stu-id="354d5-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="354d5-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="354d5-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
