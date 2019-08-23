---
title: 'Instrukcje: Tworzenie efektu najazdu przy użyciu zdarzeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960388"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Instrukcje: Tworzenie efektu najazdu przy użyciu zdarzeń
Ten przykład pokazuje, jak zmienić kolor elementu, gdy wskaźnik myszy zostanie wprowadzony i opuszcza obszar zajęty przez element.  
  
 Ten przykład zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik i plik związany z kodem.  
  
> [!NOTE]
> <xref:System.Windows.Trigger> W tym przykładzie pokazano, jak używać zdarzeń, ale zalecanym sposobem osiągnięcia tego samego efektu jest użycie w stylu. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Przykład  
 Poniżej [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] można utworzyć interfejs użytkownika, który składa się <xref:System.Windows.Controls.Border> z około <xref:System.Windows.Controls.TextBlock>a i dołącza <xref:System.Windows.Input.Mouse.MouseEnter> obsługę zdarzeń i <xref:System.Windows.UIElement.MouseLeave> do <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Poniższy kod w tle tworzy <xref:System.Windows.UIElement.MouseEnter> programy i <xref:System.Windows.UIElement.MouseLeave> obsługi zdarzeń.  Gdy wskaźnik myszy <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Border> zostanie wprowadzony, tło zostanie zmienione na czerwony.  Gdy wskaźnik myszy <xref:System.Windows.Controls.Border> zostanie pozostawiony <xref:System.Windows.Controls.Border>, tło zostanie zmienione z powrotem na biały.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
