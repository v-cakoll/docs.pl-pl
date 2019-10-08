---
title: Jak utworzyć efekt najazdu przy użyciu zdarzenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005182"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Jak utworzyć efekt najazdu przy użyciu zdarzenia
Ten przykład pokazuje, jak zmienić kolor elementu, gdy wskaźnik myszy zostanie wprowadzony i opuszcza obszar zajęty przez element.  
  
 Ten przykład składa się z pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i pliku związanego z kodem.  
  
> [!NOTE]
> W tym przykładzie pokazano, jak używać zdarzeń, ale zalecanym sposobem osiągnięcia tego samego efektu jest użycie <xref:System.Windows.Trigger> w stylu. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.Border> wokół <xref:System.Windows.Controls.TextBlock> i dołącza obsługę zdarzeń <xref:System.Windows.Input.Mouse.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> do <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Poniższy kod w tle tworzy procedury obsługi zdarzeń <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave>.  Gdy wskaźnik myszy zostanie przesunięty do <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zostanie zmienione na czerwony.  Gdy wskaźnik myszy opuszcza <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zostanie zmienione z powrotem na biały.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
