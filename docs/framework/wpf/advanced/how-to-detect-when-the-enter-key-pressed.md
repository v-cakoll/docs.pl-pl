---
title: Jak wykryć kiedy wciśnięto klawisz Enter
description: Wykryj, kiedy wybrano klawisz Enter na klawiaturze w Windows Presentation Foundation. Ten przykład składa się z kodu XAML i pliku związanego z kodem.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163183"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Jak wykryć kiedy wciśnięto klawisz Enter
Ten przykład pokazuje, jak wykryć <xref:System.Windows.Input.Key.Enter> klawisz na klawiaturze.  
  
 Ten przykład zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik i plik związany z kodem.  
  
## <a name="example"></a>Przykład  
 Gdy użytkownik naciśnie klawisz <xref:System.Windows.Input.Key.Enter> w <xref:System.Windows.Controls.TextBox> , dane wejściowe w polu tekstowym pojawiają się w innym obszarze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .  
  
 Poniższy kod XAML tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.StackPanel> , a <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Poniższy kod w tle tworzy <xref:System.Windows.UIElement.KeyDown> procedurę obsługi zdarzeń.  Jeśli klawisz, który jest wciśnięty <xref:System.Windows.Input.Key.Enter> , jest wyświetlany w oknie <xref:System.Windows.Controls.TextBlock> .  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Dane wejściowe](input-overview.md)
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
