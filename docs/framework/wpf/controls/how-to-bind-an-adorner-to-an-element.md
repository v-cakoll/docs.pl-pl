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
ms.openlocfilehash: b6909fec466c2b31a7f4156c43b21a0c724f0217
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018973"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="bf156-102">Instrukcje: Powiązywanie modułu definiowania układu z elementem</span><span class="sxs-lookup"><span data-stu-id="bf156-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="bf156-103">W tym przykładzie pokazano, jak programowo powiązać moduł definiowania układu do określonego <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="bf156-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf156-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf156-104">Example</span></span>  
 <span data-ttu-id="bf156-105">Aby powiązać moduł definiowania układu do określonego <xref:System.Windows.UIElement>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="bf156-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="bf156-106">Wywołaj `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można pobrać <xref:System.Windows.Documents.AdornerLayer> dla obiektu <xref:System.Windows.UIElement> do być powiązany.</span><span class="sxs-lookup"><span data-stu-id="bf156-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="bf156-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> przeprowadza górę drzewa wizualnego, rozpoczynając od określonego **UIElement**i zwraca pierwszą warstwą moduł definiowania układu kodu znajdzie.</span><span class="sxs-lookup"><span data-stu-id="bf156-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="bf156-108">(Jeśli nie warstwy moduł definiowania układu kodu nie zostaną znalezione, metoda zwraca wartość null.)</span><span class="sxs-lookup"><span data-stu-id="bf156-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="bf156-109">Wywołaj <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z obiektem docelowym **UIElement**.</span><span class="sxs-lookup"><span data-stu-id="bf156-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="bf156-110">Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), aby <xref:System.Windows.Controls.TextBox> o nazwie *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="bf156-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="bf156-111">Za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać moduł definiowania układu z innego elementu nie jest obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bf156-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf156-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf156-112">See also</span></span>

- [<span data-ttu-id="bf156-113">Moduły indeksowania układu — omówienie</span><span class="sxs-lookup"><span data-stu-id="bf156-113">Adorners Overview</span></span>](adorners-overview.md)
