---
title: Jak określić niestandardowe położenie okna podręcznego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635750"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="91733-102">Jak określić niestandardowe położenie okna podręcznego</span><span class="sxs-lookup"><span data-stu-id="91733-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="91733-103">W tym przykładzie pokazano, jak <xref:System.Windows.Controls.Primitives.Popup> określić <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> pozycję niestandardową formantu, gdy właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="91733-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91733-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="91733-104">Example</span></span>  
 <span data-ttu-id="91733-105">Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ustawiona na <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> wywołuje zdefiniowane wystąpienie pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="91733-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="91733-106">Ten pełnomocnik zwraca zestaw możliwych punktów, które są względem lewego górnego rogu obszaru <xref:System.Windows.Controls.Primitives.Popup>docelowego i lewego górnego rogu .</span><span class="sxs-lookup"><span data-stu-id="91733-106">This delegate returns a set of possible points that are relative to the top-left corner of the target area and the top-left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="91733-107">Umieszczenie <xref:System.Windows.Controls.Primitives.Popup> występuje w punkcie, który zapewnia najlepszą widoczność.</span><span class="sxs-lookup"><span data-stu-id="91733-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="91733-108">W poniższym przykładzie pokazano, <xref:System.Windows.Controls.Primitives.Popup> jak zdefiniować położenie a, ustawiając <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="91733-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="91733-109">Pokazuje również, jak utworzyć <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> i przypisać pełnomocnika <xref:System.Windows.Controls.Primitives.Popup>w celu umieszczenia pliku .</span><span class="sxs-lookup"><span data-stu-id="91733-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="91733-110">Pełnomocnik wywołania zwrotnego zwraca dwa <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> obiekty.</span><span class="sxs-lookup"><span data-stu-id="91733-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="91733-111">Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przez krawędź ekranu na <xref:System.Windows.Controls.Primitives.Popup> pierwszej pozycji, jest umieszczany na drugiej pozycji.</span><span class="sxs-lookup"><span data-stu-id="91733-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="91733-112">Aby uzyskać pełną próbkę, zobacz [Przykładu umieszczania wyskakujących okienków](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span><span class="sxs-lookup"><span data-stu-id="91733-112">For the complete sample, see [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91733-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91733-113">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="91733-114">Omówienie wyskakujących okienka</span><span class="sxs-lookup"><span data-stu-id="91733-114">Popup overview</span></span>](popup-overview.md)
- [<span data-ttu-id="91733-115">Artykuły do artykułów</span><span class="sxs-lookup"><span data-stu-id="91733-115">How-to articles</span></span>](popup-how-to-topics.md)
