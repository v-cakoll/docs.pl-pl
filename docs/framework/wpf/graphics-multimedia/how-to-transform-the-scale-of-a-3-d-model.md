---
title: Jak przekształcać skalę modelu 3-D
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 3cca1a210a7dbe410ebaacaaf89c08de8c31c40e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="95c2b-102">Jak przekształcać skalę modelu 3-D</span><span class="sxs-lookup"><span data-stu-id="95c2b-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="95c2b-103">Ten przykład przedstawia sposób skalowania 3-obiekt.</span><span class="sxs-lookup"><span data-stu-id="95c2b-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="95c2b-104">Aby skalować 3-obiekt, należy użyć <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="95c2b-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="95c2b-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, I <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> właściwości Zmień rozmiar elementu przez współczynnik określisz.</span><span class="sxs-lookup"><span data-stu-id="95c2b-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="95c2b-106">Na przykład <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> wartość 1.5 rozciąga się na 150 procent oryginalną szerokość obiektu.</span><span class="sxs-lookup"><span data-stu-id="95c2b-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="95c2b-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> wartość 0,5 zmniejsza wysokość obiektu 50 procent.</span><span class="sxs-lookup"><span data-stu-id="95c2b-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="95c2b-108">Poniższy kod przy użyciu <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformacji dla <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="95c2b-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="95c2b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="95c2b-109">Example</span></span>  
 <span data-ttu-id="95c2b-110">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="95c2b-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="95c2b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95c2b-111">See Also</span></span>  
 [<span data-ttu-id="95c2b-112">Animowanie przesunięcia 3D</span><span class="sxs-lookup"><span data-stu-id="95c2b-112">Animate 3-D Translations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [<span data-ttu-id="95c2b-113">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="95c2b-113">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="95c2b-114">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="95c2b-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
