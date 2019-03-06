---
title: 'Instrukcje: Utwórz wieloliniowy formant TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 75bbee806b2b7039656d6c8e7c9a64359e77d16f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352350"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="b2da3-102">Instrukcje: Utwórz wieloliniowy formant TextBox</span><span class="sxs-lookup"><span data-stu-id="b2da3-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="b2da3-103">W tym przykładzie pokazano, jak używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie rozszerzy do uwzględnienia wiele wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="b2da3-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2da3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2da3-104">Example</span></span>  
 <span data-ttu-id="b2da3-105">Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **opakować** spowoduje, że wprowadzony tekst do opakowania do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> sterowania zostanie osiągnięty, automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> kontrolki ma być uwzględniane miejsce na znak nowego wiersza, jeśli wymagane.</span><span class="sxs-lookup"><span data-stu-id="b2da3-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="b2da3-106">Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu **true** powoduje, że nowy wiersz do wstawienia po naciśnięciu klawisza RETURN, ponownie automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> obejmujący miejsca na znak nowego wiersza, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="b2da3-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="b2da3-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybut dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane za pośrednictwem if <xref:System.Windows.Controls.TextBox> rozwija rozmiar ramki lub okna, która ją obejmuje.</span><span class="sxs-lookup"><span data-stu-id="b2da3-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="b2da3-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2da3-108">See also</span></span>
- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="b2da3-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="b2da3-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="b2da3-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="b2da3-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
