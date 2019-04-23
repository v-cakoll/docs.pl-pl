---
title: 'Instrukcje: Ustawianie położenia elementu ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 811818fe6e7c0d8ce9e2aa058b42bf592ada4b92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212352"
---
# <a name="how-to-position-a-tooltip"></a>Instrukcje: Ustawianie położenia elementu ToolTip
Ten przykład przedstawia sposób określania położenia etykietki narzędzia na ekranie.  
  
## <a name="example"></a>Przykład  
 Ustaw położenie tooltip korzystając z zestawu pięciu właściwości, które są zdefiniowane w obu <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> klasy. Poniższa tabela zawiera te dwa zestawy właściwości pięć oraz zawiera łącza do ich dokumentację referencyjną, zgodnie z klasy.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Odpowiednie właściwości etykietka narzędzia, zgodnie z klasy  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Właściwości klasy|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Właściwości klasy|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Możesz definiować zawartość etykietka narzędzia za pomocą <xref:System.Windows.Controls.ToolTip> obiektu, można użyć właściwości każdej klasy; jednak <xref:System.Windows.Controls.ToolTipService> właściwości mają pierwszeństwo. Użyj <xref:System.Windows.Controls.ToolTipService> właściwości dla etykietki narzędzi, które nie są zdefiniowane jako <xref:System.Windows.Controls.ToolTip> obiektów.  
  
 Na poniższych ilustracjach przedstawiono sposób położenie tooltip przy użyciu tych właściwości. Mimo że, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] te ilustracje przykładach w sposób ustawiania właściwości, które są definiowane przez <xref:System.Windows.Controls.ToolTip> klasy odpowiednie właściwości <xref:System.Windows.Controls.ToolTipService> klasy są zgodne z regułami układu. Aby uzyskać więcej informacji na temat możliwych wartości dla właściwości umieszczania, zobacz [zachowanie położenia okna podręcznego](popup-placement-behavior.md).  
 
 Na poniższej ilustracji przedstawiono położenia etykietki narzędzia, za pomocą właściwości umieszczania:  
  
 ![Diagram przedstawiający położenia etykietki narzędzia, za pomocą właściwości umieszczania.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 Na poniższej ilustracji przedstawiono położenia etykietki narzędzia, za pomocą właściwości umieszczania i PlacementRectangle:   

 ![Diagram przedstawiający położenia etykietki narzędzia, za pomocą właściwości PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 Na poniższej ilustracji przedstawiono położenia etykietki narzędzia, za pomocą właściwości Placement, PlacementRectangle i przesunięcie:   
  
 ![Diagram przedstawiający położenia etykietki narzędzia, za pomocą właściwości przesunięcie.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTip> właściwości, aby określić położenie tooltip, którego zawartość ma <xref:System.Windows.Controls.ToolTip> obiektu.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTipService> właściwości, aby określić położenie tooltip, którego zawartość nie jest <xref:System.Windows.Controls.ToolTip> obiektu.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tematy z instrukcjami](tooltip-how-to-topics.md)
- [ToolTip — omówienie](tooltip-overview.md)
