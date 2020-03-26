---
title: 'Jak: Tworzenie sceny 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112105"
---
# <a name="how-to-create-a-3d-scene"></a><span data-ttu-id="dbc2b-102">Jak: Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="dbc2b-102">How to: Create a 3D Scene</span></span>
<span data-ttu-id="dbc2b-103">W tym przykładzie pokazano, jak utworzyć obiekt 3D, który wygląda jak płaski arkusz papieru, który został obrócony.</span><span class="sxs-lookup"><span data-stu-id="dbc2b-103">This example shows how to create a 3D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="dbc2b-104">A <xref:System.Windows.Controls.Viewport3D> wraz z następującymi składnikami są używane do tworzenia tej prostej sceny 3D:</span><span class="sxs-lookup"><span data-stu-id="dbc2b-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3D scene:</span></span>  
  
- <span data-ttu-id="dbc2b-105">Aparat jest tworzony <xref:System.Windows.Media.Media3D.PerspectiveCamera>przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="dbc2b-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="dbc2b-106">Kamera określa, jaka część sceny 3D jest chywalna.</span><span class="sxs-lookup"><span data-stu-id="dbc2b-106">The camera specifies what part of the 3D scene is viewable.</span></span>  
  
- <span data-ttu-id="dbc2b-107">Siatka jest tworzona w celu określenia kształtu obiektu <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> 3D (arkusza papieru) przy użyciu właściwości <xref:System.Windows.Media.Media3D.GeometryModel3D>programu .</span><span class="sxs-lookup"><span data-stu-id="dbc2b-107">A mesh is created to specify the shape of 3D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="dbc2b-108">Materiał jest określony do wyświetlania na powierzchni obiektu (gradient liniowy w <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> tym <xref:System.Windows.Media.Media3D.GeometryModel3D>przykładzie) przy użyciu właściwości . .</span><span class="sxs-lookup"><span data-stu-id="dbc2b-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="dbc2b-109">Światło jest tworzone, aby świecić na obiekcie za pomocą <xref:System.Windows.Media.Media3D.DirectionalLight>.</span><span class="sxs-lookup"><span data-stu-id="dbc2b-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbc2b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbc2b-110">Example</span></span>  
 <span data-ttu-id="dbc2b-111">Poniższy kod pokazuje, jak utworzyć scenę 3D w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="dbc2b-111">The code below shows how to create a 3D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="dbc2b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbc2b-112">Example</span></span>  
 <span data-ttu-id="dbc2b-113">Poniższy kod pokazuje, jak utworzyć tę samą scenę 3D w kodzie proceduralnym.</span><span class="sxs-lookup"><span data-stu-id="dbc2b-113">The code below shows how to create the same 3D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="dbc2b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbc2b-114">See also</span></span>

- [<span data-ttu-id="dbc2b-115">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="dbc2b-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
