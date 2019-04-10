---
title: 'Instrukcje: Pobieranie kolekcji wierszy z kontrolki TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224640"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="f3e68-102">Instrukcje: Pobieranie kolekcji wierszy z kontrolki TextBox</span><span class="sxs-lookup"><span data-stu-id="f3e68-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="f3e68-103">W tym przykładzie pokazano, jak pobrać kolekcję linii tekstu z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f3e68-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e68-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3e68-104">Example</span></span>  
 <span data-ttu-id="f3e68-105">W poniższym przykładzie przedstawiono proste metody, która przyjmuje <xref:System.Windows.Controls.TextBox> jako argument i zwraca <xref:System.Collections.Specialized.StringCollection> zawierające wiersze tekstu **TextBox**.</span><span class="sxs-lookup"><span data-stu-id="f3e68-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="f3e68-106"><xref:System.Windows.Controls.TextBox.LineCount%2A> Właściwość jest używana do określenia, ile wierszy jest obecnie oferowana **TextBox**i <xref:System.Windows.Controls.TextBox.GetLineText%2A> metody jest następnie używany do wyodrębniania w każdym wierszu i dodaj go do kolekcji wierszy.</span><span class="sxs-lookup"><span data-stu-id="f3e68-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="f3e68-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3e68-107">See also</span></span>

- [<span data-ttu-id="f3e68-108">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="f3e68-108">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="f3e68-109">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="f3e68-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
