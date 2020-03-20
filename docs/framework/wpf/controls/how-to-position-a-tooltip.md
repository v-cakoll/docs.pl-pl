---
title: Jak ustawić położenie ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186948"
---
# <a name="how-to-position-a-tooltip"></a>Jak ustawić położenie ToolTip
W tym przykładzie pokazano, jak określić położenie etykietki narzędzia na ekranie.  
  
## <a name="example"></a>Przykład  
 Etykietkę narzędzia można umieścić przy użyciu zestawu pięciu właściwości, <xref:System.Windows.Controls.ToolTip> które <xref:System.Windows.Controls.ToolTipService> są zdefiniowane zarówno w klasach, jak i klasach. W poniższej tabeli przedstawiono te dwa zestawy pięciu właściwości i zawiera łącza do ich dokumentacji referencyjnej zgodnie z klasą.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Odpowiednie właściwości etykietki narzędzia zgodnie z klasą  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>właściwości klasy|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>właściwości klasy|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Jeśli zawartość etykietki narzędzia zostanie zdefiniowana przy użyciu <xref:System.Windows.Controls.ToolTip> obiektu, można użyć właściwości jednej z klas; jednak <xref:System.Windows.Controls.ToolTipService> właściwości mają pierwszeństwo. <xref:System.Windows.Controls.ToolTipService> Właściwości służą do etykietek narzędzi, które <xref:System.Windows.Controls.ToolTip> nie są zdefiniowane jako obiekty.  
  
 Na poniższych ilustracjach pokazano, jak umieścić etykietkę narzędzia przy użyciu tych właściwości. Chociaż przykłady na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tych ilustracjach pokazują, jak ustawić właściwości, <xref:System.Windows.Controls.ToolTip> które są zdefiniowane <xref:System.Windows.Controls.ToolTipService> przez klasę, odpowiednie właściwości klasy są zgodne z tymi samymi regułami układu. Aby uzyskać więcej informacji na temat możliwych wartości właściwości Umieszczanie, zobacz [Zachowanie umieszczania wyskakujących](popup-placement-behavior.md)okienków .  

 Na poniższej ilustracji przedstawiono położenie etykietki narzędzia przy użyciu właściwości Placement:  
  
 ![Diagram przedstawiający położenie etykietek narzędzi przy użyciu właściwości Placement.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 Na poniższej ilustracji przedstawiono położenie etykietki narzędzia przy użyciu właściwości Placement i PlacementRectangle:

 ![Diagram przedstawiający położenie etykietki narzędzi przy użyciu właściwości PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 Na poniższej ilustracji przedstawiono położenie etykietki narzędzia przy użyciu właściwości Położenie, Rozmieszczenie i Przesunięcie:
  
 ![Diagram przedstawiający położenie etykietek narzędzi przy użyciu właściwości Przesunięcie.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 W poniższym przykładzie <xref:System.Windows.Controls.ToolTip> pokazano, jak użyć właściwości, aby określić <xref:System.Windows.Controls.ToolTip> położenie etykietki narzędzia, której zawartość jest obiektem.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 W poniższym przykładzie <xref:System.Windows.Controls.ToolTipService> pokazano, jak użyć właściwości, aby określić <xref:System.Windows.Controls.ToolTip> położenie etykietki narzędzia, której zawartość nie jest obiektem.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tematy in jakże](tooltip-how-to-topics.md)
- [ToolTip — Przegląd](tooltip-overview.md)
