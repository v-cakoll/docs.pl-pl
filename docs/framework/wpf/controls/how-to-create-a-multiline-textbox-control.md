---
title: Jak utworzyć wieloliniowy formant TextBox
description: Dowiedz się, jak używać języka XAML do definiowania kontrolki TextBox, która rozwija się w celu uwzględnienia wielu wierszy tekstu w aplikacji Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166249"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="8fbc3-103">Jak utworzyć wieloliniowy formant TextBox</span><span class="sxs-lookup"><span data-stu-id="8fbc3-103">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="8fbc3-104">Ten przykład pokazuje, jak używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formantu, który zostanie automatycznie rozszerzony w celu uwzględnienia wielu wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="8fbc3-104">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fbc3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fbc3-105">Example</span></span>  
 <span data-ttu-id="8fbc3-106">Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu **zawijania** spowoduje, że wprowadzony tekst będzie zawijany do nowego wiersza po <xref:System.Windows.Controls.TextBox> osiągnięciu krawędzi kontrolki, automatycznie rozszerzając <xref:System.Windows.Controls.TextBox> formant, aby uwzględnić miejsce dla nowego wiersza, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="8fbc3-106">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="8fbc3-107">Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu na **wartość true** powoduje, że nowy wiersz zostanie wstawiony po naciśnięciu klawisza powrotu, po ponownym rozwinięciu automatycznie, <xref:System.Windows.Controls.TextBox> Aby uwzględnić miejsce w nowym wierszu, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="8fbc3-107">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="8fbc3-108">Ten <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atrybut dodaje pasek przewijania do <xref:System.Windows.Controls.TextBox> , tak aby zawartość <xref:System.Windows.Controls.TextBox> można przewijać w przypadku, gdy <xref:System.Windows.Controls.TextBox> rozszerza się poza rozmiar ramki lub okna.</span><span class="sxs-lookup"><span data-stu-id="8fbc3-108">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="8fbc3-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fbc3-109">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="8fbc3-110">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="8fbc3-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="8fbc3-111">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="8fbc3-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
