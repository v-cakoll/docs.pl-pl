---
title: 'Instrukcje: Powiąż właściwości dwóch formantów'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 63584872c027ed3a80698304a7221c161c8d928a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570255"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="cf65c-102">Instrukcje: Powiąż właściwości dwóch formantów</span><span class="sxs-lookup"><span data-stu-id="cf65c-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="cf65c-103">W tym przykładzie pokazano, jak powiązać z innego przy użyciu właściwości jeden formant skonkretyzowany <xref:System.Windows.Data.Binding.ElementName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf65c-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf65c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf65c-104">Example</span></span>  
 <span data-ttu-id="cf65c-105">Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Canvas> do <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="cf65c-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="cf65c-106">Właściwość <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="cf65c-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="cf65c-107">Podczas renderowania w tym przykładzie wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="cf65c-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="cf65c-108">![Kanwa zielonym tle](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="cf65c-108">![A canvas with a green background](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="cf65c-109">**Uwaga** właściwość target powiązania (w tym przykładzie <xref:System.Windows.Controls.Panel.Background%2A> właściwość) musi mieć właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="cf65c-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="cf65c-110">Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf65c-110">For more information, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf65c-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf65c-111">See also</span></span>
- [<span data-ttu-id="cf65c-112">Określanie obiektu źródłowego powiązania</span><span class="sxs-lookup"><span data-stu-id="cf65c-112">Specify the Binding Source</span></span>](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)
- [<span data-ttu-id="cf65c-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="cf65c-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
