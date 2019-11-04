---
title: Jak zastosować FocusVisualStyle do formantu
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459805"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Jak zastosować FocusVisualStyle do formantu
Ten przykład pokazuje, jak utworzyć styl wizualizacji fokusu w zasobach i zastosować styl do kontrolki przy użyciu właściwości <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano styl, który tworzy dodatkowe elementy sterujące, które mają zastosowanie tylko wtedy, gdy ta kontrolka jest ukierunkowana na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Jest to realizowane przez zdefiniowanie stylu z <xref:System.Windows.Controls.ControlTemplate>, a następnie odwołanie do tego stylu jako zasobu podczas ustawiania właściwości <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Zewnętrzny prostokąt przypominający obramowanie znajduje się poza prostokątnym obszarem. O ile nie zmodyfikowano inaczej, rozmiar stylu używa <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A> prostokątnego formantu, w którym jest stosowany styl wizualizacji fokusu. Ten przykład ustawia wartości ujemne dla <xref:System.Windows.FrameworkElement.Margin%2A>, aby obramowanie pojawiło się nieco poza kontrolką ukierunkowaną.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> jest dodatkiem do dowolnego stylu szablonu formantu, który pochodzi ze stylu jawnego lub stylu motywu; styl podstawowy formantu można nadal utworzyć przy użyciu <xref:System.Windows.Controls.ControlTemplate> i ustawić ten styl na Właściwość <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 Style wizualizacji fokusu powinny być stosowane spójnie między motywem lub interfejsem użytkownika, a nie przy użyciu różnych elementów dla każdego elementu możliwego do skoncentrowania. Aby uzyskać szczegółowe informacje, zobacz [Style do fokusu w kontrolkach i FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Style dla fokusu w kontrolkach i styl FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
