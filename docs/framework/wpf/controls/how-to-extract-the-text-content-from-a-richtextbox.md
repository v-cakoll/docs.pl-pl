---
title: 'Instrukcje: Wyodrębnij zawartość tekstu z RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
ms.openlocfilehash: 8c7fd54931fad060a5d78e4c47c2cfce2767025a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355249"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="81620-102">Instrukcje: Wyodrębnij zawartość tekstu z RichTextBox</span><span class="sxs-lookup"><span data-stu-id="81620-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="81620-103">W tym przykładzie pokazano, jak wyodrębnić zawartość <xref:System.Windows.Controls.RichTextBox> jako zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="81620-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81620-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="81620-104">Example</span></span>  
 <span data-ttu-id="81620-105">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu w tym artykule opisano nazwane <xref:System.Windows.Controls.RichTextBox> formantu o prostej zawartości.</span><span class="sxs-lookup"><span data-stu-id="81620-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="81620-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="81620-106">Example</span></span>  
 <span data-ttu-id="81620-107">Poniższy kod implementuje metodę, która przyjmuje <xref:System.Windows.Controls.RichTextBox> jako argument i zwraca ciąg reprezentujący zawartość zwykły tekst <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="81620-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="81620-108">Metoda tworzy nowy <xref:System.Windows.Documents.TextRange> z zawartości <xref:System.Windows.Controls.RichTextBox>przy użyciu <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> i <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> do wskazania zakresu zawartości do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="81620-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="81620-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> i <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> właściwości każdego zwracają <xref:System.Windows.Documents.TextPointer>i są dostępne na FlowDocument podstawowego, który reprezentuje zawartość <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="81620-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="81620-110"><xref:System.Windows.Documents.TextRange> Udostępnia właściwości tekst zwykły tekst części zwraca <xref:System.Windows.Documents.TextRange> jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="81620-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="81620-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81620-111">See also</span></span>
- [<span data-ttu-id="81620-112">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="81620-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="81620-113">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="81620-113">TextBox Overview</span></span>](textbox-overview.md)
