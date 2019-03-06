---
title: 'Instrukcje: Powiąż właściwości dwóch formantów'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: f3355969d0f12f0f3ed9b49bdb7efa6913c5e4c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372103"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="627d7-102">Instrukcje: Powiąż właściwości dwóch formantów</span><span class="sxs-lookup"><span data-stu-id="627d7-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="627d7-103">W tym przykładzie pokazano, jak powiązać z innego przy użyciu właściwości jeden formant skonkretyzowany <xref:System.Windows.Data.Binding.ElementName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="627d7-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="627d7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="627d7-104">Example</span></span>  
 <span data-ttu-id="627d7-105">Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Canvas> do <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="627d7-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="627d7-106">Właściwość <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="627d7-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="627d7-107">Podczas renderowania w tym przykładzie wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="627d7-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="627d7-108">![Kanwa zielonym tle](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="627d7-108">![A canvas with a green background](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="627d7-109">**Uwaga** właściwość target powiązania (w tym przykładzie <xref:System.Windows.Controls.Panel.Background%2A> właściwość) musi mieć właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="627d7-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="627d7-110">Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="627d7-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="627d7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="627d7-111">See also</span></span>
- [<span data-ttu-id="627d7-112">Określanie obiektu źródłowego powiązania</span><span class="sxs-lookup"><span data-stu-id="627d7-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="627d7-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="627d7-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
