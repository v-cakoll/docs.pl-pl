---
title: 'Instrukcje: Powiązywanie właściwości dwóch kontrolek'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 0dd7b817b632758cfca8b5c45d88e333510485f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222071"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="9ce2e-102">Instrukcje: Powiązywanie właściwości dwóch kontrolek</span><span class="sxs-lookup"><span data-stu-id="9ce2e-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="9ce2e-103">W tym przykładzie pokazano, jak powiązać z innego przy użyciu właściwości jeden formant skonkretyzowany <xref:System.Windows.Data.Binding.ElementName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ce2e-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce2e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ce2e-104">Example</span></span>  
 <span data-ttu-id="9ce2e-105">Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Canvas> do <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce2e-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.</span></span><xref:System.Windows.Controls.ContentControl.Content%2A> <span data-ttu-id="9ce2e-106">Właściwość <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="9ce2e-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="9ce2e-107">Podczas renderowania w tym przykładzie wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="9ce2e-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="9ce2e-108">![Kanwa zielonym tle](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="9ce2e-108">![A canvas with a green background](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="9ce2e-109">**Uwaga** właściwość target powiązania (w tym przykładzie <xref:System.Windows.Controls.Panel.Background%2A> właściwość) musi mieć właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="9ce2e-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="9ce2e-110">Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9ce2e-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce2e-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ce2e-111">See also</span></span>

- [<span data-ttu-id="9ce2e-112">Określanie obiektu źródłowego powiązania</span><span class="sxs-lookup"><span data-stu-id="9ce2e-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="9ce2e-113">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="9ce2e-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
