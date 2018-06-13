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
# <a name="how-to-create-a-3-d-scene"></a>Jak utworzyć scenę 3-D
W tym przykładzie przedstawiono sposób tworzenia 3-obiekt, który wygląda jak arkusz płaskiej papieru, który został obrócony. A <xref:System.Windows.Controls.Viewport3D> wraz z następujące składniki są używane do tworzenia tego prostego sceny 3:  
  
-   Aparat fotograficzny jest tworzony przy użyciu <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Aparat Określa, jaka część 3-sceny są widoczne.  
  
-   Siatki jest tworzone w celu określenia kształt 3-obiekt (arkusza) przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Określono materiału będzie wyświetlana na powierzchni obiektu (gradientu liniowego w tym przykładzie), za pomocą <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Światło utworzone zaprezentować przy użyciu obiektu <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób tworzenia sceny 3-w języku XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób tworzenia tej samej sceny 3-w procedurach kodu.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
