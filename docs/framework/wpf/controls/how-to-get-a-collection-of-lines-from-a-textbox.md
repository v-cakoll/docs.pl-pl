---
title: 'Instrukcje: Pobierz kolekcję linii z TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: a63470c6f0db72340f482bf638910685aa3f461f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561767"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="84a49-102">Instrukcje: Pobierz kolekcję linii z TextBox</span><span class="sxs-lookup"><span data-stu-id="84a49-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="84a49-103">W tym przykładzie pokazano, jak pobrać kolekcję linii tekstu z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="84a49-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a49-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="84a49-104">Example</span></span>  
 <span data-ttu-id="84a49-105">W poniższym przykładzie przedstawiono proste metody, która przyjmuje <xref:System.Windows.Controls.TextBox> jako argument i zwraca <xref:System.Collections.Specialized.StringCollection> zawierające wiersze tekstu **TextBox**.</span><span class="sxs-lookup"><span data-stu-id="84a49-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="84a49-106"><xref:System.Windows.Controls.TextBox.LineCount%2A> Właściwość jest używana do określenia, ile wierszy jest obecnie oferowana **TextBox**i <xref:System.Windows.Controls.TextBox.GetLineText%2A> metody jest następnie używany do wyodrębniania w każdym wierszu i dodaj go do kolekcji wierszy.</span><span class="sxs-lookup"><span data-stu-id="84a49-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="84a49-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84a49-107">See also</span></span>
- [<span data-ttu-id="84a49-108">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="84a49-108">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="84a49-109">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="84a49-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
