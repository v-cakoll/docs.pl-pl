---
title: 'Instrukcje: Utwórz wieloliniowy formant TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: ca1b499b2acdfd9fd2ff0f57f2b0c07d7da10789
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517828"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Instrukcje: Utwórz wieloliniowy formant TextBox
W tym przykładzie pokazano, jak używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie rozszerzy do uwzględnienia wiele wierszy tekstu.  
  
## <a name="example"></a>Przykład  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **opakować** spowoduje, że wprowadzony tekst do opakowania do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> sterowania zostanie osiągnięty, automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> kontrolki ma być uwzględniane miejsce na znak nowego wiersza, jeśli wymagane.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu **true** powoduje, że nowy wiersz do wstawienia po naciśnięciu klawisza RETURN, ponownie automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> obejmujący miejsca na znak nowego wiersza, jeśli to konieczne.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybut dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane za pośrednictwem if <xref:System.Windows.Controls.TextBox> rozwija rozmiar ramki lub okna, która ją obejmuje.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.TextWrapping>
- [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
