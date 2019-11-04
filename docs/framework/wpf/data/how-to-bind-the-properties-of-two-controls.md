---
title: Jak powiązać właściwości dwóch formantów
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 66c759c28747de5b0288c906f5d51e4253fb7d52
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459168"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="bddf7-102">Jak powiązać właściwości dwóch formantów</span><span class="sxs-lookup"><span data-stu-id="bddf7-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="bddf7-103">Ten przykład pokazuje, jak powiązać Właściwość jednego wystąpienia kontrolki z inną przy użyciu właściwości <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="bddf7-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bddf7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bddf7-104">Example</span></span>  
 <span data-ttu-id="bddf7-105">Poniższy przykład pokazuje, jak powiązać Właściwość <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Canvas> z <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="bddf7-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="bddf7-106">Właściwość <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="bddf7-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="bddf7-107">Gdy ten przykład jest renderowany, wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="bddf7-107">When this example is rendered it looks like the following:</span></span>  
  
![Zrzut ekranu przedstawiający pole kombi z wybraną wartością zielony i zieloną kwadratową.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="bddf7-109">Właściwość Target powiązania (w tym przykładzie właściwość <xref:System.Windows.Controls.Panel.Background%2A>) musi być właściwością zależności.</span><span class="sxs-lookup"><span data-stu-id="bddf7-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="bddf7-110">Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bddf7-110">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bddf7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bddf7-111">See also</span></span>

- [<span data-ttu-id="bddf7-112">Określanie obiektu źródłowego powiązania</span><span class="sxs-lookup"><span data-stu-id="bddf7-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="bddf7-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="bddf7-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
