---
title: 'Instrukcje: Zastosuj FocusVisualStyle do formantu'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: c4b379d3c57b6d0ae29952c23a35d7cc2cdf7f96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366603"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Instrukcje: Zastosuj FocusVisualStyle do formantu
W tym przykładzie pokazano, jak utworzyć styl wizualny fokusu w zasobach i zastosować styl do kontrolki, za pomocą <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano styl, który tworzy dodatkową kontrolę składania, które tylko wtedy, gdy kontrola jest klawiatury w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Jest to realizowane przez zdefiniowanie styl z <xref:System.Windows.Controls.ControlTemplate>, a następnie odwołuje się do tego stylu jako zasób podczas ustawiania <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.  
  
 Prostokąt zewnętrznych przypominającą obramowanie jest umieszczany poza prostokątny obszar. O ile nie zmodyfikowano inaczej, korzysta z rozmiaru stylu <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A> prostokątny kontrolki, w której stosowana jest styl wizualny fokusu. W tym przykładzie wartości ujemnych dla <xref:System.Windows.FrameworkElement.Margin%2A> Aby obramowanie pojawiają się nieco poza kontrolą wąsko zdefiniowany.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> jest dodatku na dowolny styl szablonu kontrolki, dostarczanego z style jawne lub style motyw; podstawowy styl kontrolki nadal można utworzyć za pomocą <xref:System.Windows.Controls.ControlTemplate> i ustawienie stylu <xref:System.Windows.FrameworkElement.Style%2A> właściwości.  
  
 Fokus stylów wizualnych powinien stosowane konsekwentnie w motywu lub interfejsu użytkownika, a nie przy użyciu innej dla każdego elementu focusable. Aby uzyskać więcej informacji, zobacz [style dla fokusu w formantach i FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Style dla fokusu w kontrolkach i styl FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
