---
title: "Zmień wybór RichTextBox za pomocą programowania"
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
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbfb61db786286209ed24e79026d4759a46c84d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a>Zmień wybór RichTextBox za pomocą programowania
W tym przykładzie pokazano, jak programowo zmienić bieżące zaznaczenie w <xref:System.Windows.Controls.RichTextBox>. To pole wyboru jest taki sam, jakby użytkownik wybrana zawartość za pomocą interfejsu użytkownika.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod opisuje nazwane <xref:System.Windows.Controls.RichTextBox> formantu o prostej zawartości.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Gdy użytkownik kliknie wewnątrz następujący kod programowo wybiera dowolny tekst <xref:System.Windows.Controls.RichTextBox>.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)
