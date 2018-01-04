---
title: "Jak tworzyć połączone geometrie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee77da00604b7e4965cc376748606b6bd0e92ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a>Jak tworzyć połączone geometrie
Ten przykład przedstawia sposób łączenia mają geometrię. Aby połączyć dwie mają geometrię, należy użyć <xref:System.Windows.Media.CombinedGeometry> obiektu. Ustaw jego <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> właściwości z dwóch geometrii, łączenie i ustawić <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> właściwość, która określa, jak mają geometrię zostaną połączone ze sobą, aby `Union`, `Intersect`, `Exclude`, lub `Xor`.  
  
 Aby utworzyć geometrii złożonego z dwóch lub więcej mają geometrię, użyj <xref:System.Windows.Media.GeometryGroup>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia geometrii z `Exclude`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Wyłącz wyniki użycia trybu łączenia](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
Wyklucz geometrii połączone  
  
 W następujących znaczników <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia z `Intersect`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![Wyniki INTERSECT połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
Łączna geometrii Intersect  
  
 W następujących znaczników <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia z `Union`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Wyniki Unii połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
Łączna geometrii Unii  
  
 W następujących znaczników <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia z `Xor`.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Wyniki Xor połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Xor geometrii połączone
