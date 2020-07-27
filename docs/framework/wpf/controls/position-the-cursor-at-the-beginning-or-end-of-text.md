---
title: Jak umieścić kursor na początku lub na końcu tekstu w formancie TextBox
description: Dowiedz się, jak umieścić kursor na początku lub na końcu zawartości tekstowej kontrolki TextBox Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167518"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="85c06-103">Jak umieścić kursor na początku lub na końcu tekstu w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="85c06-103">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="85c06-104">Ten przykład pokazuje, jak umieścić kursor na początku lub na końcu zawartości tekstowej <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="85c06-104">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85c06-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="85c06-105">Example</span></span>  
 <span data-ttu-id="85c06-106">Poniższy [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod opisuje <xref:System.Windows.Controls.TextBox> formant i przypisuje mu nazwę.</span><span class="sxs-lookup"><span data-stu-id="85c06-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="85c06-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="85c06-107">Example</span></span>  
 <span data-ttu-id="85c06-108">Aby ustawić położenie kursora na początku zawartości <xref:System.Windows.Controls.TextBox> kontrolki, wywołaj <xref:System.Windows.Controls.TextBox.Select%2A> metodę i określ pozycję początkową wyboru równą 0 i wybierz wartość 0.</span><span class="sxs-lookup"><span data-stu-id="85c06-108">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="85c06-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="85c06-109">Example</span></span>  
 <span data-ttu-id="85c06-110">Aby ustawić położenie kursora na końcu zawartości <xref:System.Windows.Controls.TextBox> kontrolki, należy wywołać <xref:System.Windows.Controls.TextBox.Select%2A> metodę i określić pozycję początkową wyboru równą długości zawartości tekstowej, a wybór wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="85c06-110">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="85c06-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85c06-111">See also</span></span>

- [<span data-ttu-id="85c06-112">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="85c06-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="85c06-113">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="85c06-113">RichTextBox Overview</span></span>](richtextbox-overview.md)
