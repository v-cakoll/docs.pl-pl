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
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="aa046-102">Instrukcje: Tworzenie wielowierszowej kontrolki TextBox</span><span class="sxs-lookup"><span data-stu-id="aa046-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="aa046-103">W tym przykładzie pokazano, jak używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie rozszerzy do uwzględnienia wiele wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="aa046-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa046-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa046-104">Example</span></span>  
 <span data-ttu-id="aa046-105">Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **opakować** spowoduje, że wprowadzony tekst do opakowania do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> sterowania zostanie osiągnięty, automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> kontrolki ma być uwzględniane miejsce na znak nowego wiersza, jeśli wymagane.</span><span class="sxs-lookup"><span data-stu-id="aa046-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="aa046-106">Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu **true** powoduje, że nowy wiersz do wstawienia po naciśnięciu klawisza RETURN, ponownie automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> obejmujący miejsca na znak nowego wiersza, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="aa046-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="aa046-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybut dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane za pośrednictwem if <xref:System.Windows.Controls.TextBox> rozwija rozmiar ramki lub okna, która ją obejmuje.</span><span class="sxs-lookup"><span data-stu-id="aa046-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="aa046-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa046-108">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="aa046-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="aa046-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="aa046-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="aa046-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
