---
title: 'Jak: Przekształcanie skali modelu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111988"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a><span data-ttu-id="fb3e3-102">Jak: Przekształcanie skali modelu 3D</span><span class="sxs-lookup"><span data-stu-id="fb3e3-102">How to: Transform the Scale of a 3D Model</span></span>
<span data-ttu-id="fb3e3-103">W tym przykładzie pokazano, jak skalować obiekt 3D.</span><span class="sxs-lookup"><span data-stu-id="fb3e3-103">This example shows how to scale a 3D object.</span></span> <span data-ttu-id="fb3e3-104">Aby skalować obiekt 3D, użyj pliku <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="fb3e3-104">To scale a 3D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="fb3e3-105">Obiekt <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> i właściwości zmienić rozmiar elementu według określonego współczynnika.</span><span class="sxs-lookup"><span data-stu-id="fb3e3-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="fb3e3-106">Na przykład <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> wartość 1,5 rozciąga obiekt do 150 procent jego pierwotnej szerokości.</span><span class="sxs-lookup"><span data-stu-id="fb3e3-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="fb3e3-107">Wartość <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> 0,5 zmniejsza wysokość obiektu o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="fb3e3-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="fb3e3-108">Poniższy kod pokazuje <xref:System.Windows.Media.Media3D.ScaleTransform3D> przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D>jako przekształcenie dla .</span><span class="sxs-lookup"><span data-stu-id="fb3e3-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="fb3e3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb3e3-109">Example</span></span>  
 <span data-ttu-id="fb3e3-110">Poniższy kod przedstawia cały przykład.</span><span class="sxs-lookup"><span data-stu-id="fb3e3-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fb3e3-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb3e3-111">See also</span></span>

- [<span data-ttu-id="fb3e3-112">Animowanie tłumaczeń 3D</span><span class="sxs-lookup"><span data-stu-id="fb3e3-112">Animate 3D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="fb3e3-113">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="fb3e3-113">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="fb3e3-114">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="fb3e3-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
