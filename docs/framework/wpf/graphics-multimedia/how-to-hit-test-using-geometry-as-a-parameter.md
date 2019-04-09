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
ms.openlocfilehash: 73420d6ae1386676ed900e91b3951df9e0934db8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100967"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Instrukcje: Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru
W tym przykładzie pokazano, jak przeprowadzić test trafień na obiekt wizualny przy użyciu <xref:System.Windows.Media.Geometry> jako hit test parametru.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować test trafień za pomocą <xref:System.Windows.Media.GeometryHitTestParameters> dla <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. <xref:System.Windows.Point> Wartość, która jest przekazywana do `OnMouseDown` metoda służy do tworzenia <xref:System.Windows.Media.Geometry> obiektu, aby rozszerzyć zakres testu trafienia.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Właściwość <xref:System.Windows.Media.GeometryHitTestResult> zawiera informacje o wynikach hit test, który używa <xref:System.Windows.Media.Geometry> jako hit test parametru. Poniższa ilustracja przedstawia relację między testu trafienia geometrii (jasnoniebieski okrąg) i renderowanej zawartości visual obiektu docelowego (czerwony kwadrat).  
  
 ![Diagram pokazujący właściwości IntersectionDetail użytej podczas testowania trafień.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 Poniższy przykład pokazuje, jak zaimplementować wywołanie zwrotne testu trafienia przy <xref:System.Windows.Media.Geometry> jest używany jako parametr testu trafienia. `result` Parametru jest rzutowany na <xref:System.Windows.Media.GeometryHitTestResult> w celu pobierania wartości <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> właściwości. Wartość właściwości służy do określenia, czy <xref:System.Windows.Media.Geometry> parametru test trafień jest całkowicie lub częściowo zawarty w renderowanej zawartości elementu docelowego testu trafienia. W takim przypadku przykładowy kod jest dodawanie wyników testu trafienia do listy elementów wizualnych, które są w pełni zawarte w obrębie docelowego.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult> Wywołanie zwrotne nie powinna być wywoływana po szczegóły wspólną <xref:System.Windows.Media.IntersectionDetail.Empty>.  
  
## <a name="see-also"></a>Zobacz także

- [Test trafienia w warstwie Visual](hit-testing-in-the-visual-layer.md)
- [Przeprowadzanie testu trafienia geometrii w wizualizacji](how-to-hit-test-geometry-in-a-visual.md)
