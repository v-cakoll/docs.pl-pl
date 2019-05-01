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
ms.openlocfilehash: 87740a215136863199d962a2704cf691f27fc3bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776652"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Instrukcje: Tworzenie efektu najazdu przy użyciu zdarzeń
Ten przykład przedstawia sposób zmienić kolor elementu, jak wskaźnik myszy wprowadza i pozostawia obszar zajmowany przez element.  
  
 W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.  
  
> [!NOTE]
>  W tym przykładzie pokazano, jak używać zdarzeń, ale zalecany sposób, aby osiągnąć ten sam efekt jest użycie <xref:System.Windows.Trigger> w stylu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.Border> wokół <xref:System.Windows.Controls.TextBlock>i dołącza <xref:System.Windows.Input.Mouse.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> programów obsługi zdarzeń do <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Poniższy kod tworzy <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> procedury obsługi zdarzeń.  Po umieszczeniu wskaźnika myszy <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> jest zmieniana na czerwono.  Po odsunięciu wskaźnika myszy <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zmieniony na biały.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
