---
title: Jak odzyskać wybór tekstu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: 6b25c555d5e6cac93b2e1518b25e7880ab77c866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552015"
---
# <a name="how-to-retrieve-a-text-selection"></a>Jak odzyskać wybór tekstu
W tym przykładzie pokazano sposób użycia <xref:System.Windows.Controls.TextBox.SelectedText%2A> właściwości do pobierania tekstu zaznaczonego w <xref:System.Windows.Controls.TextBox> formantu.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie pokazano definicję <xref:System.Windows.Controls.TextBox> kontrolki zawierającej tekst, który zostanie wybrana, a <xref:System.Windows.Controls.Button> kontroli z określonym <xref:System.Windows.Controls.Button.OnClick%2A> — metoda.  
  
 W tym przykładzie przycisk skojarzony <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń służy do pobierania zaznaczonego tekstu. Gdy użytkownik kliknie przycisk <xref:System.Windows.Controls.Button.OnClick%2A> metoda Kopiuje zaznaczony tekst w polu tekstowym na ciąg. Okoliczności za pomocą których zaznaczenie tekstu jest pobierana (kliknięcie przycisku), jak i akcji wykonanych za pomocą tego zaznaczenia (kopiowanie zaznaczenia tekstu do ciągu), można łatwo zmodyfikowane w celu uwzględnienia wielu różnych scenariuszach.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Przykład  
 C# ilustruje przykład <xref:System.Windows.Controls.Button.OnClick%2A> programu obsługi zdarzeń dla przycisku zdefiniowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tym przykładzie.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
