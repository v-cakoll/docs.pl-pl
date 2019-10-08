---
title: Jak wykryć kiedy wciśnięto klawisz Enter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004822"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Jak wykryć kiedy wciśnięto klawisz Enter
Ten przykład pokazuje, jak wykryć, kiedy naciśnięto klawisz <xref:System.Windows.Input.Key.Enter> na klawiaturze.  
  
 Ten przykład składa się z pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i pliku związanego z kodem.  
  
## <a name="example"></a>Przykład  
 Gdy użytkownik naciśnie klawisz <xref:System.Windows.Input.Key.Enter> w <xref:System.Windows.Controls.TextBox>, dane wejściowe w polu tekstowym pojawiają się w innym obszarze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Poniższy kod XAML tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Poniższy kod w tle tworzy procedurę obsługi zdarzeń <xref:System.Windows.UIElement.KeyDown>.  Jeśli klawisz, który jest wciśnięty, jest kluczem <xref:System.Windows.Input.Key.Enter>, zostanie wyświetlony komunikat w <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd danych wejściowych](input-overview.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
