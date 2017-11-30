---
title: "Jak ustawić zawartość tekstu dla formantu TextBox"
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
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8da173fb91745f83aac2b4461a917c1fff6e9cb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Jak ustawić zawartość tekstu dla formantu TextBox
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.TextBox.Text%2A> właściwości można ustawić zawartość tekstową początkowej <xref:System.Windows.Controls.TextBox> formantu.  
  
 **Uwaga** chociaż [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wersja przykładu można użyć `<TextBox.Text>` tagi wokół tekstu każdego przycisku <xref:System.Windows.Controls.TextBox> zawartości, nie jest konieczne, ponieważ <xref:System.Windows.Controls.TextBox> stosuje <xref:System.Windows.Markup.ContentPropertyAttribute> atrybutu <xref:System.Windows.Controls.TextBox.Text%2A> właściwości. Aby uzyskać więcej informacji, zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
