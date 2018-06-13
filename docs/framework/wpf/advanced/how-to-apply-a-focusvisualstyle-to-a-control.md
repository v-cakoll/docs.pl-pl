---
title: Jak zastosować FocusVisualStyle do formantu
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 34af5ca6f5ce6b3714d7d7e0d707841cdfc61349
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543735"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Jak zastosować FocusVisualStyle do formantu
W tym przykładzie przedstawiono sposób tworzenia stylu wizualnego fokusu w zasobach i zastosować go do formantu, za pomocą <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano styl, który tworzy dodatkową kontrolę składania, które tylko wtedy, gdy formant jest klawiatury w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Jest to osiągane przez definiowanie styl o <xref:System.Windows.Controls.ControlTemplate>, a następnie odwołuje się do tego stylu jako zasób podczas ustawiania <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.  
  
 Prostokąt zewnętrznych przypominającą obramowanie znajduje się poza prostokątnym obszarem. Chyba, że zmodyfikowany, rozmiar styl używa <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A> prostokątny formantu, których stosowane jest stylu wizualnego fokus. W tym przykładzie wartości ujemnych dla <xref:System.Windows.FrameworkElement.Margin%2A> aby pojawiają się nieco poza kontrolą ukierunkowanych obramowanie.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> jest dodatek do stylu szablonu żadnych kontroli, wchodzącej z jawnym styl lub style kompozycji; podstawowy styl formantu nadal można utworzyć przy użyciu <xref:System.Windows.Controls.ControlTemplate> i ustawienie stylu <xref:System.Windows.FrameworkElement.Style%2A> właściwości.  
  
 Fokus style wizualne powinien być używany spójnie motyw lub interfejsu użytkownika, zamiast użyć innego dla każdego elementu focusable. Aby uzyskać więcej informacji, zobacz [style dla zespołu w formantach i FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Style dla fokusu w kontrolkach i styl FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
