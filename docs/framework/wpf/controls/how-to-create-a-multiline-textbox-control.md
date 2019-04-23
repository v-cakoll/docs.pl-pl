---
title: 'Instrukcje: Tworzenie wielowierszowej kontrolki TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 29fb4c9498fe163c36e71680242d3ef8cf98c089
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181171"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Instrukcje: Tworzenie wielowierszowej kontrolki TextBox
W tym przykładzie pokazano, jak używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie rozszerzy do uwzględnienia wiele wierszy tekstu.  
  
## <a name="example"></a>Przykład  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **opakować** spowoduje, że wprowadzony tekst do opakowania do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> sterowania zostanie osiągnięty, automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> kontrolki ma być uwzględniane miejsce na znak nowego wiersza, jeśli wymagane.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu **true** powoduje, że nowy wiersz do wstawienia po naciśnięciu klawisza RETURN, ponownie automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> obejmujący miejsca na znak nowego wiersza, jeśli to konieczne.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybut dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane za pośrednictwem if <xref:System.Windows.Controls.TextBox> rozwija rozmiar ramki lub okna, która ją obejmuje.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.TextWrapping>
- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
