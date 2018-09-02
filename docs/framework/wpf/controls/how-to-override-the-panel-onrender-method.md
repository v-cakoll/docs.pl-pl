---
title: Jak zastąpić metodę panela OnRender
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
ms.openlocfilehash: 8f3b65bdfe96efdc57c6b8d30991439d3bdb0bc5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404439"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="1dcba-102">Jak zastąpić metodę panela OnRender</span><span class="sxs-lookup"><span data-stu-id="1dcba-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="1dcba-103">Ten przykład przedstawia sposób przesłonięcia <xref:System.Windows.Controls.Panel.OnRender%2A> metody <xref:System.Windows.Controls.Panel> celu stosowanie efektów niestandardowych graficznego elementu układu.</span><span class="sxs-lookup"><span data-stu-id="1dcba-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dcba-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dcba-104">Example</span></span>  
 <span data-ttu-id="1dcba-105">Użyj <xref:System.Windows.Controls.Panel.OnRender%2A> metody, aby można było dodać efekty graficzne do elementu renderowanego panelu.</span><span class="sxs-lookup"><span data-stu-id="1dcba-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="1dcba-106">Na przykład służy tej metody można dodać obramowanie niestandardowe lub efekty w tle.</span><span class="sxs-lookup"><span data-stu-id="1dcba-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="1dcba-107">A <xref:System.Windows.Media.DrawingContext> obiekt jest przekazywany jako argument, który udostępnia metody do rysowania kształtów, tekstu, obrazów lub wideo.</span><span class="sxs-lookup"><span data-stu-id="1dcba-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="1dcba-108">W rezultacie ta metoda jest przydatna do dostosowywania obiektów panel.</span><span class="sxs-lookup"><span data-stu-id="1dcba-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1dcba-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1dcba-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="1dcba-110">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="1dcba-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="1dcba-111">Przykładowe niestandardowe panelu promieniowego</span><span class="sxs-lookup"><span data-stu-id="1dcba-111">Custom Radial Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159982)  
 [<span data-ttu-id="1dcba-112">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1dcba-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
