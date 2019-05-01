---
title: 'Instrukcje: Tworzenie sceny 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 8e176cb437055787da86d56770dd71323134fa33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910185"
---
# <a name="how-to-create-a-3-d-scene"></a><span data-ttu-id="37af5-102">Instrukcje: Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="37af5-102">How to: Create a 3-D Scene</span></span>
<span data-ttu-id="37af5-103">Ten przykład przedstawia sposób tworzenia obiektu 3-D przypominającą prostego arkusz papieru, który został obrócony.</span><span class="sxs-lookup"><span data-stu-id="37af5-103">This example shows how to create a 3-D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="37af5-104">A <xref:System.Windows.Controls.Viewport3D> wraz z następujące składniki zostaną użyte do utworzenia tego prostego sceny 3D:</span><span class="sxs-lookup"><span data-stu-id="37af5-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3-D scene:</span></span>  
  
- <span data-ttu-id="37af5-105">Aparat jest tworzony przy użyciu <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="37af5-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="37af5-106">Aparat fotograficzny Określa, jaka część Scena 3-w jest możliwy do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="37af5-106">The camera specifies what part of the 3-D scene is viewable.</span></span>  
  
- <span data-ttu-id="37af5-107">Siatka jest tworzone w celu określenia kształt obiektu 3-w (arkusz papieru) przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="37af5-107">A mesh is created to specify the shape of 3-D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="37af5-108">Materiał jest określony, będzie wyświetlana na powierzchni obiektu (gradientu liniowego w tym przykładzie), przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="37af5-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="37af5-109">Zostanie utworzona przykuć uwagę na obiekt przy użyciu światła <xref:System.Windows.Media.Media3D.DirectionalLight>.</span><span class="sxs-lookup"><span data-stu-id="37af5-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37af5-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="37af5-110">Example</span></span>  
 <span data-ttu-id="37af5-111">Poniższy kod pokazuje, jak utworzyć scenę 3-D w XAML.</span><span class="sxs-lookup"><span data-stu-id="37af5-111">The code below shows how to create a 3-D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="37af5-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="37af5-112">Example</span></span>  
 <span data-ttu-id="37af5-113">Poniższy kod przedstawia sposób tworzenia tych samych Scena 3-w kodzie proceduralnym.</span><span class="sxs-lookup"><span data-stu-id="37af5-113">The code below shows how to create the same 3-D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="37af5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37af5-114">See also</span></span>

- [<span data-ttu-id="37af5-115">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="37af5-115">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
