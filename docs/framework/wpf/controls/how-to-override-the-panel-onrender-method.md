---
title: 'Instrukcje: Zastępowanie metody OnRender panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666714"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="5854e-102">Instrukcje: Zastępowanie metody OnRender panelu</span><span class="sxs-lookup"><span data-stu-id="5854e-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="5854e-103">Ten przykład pokazuje, <xref:System.Windows.Controls.Panel.OnRender%2A> jak zastąpić <xref:System.Windows.Controls.Panel> metodę w celu dodania niestandardowych efektów graficznych do elementu układu.</span><span class="sxs-lookup"><span data-stu-id="5854e-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5854e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5854e-104">Example</span></span>  
 <span data-ttu-id="5854e-105">Użyj metody <xref:System.Windows.Controls.Panel.OnRender%2A> , aby dodać efekty graficzne do renderowanego elementu panelu.</span><span class="sxs-lookup"><span data-stu-id="5854e-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="5854e-106">Na przykład można użyć tej metody, aby dodać obramowanie niestandardowe lub efekty tła.</span><span class="sxs-lookup"><span data-stu-id="5854e-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="5854e-107"><xref:System.Windows.Media.DrawingContext> Obiekt jest przekazaniem jako argument, który zapewnia metody rysowania kształtów, tekstu, obrazów lub filmów wideo.</span><span class="sxs-lookup"><span data-stu-id="5854e-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="5854e-108">W związku z tym ta metoda jest przydatna do dostosowywania obiektu panelu.</span><span class="sxs-lookup"><span data-stu-id="5854e-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5854e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5854e-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="5854e-110">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="5854e-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="5854e-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="5854e-111">How-to Topics</span></span>](panel-how-to-topics.md)
