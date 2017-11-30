---
title: "Jak pobrać kolekcję linii z TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb771cdb4d12ebaa5160ec16ca57ba6acf011222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Jak pobrać kolekcję linii z TextBox
W tym przykładzie pokazano, jak uzyskać kolekcji wierszy tekstu z <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono prostą metodę, która przyjmuje <xref:System.Windows.Controls.TextBox> jako argument i zwraca <xref:System.Collections.Specialized.StringCollection> zawierających wiersze tekstu w **pole tekstowe**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Właściwość jest używana w celu ustalenia liczby wierszy są obecnie w **pole tekstowe**i <xref:System.Windows.Controls.TextBox.GetLineText%2A> metody jest następnie używany do wyodrębniania każdego wiersza i dodać go do kolekcji wierszy.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
