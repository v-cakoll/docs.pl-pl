---
title: 'Instrukcje: Umieść kursor na początku lub na końcu tekstu w formancie TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: e4058518e4eb56e1cd9d5fdafd792d8f8d3b77ab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367846"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="0c9a6-102">Instrukcje: Umieść kursor na początku lub na końcu tekstu w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="0c9a6-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="0c9a6-103">W tym przykładzie pokazano, jak umieścić kursor na początku lub końcu zawartość tekstową <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0c9a6-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c9a6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c9a6-104">Example</span></span>  
 <span data-ttu-id="0c9a6-105">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod opisuje <xref:System.Windows.Controls.TextBox> kontroli i przypisuje mu nazwę.</span><span class="sxs-lookup"><span data-stu-id="0c9a6-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="0c9a6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c9a6-106">Example</span></span>  
 <span data-ttu-id="0c9a6-107">Aby umieść kursor na początku zawartość <xref:System.Windows.Controls.TextBox> sterowania, wywołaj <xref:System.Windows.Controls.TextBox.Select%2A> metody i określ wybór start pozycji 0, a wybór długość 0.</span><span class="sxs-lookup"><span data-stu-id="0c9a6-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="0c9a6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c9a6-108">Example</span></span>  
 <span data-ttu-id="0c9a6-109">Aby umieść kursor na końcu zawartości <xref:System.Windows.Controls.TextBox> sterowania, wywołaj <xref:System.Windows.Controls.TextBox.Select%2A> metodę i określić pozycja początkowa wybranego równa długości tekstu, zawartości i wyboru długość 0.</span><span class="sxs-lookup"><span data-stu-id="0c9a6-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="0c9a6-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c9a6-110">See also</span></span>
- [<span data-ttu-id="0c9a6-111">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="0c9a6-111">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="0c9a6-112">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="0c9a6-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
