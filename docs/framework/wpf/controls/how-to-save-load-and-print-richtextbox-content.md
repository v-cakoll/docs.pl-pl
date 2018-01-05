---
title: "Jak zapisać, ładować i drukować zawartość RichTextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- saving RichTextBox controls [WPF]
- printing RichTextBox controls [WPF]
- loading RichTextBox controls [WPF]
- RichTextBox control [WPF], saving
- RichTextBox control [WPF], printing
- RichTextBox control [WPF], loading
ms.assetid: ffb113d3-c68a-47ca-8ac0-882283f38326
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45cd99332ca5ea87bf70c9b881da7daa3705ec25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-load-and-print-richtextbox-content"></a><span data-ttu-id="fd59d-102">Jak zapisać, ładować i drukować zawartość RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fd59d-102">How to: Save, Load, and Print RichTextBox Content</span></span>
<span data-ttu-id="fd59d-103">Poniższy przykład pokazuje, jak można zapisać zawartości <xref:System.Windows.Controls.RichTextBox> do pliku, załadować tego treść z powrotem do <xref:System.Windows.Controls.RichTextBox>i Drukuj zawartość.</span><span class="sxs-lookup"><span data-stu-id="fd59d-103">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd59d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd59d-104">Example</span></span>  
 <span data-ttu-id="fd59d-105">Poniżej znajduje się kod znaczników dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="fd59d-105">Below is the markup for the example.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="fd59d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd59d-106">Example</span></span>  
 <span data-ttu-id="fd59d-107">Poniżej znajduje się za przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="fd59d-107">Below is the code behind for the example.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fd59d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd59d-108">See Also</span></span>  
 [<span data-ttu-id="fd59d-109">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="fd59d-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="fd59d-110">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="fd59d-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
