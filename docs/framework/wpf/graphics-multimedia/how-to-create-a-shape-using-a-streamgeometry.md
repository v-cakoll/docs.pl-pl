---
title: "Jak utworzyć kształt używając StreamGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: caa97d0dbd4c847892e164ecb168349c38f7f271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>Jak utworzyć kształt używając StreamGeometry
<xref:System.Windows.Media.StreamGeometry>jest lekki zamiast <xref:System.Windows.Media.PathGeometry> tworzenia kształtów geometrycznych. Użyj <xref:System.Windows.Media.StreamGeometry> potrzebne do opisywania złożonych geometry, ale nie chcesz koszty obsługi wiązania z danymi, animacji lub modyfikacji. Na przykład ze względu na jego wydajność <xref:System.Windows.Media.StreamGeometry> klasy jest dobrym rozwiązaniem dla opisu modułu definiowania układu kodu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto Składnia atrybutu, aby utworzyć trójkątny <xref:System.Windows.Media.StreamGeometry> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.StreamGeometry> atrybutu składni, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.  
  
## <a name="example"></a>Przykład  
 W następnym przykładzie użyto <xref:System.Windows.Media.StreamGeometry> do definiowania trójkąt w kodzie. Po pierwsze, w przykładzie jest tworzony <xref:System.Windows.Media.StreamGeometry>, następnie uzyskuje <xref:System.Windows.Media.StreamGeometryContext> i używa go do opisywania trójkąt.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 W następnym przykładzie jest tworzony metody, która używa <xref:System.Windows.Media.StreamGeometry> i <xref:System.Windows.Media.StreamGeometryContext> do definiowania kształtu geometrycznego na podstawie określonych parametrów.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [Tworzenie za pomocą PathGeometry kształtu](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [Omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
