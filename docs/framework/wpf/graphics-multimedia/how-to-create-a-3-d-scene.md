---
title: Jak utworzyć scenę 3-D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: e3c2ea803961ca57606f8ea8bec21d50a38dbe1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559529"
---
# <a name="how-to-create-a-3-d-scene"></a><span data-ttu-id="93097-102">Jak utworzyć scenę 3-D</span><span class="sxs-lookup"><span data-stu-id="93097-102">How to: Create a 3-D Scene</span></span>
<span data-ttu-id="93097-103">W tym przykładzie przedstawiono sposób tworzenia 3-obiekt, który wygląda jak arkusz płaskiej papieru, który został obrócony.</span><span class="sxs-lookup"><span data-stu-id="93097-103">This example shows how to create a 3-D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="93097-104">A <xref:System.Windows.Controls.Viewport3D> wraz z następujące składniki są używane do tworzenia tego prostego sceny 3:</span><span class="sxs-lookup"><span data-stu-id="93097-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3-D scene:</span></span>  
  
-   <span data-ttu-id="93097-105">Aparat fotograficzny jest tworzony przy użyciu <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="93097-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="93097-106">Aparat Określa, jaka część 3-sceny są widoczne.</span><span class="sxs-lookup"><span data-stu-id="93097-106">The camera specifies what part of the 3-D scene is viewable.</span></span>  
  
-   <span data-ttu-id="93097-107">Siatki jest tworzone w celu określenia kształt 3-obiekt (arkusza) przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="93097-107">A mesh is created to specify the shape of 3-D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="93097-108">Określono materiału będzie wyświetlana na powierzchni obiektu (gradientu liniowego w tym przykładzie), za pomocą <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="93097-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="93097-109">Światło utworzone zaprezentować przy użyciu obiektu <xref:System.Windows.Media.Media3D.DirectionalLight>.</span><span class="sxs-lookup"><span data-stu-id="93097-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93097-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="93097-110">Example</span></span>  
 <span data-ttu-id="93097-111">Poniższy kod przedstawia sposób tworzenia sceny 3-w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="93097-111">The code below shows how to create a 3-D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="93097-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="93097-112">Example</span></span>  
 <span data-ttu-id="93097-113">Poniższy kod przedstawia sposób tworzenia tej samej sceny 3-w procedurach kodu.</span><span class="sxs-lookup"><span data-stu-id="93097-113">The code below shows how to create the same 3-D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="93097-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93097-114">See Also</span></span>  
 [<span data-ttu-id="93097-115">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="93097-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
