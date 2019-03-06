---
title: 'Instrukcje: Wykryć kiedy wciśnięto klawisz Enter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: 1796127d33087a3fd4504d03f175f8afe5323630
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351869"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Instrukcje: Wykryć kiedy wciśnięto klawisz Enter
W tym przykładzie pokazano, jak wykryć kiedy <xref:System.Windows.Input.Key.Enter> zostanie naciśnięty klawisz na klawiaturze.  
  
 W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.  
  
## <a name="example"></a>Przykład  
 Gdy użytkownik naciśnie <xref:System.Windows.Input.Key.Enter> w <xref:System.Windows.Controls.TextBox>, danych wejściowych w polu tekstowym zostanie wyświetlony w innym obszarze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Poniższy kod tworzy <xref:System.Windows.UIElement.KeyDown> programu obsługi zdarzeń.  W przypadku naciśnięcia klawisza <xref:System.Windows.Input.Key.Enter> klucza, zostanie wyświetlony komunikat w <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd danych wejściowych](input-overview.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
