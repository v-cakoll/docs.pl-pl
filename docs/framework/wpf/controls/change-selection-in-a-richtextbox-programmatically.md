---
title: Zmień wybór RichTextBox za pomocą programowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
ms.openlocfilehash: a85dc4baa8a59d25f577996c541a422bbe2af24e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367079"
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a><span data-ttu-id="4d1f3-102">Zmień wybór RichTextBox za pomocą programowania</span><span class="sxs-lookup"><span data-stu-id="4d1f3-102">Change Selection in a RichTextBox Programmatically</span></span>
<span data-ttu-id="4d1f3-103">W tym przykładzie przedstawiono sposób programowego modyfikowania bieżące zaznaczenie w <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="4d1f3-103">This example shows how to programmatically change the current selection in a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="4d1f3-104">Zaznacz to pole wyboru jest taki sam, jakby wybrany przez użytkownika ma zawartość za pomocą interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d1f3-104">This selection is the same as if the user had selected the content by using the user interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d1f3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d1f3-105">Example</span></span>  
 <span data-ttu-id="4d1f3-106">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu w tym artykule opisano nazwane <xref:System.Windows.Controls.RichTextBox> formantu o prostej zawartości.</span><span class="sxs-lookup"><span data-stu-id="4d1f3-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="4d1f3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d1f3-107">Example</span></span>  
 <span data-ttu-id="4d1f3-108">Poniższy kod wybiera programowo dowolny tekst po kliknięciu wewnątrz <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="4d1f3-108">The following code programmatically selects some arbitrary text when the user clicks inside the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4d1f3-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d1f3-109">See also</span></span>
- [<span data-ttu-id="4d1f3-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="4d1f3-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="4d1f3-111">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="4d1f3-111">TextBox Overview</span></span>](textbox-overview.md)
