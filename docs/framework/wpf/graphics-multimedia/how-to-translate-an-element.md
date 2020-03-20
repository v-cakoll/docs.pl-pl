---
title: Jak przesunąć element
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: ba6bda09a4ee189cdd1a32eed8f65b32d1a9abe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187305"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="8e468-102">Jak przesunąć element</span><span class="sxs-lookup"><span data-stu-id="8e468-102">How to: Translate an Element</span></span>
<span data-ttu-id="8e468-103">W tym przykładzie pokazano, jak przetłumaczyć (przenieść) element za pomocą . <xref:System.Windows.Media.TranslateTransform></span><span class="sxs-lookup"><span data-stu-id="8e468-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="8e468-104">Klasa <xref:System.Windows.Media.TranslateTransform> jest szczególnie przydatna w przypadku ruchomych elementów wewnątrz paneli, które nie obsługują pozycjonowania bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="8e468-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="8e468-105">Na przykład, stosując <xref:System.Windows.Media.TranslateTransform> a <xref:System.Windows.UIElement.RenderTransform%2A> do właściwości elementu, można przenieść <xref:System.Windows.Controls.StackPanel> element <xref:System.Windows.Controls.DockPanel>w obrębie lub .</span><span class="sxs-lookup"><span data-stu-id="8e468-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="8e468-106">Użyj <xref:System.Windows.Media.TranslateTransform.X%2A> właściwości, <xref:System.Windows.Media.TranslateTransform> aby określić ilość w pikselach, aby przenieść element wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="8e468-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="8e468-107">Użyj <xref:System.Windows.Media.TranslateTransform.Y%2A> właściwości, aby określić ilość w pikselach, aby przenieść element wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="8e468-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="8e468-108">Na koniec zastosuj <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="8e468-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="8e468-109">W poniższym przykładzie użyto a, <xref:System.Windows.Media.TranslateTransform> aby przenieść element 50 pikseli w prawo i 50 pikseli w dół.</span><span class="sxs-lookup"><span data-stu-id="8e468-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e468-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e468-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="8e468-111">Aby uzyskać pełną próbkę, zobacz [przykład przekształca 2-W](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="8e468-111">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e468-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e468-112">See also</span></span>

- [<span data-ttu-id="8e468-113">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="8e468-113">Transforms Overview</span></span>](transforms-overview.md)
