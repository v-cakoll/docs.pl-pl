---
title: 'Instrukcje: Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923405"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Instrukcje: Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru
Ten przykład pokazuje, jak wykonać test trafień na obiekcie wizualizacji przy użyciu <xref:System.Windows.Media.Geometry> jako parametru testu trafień.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować test trafień za pomocą <xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> dla metody. Wartość, która jest przesyłana `OnMouseDown` do metody, <xref:System.Windows.Media.Geometry> jest używana do utworzenia obiektu w celu rozszerzenia zakresu testu trafień. <xref:System.Windows.Point>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 Właściwość zawiera informacje o wynikach testu <xref:System.Windows.Media.Geometry> trafień wykorzystujących jako parametr testu trafień. <xref:System.Windows.Media.GeometryHitTestResult> <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Na poniższej ilustracji przedstawiono relacje między geometrią testu trafień (niebieski okrąg) i renderowanej zawartości docelowego obiektu wizualizacji (czerwony kwadrat).  
  
 ![Diagram pokazujący IntersectionDetail używany podczas testowania trafień.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 Poniższy przykład pokazuje, jak zaimplementować wywołanie zwrotne testu trafień, <xref:System.Windows.Media.Geometry> gdy jest używany jako parametr testu trafień. Parametr jest rzutowany <xref:System.Windows.Media.GeometryHitTestResult> do w celu <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> pobrania wartości właściwości. `result` Wartość właściwości pozwala określić, czy <xref:System.Windows.Media.Geometry> parametr testu trafień jest w pełni lub częściowo zawarty w renderowanej zawartości docelowego testu trafień. W tym przypadku przykładowy kod dodaje tylko wyniki testów trafień do listy dla wizualizacji, które są w pełni zawarte w granicy docelowej.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> Nie należy wywoływać <xref:System.Windows.Media.IntersectionDetail.Empty> wywołaniazwrotnego,jeśliszczegółymiędzyczęściowe<xref:System.Windows.Media.HitTestResult> są.  
  
## <a name="see-also"></a>Zobacz także

- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
- [Przeprowadzanie testu trafienia geometrii w wizualizacji](how-to-hit-test-geometry-in-a-visual.md)
