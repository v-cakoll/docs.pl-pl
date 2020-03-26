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
# <a name="how-to-create-a-3d-scene"></a>Jak: Tworzenie sceny 3D
W tym przykładzie pokazano, jak utworzyć obiekt 3D, który wygląda jak płaski arkusz papieru, który został obrócony. A <xref:System.Windows.Controls.Viewport3D> wraz z następującymi składnikami są używane do tworzenia tej prostej sceny 3D:  
  
- Aparat jest tworzony <xref:System.Windows.Media.Media3D.PerspectiveCamera>przy użyciu pliku . Kamera określa, jaka część sceny 3D jest chywalna.  
  
- Siatka jest tworzona w celu określenia kształtu obiektu <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> 3D (arkusza papieru) przy użyciu właściwości <xref:System.Windows.Media.Media3D.GeometryModel3D>programu .  
  
- Materiał jest określony do wyświetlania na powierzchni obiektu (gradient liniowy w <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> tym <xref:System.Windows.Media.Media3D.GeometryModel3D>przykładzie) przy użyciu właściwości . .  
  
- Światło jest tworzone, aby świecić na obiekcie za pomocą <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, jak utworzyć scenę 3D w języku XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, jak utworzyć tę samą scenę 3D w kodzie proceduralnym.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie grafiki 3D](3-d-graphics-overview.md)
