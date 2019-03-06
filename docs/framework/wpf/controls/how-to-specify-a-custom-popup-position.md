---
title: 'Instrukcje: Określ niestandardowe położenie okna podręcznego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 2ffba3d1a0fee236f803dd5877d541084192418b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358486"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="9cab5-102">Instrukcje: Określ niestandardowe położenie okna podręcznego</span><span class="sxs-lookup"><span data-stu-id="9cab5-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="9cab5-103">W tym przykładzie pokazano, jak określić niestandardowe położenie <xref:System.Windows.Controls.Primitives.Popup> decyduje o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="9cab5-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cab5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cab5-104">Example</span></span>  
 <span data-ttu-id="9cab5-105">Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> wywołuje zdefiniowane wystąpienie <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegować.</span><span class="sxs-lookup"><span data-stu-id="9cab5-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="9cab5-106">Ten delegat zwraca zestaw możliwych punktów, które są względne wobec lewym górnym rogu w obszarze docelowym i górnym lewym rogu <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="9cab5-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="9cab5-107"><xref:System.Windows.Controls.Primitives.Popup> Umieszczania występuje w momencie, który zapewnia widoczność najlepsze.</span><span class="sxs-lookup"><span data-stu-id="9cab5-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="9cab5-108">Poniższy przykład pokazuje jak zdefiniować położenie <xref:System.Windows.Controls.Primitives.Popup> , ustawiając <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="9cab5-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="9cab5-109">Pokazano również, jak utworzyć i przypisać <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata w celu umieść <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="9cab5-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="9cab5-110">Delegat wywołania zwrotnego zwraca dwa <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="9cab5-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="9cab5-111">Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryta przez krawędzi ekranu, na pierwszym miejscu <xref:System.Windows.Controls.Primitives.Popup> jest umieszczany na drugim miejscu.</span><span class="sxs-lookup"><span data-stu-id="9cab5-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="9cab5-112">Aby uzyskać pełny przykład, zobacz [przykładowe położenia okna podręcznego](https://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="9cab5-112">For the complete sample, see [Popup Placement Sample](https://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cab5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cab5-113">See also</span></span>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="9cab5-114">Okno podręczne — omówienie</span><span class="sxs-lookup"><span data-stu-id="9cab5-114">Popup Overview</span></span>](popup-overview.md)
- [<span data-ttu-id="9cab5-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9cab5-115">How-to Topics</span></span>](popup-how-to-topics.md)
