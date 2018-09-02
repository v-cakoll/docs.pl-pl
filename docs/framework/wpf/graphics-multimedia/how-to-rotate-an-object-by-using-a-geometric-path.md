---
title: Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 6d6d21f3f7b609cb2933093a6990425deb39d4a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398151"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="8ec1f-102">Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej</span><span class="sxs-lookup"><span data-stu-id="8ec1f-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="8ec1f-103">W tym przykładzie pokazano, jak obrócić (Tabela przestawna) obiekt na ścieżce geometryczne, który jest definiowany przez <xref:System.Windows.Media.PathGeometry> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ec1f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ec1f-104">Example</span></span>  
 <span data-ttu-id="8ec1f-105">W poniższym przykładzie użyto trzy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów można przesuwać wzdłuż ścieżki geometrycznej.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="8ec1f-106">Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> mający zastosowanie do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="8ec1f-107">Animacja generuje wartości kąta.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-107">The animation generates angle values.</span></span> <span data-ttu-id="8ec1f-108">To sprawia, że prostokąt Obróć (Tabela przestawna) wzdłuż konturów ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="8ec1f-109">Animowanie dwa obiekty <xref:System.Windows.Media.TranslateTransform.X%2A> i <xref:System.Windows.Media.TranslateTransform.Y%2A> wartości <xref:System.Windows.Media.TranslateTransform> mający zastosowanie do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="8ec1f-110">Dokonają prostokąt, Przenieś poziomo i pionowo wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="8ec1f-111">Obracanie obiektu przy użyciu ścieżki geometrycznej innym sposobem jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu i ustaw jego <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="8ec1f-112">Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [Obracanie obiektu przy użyciu ścieżki geometrycznej (animacja Matrix)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="8ec1f-113">Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-113">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec1f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ec1f-114">See Also</span></span>  
 [<span data-ttu-id="8ec1f-115">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="8ec1f-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="8ec1f-116">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="8ec1f-116">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="8ec1f-117">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="8ec1f-117">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
