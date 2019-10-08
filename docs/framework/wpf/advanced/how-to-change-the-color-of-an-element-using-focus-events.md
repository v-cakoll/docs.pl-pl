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
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004836"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Jak zmienić kolor elementu przy użyciu elementów Fokus
Ten przykład pokazuje, jak zmienić kolor elementu, gdy zyskuje i traci fokus przy użyciu zdarzeń <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus>.  
  
 Ten przykład składa się z pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i pliku związanego z kodem.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML tworzy interfejs użytkownika, który składa się z dwóch <xref:System.Windows.Controls.Button> obiektów i dołącza obsługę zdarzeń dla zdarzeń <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> do obiektów <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Poniższy kod w tle tworzy procedury obsługi zdarzeń <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus>.  Gdy <xref:System.Windows.Controls.Button> ma fokus klawiatury, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony na czerwony.  Gdy <xref:System.Windows.Controls.Button> utraci fokus klawiatury, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony z powrotem na biały.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd danych wejściowych](input-overview.md)
