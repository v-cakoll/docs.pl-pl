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
ms.openlocfilehash: a431b78993d197dac99f0b6e365823acb295f0b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611636"
---
# <a name="how-to-create-a-3-d-scene"></a>Instrukcje: Tworzenie sceny 3D
Ten przykład przedstawia sposób tworzenia obiektu 3-D przypominającą prostego arkusz papieru, który został obrócony. A <xref:System.Windows.Controls.Viewport3D> wraz z następujące składniki zostaną użyte do utworzenia tego prostego sceny 3D:  
  
- Aparat jest tworzony przy użyciu <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Aparat fotograficzny Określa, jaka część Scena 3-w jest możliwy do wyświetlenia.  
  
- Siatka jest tworzone w celu określenia kształt obiektu 3-w (arkusz papieru) przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Materiał jest określony, będzie wyświetlana na powierzchni obiektu (gradientu liniowego w tym przykładzie), przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Zostanie utworzona przykuć uwagę na obiekt przy użyciu światła <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, jak utworzyć scenę 3-D w XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób tworzenia tych samych Scena 3-w kodzie proceduralnym.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Grafika 3D — przegląd](3-d-graphics-overview.md)
