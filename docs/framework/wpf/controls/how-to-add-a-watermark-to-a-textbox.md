---
title: "Jak dodać znak wodny do TextBox"
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
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92d619cb713e22d49e5c62bf7545d946b418dbda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Jak dodać znak wodny do TextBox
Poniższy przykład przedstawia sposób pomocy użyteczność <xref:System.Windows.Controls.TextBox> wyświetlając wyjaśniające obraz tła wewnątrz <xref:System.Windows.Controls.TextBox> dopóki tekst danych wejściowych użytkownika, w którym obraz jest usuwany. Ponadto obraz tła jest przywracany ponownie, jeśli użytkownik usunie swoje dane wejściowe. Zobacz na poniższej ilustracji.  
  
 ![Pole tekstowe z obrazem tła](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  Przyczyna obraz tła jest używany w tym przykładzie, a następnie po prostu manipulowanie <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox>, jest, że obraz tła nie zakłóca wiązania z danymi.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
