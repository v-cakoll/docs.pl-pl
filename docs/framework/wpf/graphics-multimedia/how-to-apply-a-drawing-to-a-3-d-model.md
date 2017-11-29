---
title: "Jak zastosować rysowanie do modelu 3-D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Jak zastosować rysowanie do modelu 3-D
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> dotyczą [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.  
  
 Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Jest ustawiony jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> właściwość <xref:System.Windows.Media.Media3D.DiffuseMaterial> stosowane do [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] płaszczyzny.  
  
 **Uwaga:** często jest to pożądane, aby zdefiniować złożone obiekty oraz wartości jak rysunek poniżej jako zasoby, które mogą być ponownie używane i uprościć kod. Zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) Aby uzyskać więcej informacji.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zasoby dla języka XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Utwórz 3-sceny](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Rysowanie obiekty — omówienie](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Przegląd grafiki 3-w](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
