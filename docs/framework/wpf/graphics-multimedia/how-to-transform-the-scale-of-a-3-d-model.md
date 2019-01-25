---
title: 'Instrukcje: Przekształć skalę modelu 3-D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 13f718451cb1b753a41304efde7db55360d3f687
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672898"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="df07d-102">Instrukcje: Przekształć skalę modelu 3-D</span><span class="sxs-lookup"><span data-stu-id="df07d-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="df07d-103">Ten przykład przedstawia sposób skalowania obiektu 3D.</span><span class="sxs-lookup"><span data-stu-id="df07d-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="df07d-104">Aby skalować obiektu 3D, należy użyć <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="df07d-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="df07d-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, I <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> właściwości Zmień rozmiar elementu współczynnik określisz.</span><span class="sxs-lookup"><span data-stu-id="df07d-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="df07d-106">Na przykład <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> wartość 1.5 rozciąga obiekt, do 150 procent jego oryginalna szerokość.</span><span class="sxs-lookup"><span data-stu-id="df07d-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="df07d-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> wartość 0,5 zmniejsza wysokość obiektu o 50%.</span><span class="sxs-lookup"><span data-stu-id="df07d-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="df07d-108">Poniższy kod przy użyciu <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformację dla <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="df07d-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="df07d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="df07d-109">Example</span></span>  
 <span data-ttu-id="df07d-110">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="df07d-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="df07d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df07d-111">See also</span></span>
- [<span data-ttu-id="df07d-112">Animowanie przesunięcia 3D</span><span class="sxs-lookup"><span data-stu-id="df07d-112">Animate 3-D Translations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)
- [<span data-ttu-id="df07d-113">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="df07d-113">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="df07d-114">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="df07d-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
