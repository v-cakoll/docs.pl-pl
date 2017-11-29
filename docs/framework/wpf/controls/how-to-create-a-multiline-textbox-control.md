---
title: "Jak utworzyć wieloliniowy formant TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 244eb38ea47bbd7376c2f8c6f5b2609fbd9c4330
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="08d4b-102">Jak utworzyć wieloliniowy formant TextBox</span><span class="sxs-lookup"><span data-stu-id="08d4b-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="08d4b-103">Ten przykład przedstawia sposób użycia [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie zostanie rozwinięty w celu uwzględnienia wiele wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="08d4b-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08d4b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="08d4b-104">Example</span></span>  
 <span data-ttu-id="08d4b-105">Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **zawijanie** spowoduje, że wprowadzony tekst, który ma być zawijany do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> osiągnięciu kontroli automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> formantu, aby uwzględnić miejsce dla nowego wiersza, jeśli niezbędne.</span><span class="sxs-lookup"><span data-stu-id="08d4b-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="08d4b-106">Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu **true** powoduje, że nowy wiersz do wstawienia, gdy zostanie naciśnięty klawisz RETURN ponownie automatycznie rozszerzanie <xref:System.Windows.Controls.TextBox> uwzględnienie miejsce dla nowego wiersza, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="08d4b-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="08d4b-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybutu dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane Jeśli <xref:System.Windows.Controls.TextBox> rozszerza się poza rozmiaru ramki lub okna ograniczający go.</span><span class="sxs-lookup"><span data-stu-id="08d4b-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="08d4b-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08d4b-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="08d4b-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="08d4b-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="08d4b-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="08d4b-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
