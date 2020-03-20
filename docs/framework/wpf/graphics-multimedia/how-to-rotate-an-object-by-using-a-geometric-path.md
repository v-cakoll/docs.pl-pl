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
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186874"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="c8ecf-102">Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej</span><span class="sxs-lookup"><span data-stu-id="c8ecf-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="c8ecf-103">W tym przykładzie pokazano, jak obrócić (obrócić) obiekt <xref:System.Windows.Media.PathGeometry> wzdłuż ścieżki geometrycznej zdefiniowanej przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8ecf-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8ecf-104">Example</span></span>  
 <span data-ttu-id="c8ecf-105">W poniższym przykładzie użyto trzech <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów do przesuń prostokąt wzdłuż ścieżki geometrycznej.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
- <span data-ttu-id="c8ecf-106">Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> a, który jest stosowany do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="c8ecf-107">Animacja generuje wartości kąta.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-107">The animation generates angle values.</span></span> <span data-ttu-id="c8ecf-108">To sprawia, że prostokąt obraca się (pivot) wzdłuż konturów ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
- <span data-ttu-id="c8ecf-109">Pozostałe dwa obiekty animują <xref:System.Windows.Media.TranslateTransform.X%2A> wartości i <xref:System.Windows.Media.TranslateTransform.Y%2A> wartości <xref:System.Windows.Media.TranslateTransform> a, które są stosowane do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="c8ecf-110">Sprawiają, że prostokąt porusza się poziomo i pionowo wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="c8ecf-111">Innym sposobem obracania obiektu za pomocą ścieżki geometrycznej jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu i ustawienie jego <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwości na `true`.</span><span class="sxs-lookup"><span data-stu-id="c8ecf-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="c8ecf-112">Aby uzyskać więcej informacji i przykład, zobacz [Obracanie obiektu przy użyciu ścieżki geometrycznej (animacja macierzy)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="c8ecf-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="c8ecf-113">Aby uzyskać pełną próbkę, zobacz [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="c8ecf-113">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ecf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8ecf-114">See also</span></span>

- [<span data-ttu-id="c8ecf-115">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="c8ecf-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="c8ecf-116">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="c8ecf-116">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="c8ecf-117">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c8ecf-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
