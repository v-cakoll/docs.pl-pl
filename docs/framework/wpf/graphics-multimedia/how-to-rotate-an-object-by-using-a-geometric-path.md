---
title: "Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 078d1054f9b6a4c2f6172f00aa8c4ad9077e6db2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="8ff8f-102">Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej</span><span class="sxs-lookup"><span data-stu-id="8ff8f-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="8ff8f-103">W tym przykładzie pokazano, jak Obróć (Tabela przestawna) obiektu wzdłuż ścieżki geometryczne, która jest definiowana za pomocą <xref:System.Windows.Media.PathGeometry> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ff8f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ff8f-104">Example</span></span>  
 <span data-ttu-id="8ff8f-105">W poniższym przykładzie użyto trzy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów, które można przesuwać ścieżce geometrycznej.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="8ff8f-106">Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> do prostokąta zastosowano.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="8ff8f-107">Animacja generuje wartości kąta.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-107">The animation generates angle values.</span></span> <span data-ttu-id="8ff8f-108">Powoduje to dodanie prostokąta Obróć (Tabela przestawna) wzdłuż konturów ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="8ff8f-109">Dwa obiekty animować <xref:System.Windows.Media.TranslateTransform.X%2A> i <xref:System.Windows.Media.TranslateTransform.Y%2A> wartości <xref:System.Windows.Media.TranslateTransform> do prostokąta zastosowano.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="8ff8f-110">Finalizowania prostokąt Przenieś poziomie i w pionie na ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="8ff8f-111">Obracanie obiektu przy użyciu ścieżki geometrycznych na innym sposobem jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu i ustawić jej <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="8ff8f-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="8ff8f-112">Aby uzyskać więcej informacji i przykład zobacz [Obracanie obiektu przy użyciu ścieżki geometrycznych (macierzy Animacja)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="8ff8f-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="8ff8f-113">Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="8ff8f-113">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff8f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ff8f-114">See Also</span></span>  
 [<span data-ttu-id="8ff8f-115">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="8ff8f-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="8ff8f-116">Ścieżka animacji próbki</span><span class="sxs-lookup"><span data-stu-id="8ff8f-116">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="8ff8f-117">Ścieżka animacji — tematy porad</span><span class="sxs-lookup"><span data-stu-id="8ff8f-117">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
