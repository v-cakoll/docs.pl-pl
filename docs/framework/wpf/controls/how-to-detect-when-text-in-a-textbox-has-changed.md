---
title: Jak wykryć kiedy tekst w TextBox uległ zmianie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552955"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Jak wykryć kiedy tekst w TextBox uległ zmianie
W tym przykładzie pokazano sposób użycia <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia w celu wykonania metody zawsze, gdy tekst w <xref:System.Windows.Controls.TextBox> kontrolki została zmieniona.  
  
 W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmian, Wstaw metodę do wywołania po każdej zmianie <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.  Ta metoda musi mieć podpisie, który odpowiada, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegowanie.  
  
 Program obsługi zdarzeń jest wywoływana przy każdym zawartość <xref:System.Windows.Controls.TextBox> formantu są zmieniane przez użytkownika lub programowo.  
  
 **Uwaga:** to zdarzenie uruchamiane w przypadku <xref:System.Windows.Controls.TextBox> formantu zostanie utworzona i wstępnie wypełniane przy użyciu tekstu.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definiuje Twojej <xref:System.Windows.Controls.TextBox> kontrolować, określ <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atrybut o wartości, która jest zgodna z nazwą metody obsługi zdarzeń.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Przykład  
 W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmian, Wstaw metodę do wywołania po każdej zmianie <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.  Ta metoda musi mieć podpisie, który odpowiada, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegowanie.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Program obsługi zdarzeń jest wywoływana przy każdym zawartość <xref:System.Windows.Controls.TextBox> formantu są zmieniane przez użytkownika lub programowo.  
  
 **Uwaga:** to zdarzenie uruchamiane w przypadku <xref:System.Windows.Controls.TextBox> formantu zostanie utworzona i wstępnie wypełniane przy użyciu tekstu.  
  
 Komentarze  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
