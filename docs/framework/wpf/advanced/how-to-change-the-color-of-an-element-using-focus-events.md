---
title: Jak zmienić kolor elementu przy użyciu elementów Fokus
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: d8d8a3e8b24021cf8a5f916ce3f291a3b66d9411
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Jak zmienić kolor elementu przy użyciu elementów Fokus
W tym przykładzie pokazano, jak zmienić kolor elementu uzyska i traci fokus przy użyciu <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> zdarzenia.  
  
 W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z dwóch <xref:System.Windows.Controls.Button> obiekty i dołącza obsługi zdarzeń <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> zdarzenia <xref:System.Windows.Controls.Button> obiektów.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Poniższy kod za tworzy <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> procedury obsługi zdarzeń.  Gdy <xref:System.Windows.Controls.Button> zyski klawiatury fokus, <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> zostanie zmieniona na czerwony.  Gdy <xref:System.Windows.Controls.Button> utraci fokus klawiatury <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> zmieniony na biały.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)
