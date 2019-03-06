---
title: 'Instrukcje: Przekształć skalę modelu 3-D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: afe18cea95be945313ef78a690c58950a3fff9b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378785"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="b3e5d-102">Instrukcje: Przekształć skalę modelu 3-D</span><span class="sxs-lookup"><span data-stu-id="b3e5d-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="b3e5d-103">Ten przykład przedstawia sposób skalowania obiektu 3D.</span><span class="sxs-lookup"><span data-stu-id="b3e5d-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="b3e5d-104">Aby skalować obiektu 3D, należy użyć <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="b3e5d-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="b3e5d-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, I <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> właściwości Zmień rozmiar elementu współczynnik określisz.</span><span class="sxs-lookup"><span data-stu-id="b3e5d-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="b3e5d-106">Na przykład <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> wartość 1.5 rozciąga obiekt, do 150 procent jego oryginalna szerokość.</span><span class="sxs-lookup"><span data-stu-id="b3e5d-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="b3e5d-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> wartość 0,5 zmniejsza wysokość obiektu o 50%.</span><span class="sxs-lookup"><span data-stu-id="b3e5d-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="b3e5d-108">Poniższy kod przy użyciu <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformację dla <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="b3e5d-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="b3e5d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3e5d-109">Example</span></span>  
 <span data-ttu-id="b3e5d-110">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="b3e5d-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b3e5d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3e5d-111">See also</span></span>
- [<span data-ttu-id="b3e5d-112">Animowanie przesunięcia 3D</span><span class="sxs-lookup"><span data-stu-id="b3e5d-112">Animate 3-D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="b3e5d-113">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="b3e5d-113">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="b3e5d-114">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="b3e5d-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
