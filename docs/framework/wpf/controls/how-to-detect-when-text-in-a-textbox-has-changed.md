---
title: 'Instrukcje: Wykrywanie momentu zmiany tekstu w kontrolce TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091151"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Instrukcje: Wykrywanie momentu zmiany tekstu w kontrolce TextBox
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia w celu wykonania metody zawsze wtedy, gdy tekst w <xref:System.Windows.Controls.TextBox> kontrolki została zmieniona.  
  
 W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmiany, Wstaw metodę do wywołania, gdy <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.  Ta metoda musi mieć podpisu, który jest zgodny, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegować.  
  
 Program obsługi zdarzeń jest wywoływana zawsze wtedy, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki są zmieniane przez użytkownika lub programowo.  
  
 **Uwaga:** To zdarzenie jest uruchamiany, gdy <xref:System.Windows.Controls.TextBox> formant zostanie utworzony i wstępnie wypełniane przy użyciu tekstu.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definiująca swoje <xref:System.Windows.Controls.TextBox> sterowania, określ <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atrybutu z wartością, która jest zgodna z nazwą metody obsługi zdarzeń.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Przykład  
 W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmiany, Wstaw metodę do wywołania, gdy <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.  Ta metoda musi mieć podpisu, który jest zgodny, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegować.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Program obsługi zdarzeń jest wywoływana zawsze wtedy, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki są zmieniane przez użytkownika lub programowo.  
  
 **Uwaga:** To zdarzenie jest uruchamiany, gdy <xref:System.Windows.Controls.TextBox> formant zostanie utworzony i wstępnie wypełniane przy użyciu tekstu.  
  
 Komentarze  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
