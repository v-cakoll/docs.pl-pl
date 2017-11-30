---
title: "Jak przeprowadzać test trafienia przy użyciu geometrii jako parametru"
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
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 32feb70a3b7a44a5a48f57fc2ecee912de4d39ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Jak przeprowadzać test trafienia przy użyciu geometrii jako parametru
W tym przykładzie przedstawiono sposób wykonywania testu trafienia na obiekt wizualny przy użyciu <xref:System.Windows.Media.Geometry> jako trafienie testowania parametru.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konfigurowane za pomocą testu trafienia <xref:System.Windows.Media.GeometryHitTestParameters> dla <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. <xref:System.Windows.Point> Wartość, która została przekazana do `OnMouseDown` metoda służy do tworzenia <xref:System.Windows.Media.Geometry> obiekt, aby rozszerzyć zakres testu trafienia.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Właściwość <xref:System.Windows.Media.GeometryHitTestResult> zawiera informacje o wynikach testu trafienia, która używa <xref:System.Windows.Media.Geometry> jako trafienie testowania parametru. Na poniższej ilustracji przedstawiono relacje między geometrii testu trafienia (niebieskie koło) a renderowanej zawartości obiektu visual docelowego (czerwonego kwadratu).  
  
 ![Testowanie trafień Diagram właściwości IntersectionDetail użytej w](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")  
Przecięcia testu trafienia geometrii i obiekt docelowy obiekt wizualny  
  
 Poniższy przykład przedstawia sposób wykonania testu trafienia wywołanie zwrotne po <xref:System.Windows.Media.Geometry> jest używany jako parametr testu trafienia. `result` Parametru jest rzutowane na <xref:System.Windows.Media.GeometryHitTestResult> Aby pobrać wartość <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> właściwości. Wartość właściwości pozwala określić, czy <xref:System.Windows.Media.Geometry> parametru testu trafienia pełni lub częściowo zawarty w renderowanej zawartości elementu docelowego testu trafienia. W takim przypadku przykładowy kod jest tylko dodawanie wyników testu trafienia na liście elementy wizualne znajdujące się całkowicie w obrębie granicy docelowej.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult> Wywołania zwrotnego nie powinna być wywoływana, gdy szczegół przecięcia <xref:System.Windows.Media.IntersectionDetail.Empty>.  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie w warstwie Visual trafień](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Trafienia geometrii testu w element wizualny](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
