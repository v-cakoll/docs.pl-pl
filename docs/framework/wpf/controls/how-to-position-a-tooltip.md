---
title: 'Instrukcje: Ustaw położenie ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 403b070e782a6f243fd5a420e569daa02044dbb1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727706"
---
# <a name="how-to-position-a-tooltip"></a>Instrukcje: Ustaw położenie ToolTip
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
  
 Na poniższych ilustracjach przedstawiono sposób położenie tooltip przy użyciu tych właściwości. Mimo że, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] te ilustracje przykładach w sposób ustawiania właściwości, które są definiowane przez <xref:System.Windows.Controls.ToolTip> klasy odpowiednie właściwości <xref:System.Windows.Controls.ToolTipService> klasy są zgodne z regułami układu. Aby uzyskać więcej informacji na temat możliwych wartości dla właściwości umieszczania, zobacz [zachowanie położenia okna podręcznego](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).  
  
 ![Położenie ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
Położenia etykietki narzędzia, za pomocą właściwości umieszczania  
  
 ![Umieszczenie etykietka narzędzia, za pomocą prostokąta umieszczania](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
Położenia etykietki narzędzia, za pomocą właściwości umieszczania i PlacementRectangle  
  
 ![Diagram położenie ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
Położenie ToolTip przy użyciu właściwości Placement, PlacementRectangle i przesunięcia  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTip> właściwości, aby określić położenie tooltip, którego zawartość ma <xref:System.Windows.Controls.ToolTip> obiektu.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTipService> właściwości, aby określić położenie tooltip, którego zawartość nie jest <xref:System.Windows.Controls.ToolTip> obiektu.  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
- [ToolTip — omówienie](../../../../docs/framework/wpf/controls/tooltip-overview.md)
- [Użyj ContextMenuService i ToolTipService](https://msdn.microsoft.com/library/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
