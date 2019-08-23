---
title: 'Instrukcje: Powiązywanie modułu definiowania układu z elementem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923494"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="3a2ed-102">Instrukcje: Powiązywanie modułu definiowania układu z elementem</span><span class="sxs-lookup"><span data-stu-id="3a2ed-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="3a2ed-103">W tym przykładzie pokazano, jak programowo powiązać moduł definiowania układu z określonym <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a2ed-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a2ed-104">Example</span></span>  
 <span data-ttu-id="3a2ed-105">Aby powiązać moduł definiowania układu z konkretną <xref:System.Windows.UIElement>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3a2ed-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="3a2ed-106">Wywołaj `static` metodę <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> , aby <xref:System.Windows.Documents.AdornerLayer> uzyskaćobiekt<xref:System.Windows.UIElement> dla elementu do.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="3a2ed-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>wyszukuje drzewo wizualne, rozpoczynając od określonego elementu **UIElement**i zwraca początkową warstwę modułu definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="3a2ed-108">(Jeśli nie zostaną znalezione żadne warstwy modułu definiowania układu, metoda zwróci wartość null).</span><span class="sxs-lookup"><span data-stu-id="3a2ed-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="3a2ed-109">Wywołaj <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z docelowym elementem **UIElement**.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="3a2ed-110">Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej) z nazwanym <xref:System.Windows.Controls.TextBox> obiektem *TextBox*.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> <span data-ttu-id="3a2ed-111">Używanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do powiązania modułu definiowania układu z innym elementem nie jest obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a2ed-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a2ed-112">See also</span></span>

- [<span data-ttu-id="3a2ed-113">Moduły indeksowania układu — omówienie</span><span class="sxs-lookup"><span data-stu-id="3a2ed-113">Adorners Overview</span></span>](adorners-overview.md)
