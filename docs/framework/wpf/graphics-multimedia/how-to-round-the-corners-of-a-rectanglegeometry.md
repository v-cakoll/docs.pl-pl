---
title: 'Instrukcje: Zaokrąglanie rogów elementu RectangleGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089136"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>Instrukcje: Zaokrąglanie rogów elementu RectangleGeometry
Aby zaokrąglić rogi <xref:System.Windows.Media.RectangleGeometry>, ustaw jego <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> właściwości na wartość większą niż zero. Większe wartości, bardziej okrągłe prostokąta.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kilka <xref:System.Windows.Media.RectangleGeometry> obiektów z różnymi <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ustawienia. <xref:System.Windows.Media.RectangleGeometry> Obiekty są wyświetlane przy użyciu <xref:System.Windows.Shapes.Path> elementów.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Prostokąty za pomocą różnych RadiusX&#47;RadiusY ustawienia](./media/graphicsmm-rounded.png "graphicsmm_rounded")  
Prostokąty z zaokrąglonymi narożnikami  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Geometria](geometry-overview.md)
- [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md)
- [Tworzenie kształtu przy użyciu elementu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
