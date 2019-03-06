---
title: 'Instrukcje: Twórz połączone geometrie'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364791"
---
# <a name="how-to-create-a-combined-geometry"></a>Instrukcje: Twórz połączone geometrie
W tym przykładzie pokazano, jak połączyć geometrii. Aby połączyć dwa geometrii, należy użyć <xref:System.Windows.Media.CombinedGeometry> obiektu. Ustaw jego <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> właściwości za pomocą dwóch geometrii, łączyć, a następnie ustaw <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> właściwość, która określa, jak geometrii będą połączone ze sobą, aby `Union`, `Intersect`, `Exclude`, lub `Xor`.  
  
 Aby utworzyć geometrii złożonego z co najmniej dwóch geometrii, użyj <xref:System.Windows.Media.GeometryGroup>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenie geometrii `Exclude`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Wyłącz wyniki użycia trybu łączenia](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
Wyklucz połączone Geometrie  
  
 W niej następujące znaczniki <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenia `Intersect`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![Wyniki INTERSECT połączyć tryb](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
Intersect połączone Geometrie  
  
 W niej następujące znaczniki <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenia `Union`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Wyniki Unii połączyć tryb](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
Unia połączone Geometrie  
  
 W niej następujące znaczniki <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenia `Xor`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Wyniki Xor użycia trybu łączenia](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Xor połączone Geometrie
