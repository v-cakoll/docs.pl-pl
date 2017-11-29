---
title: "Jak utworzyć formant TextBox tylko do odczytu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36116346b389dac7e9783e69d9bcd79573b4bf75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Jak utworzyć formant TextBox tylko do odczytu
W tym przykładzie przedstawiono sposób konfigurowania <xref:System.Windows.Controls.TextBox> formantu nie zezwalać na dane wejściowe użytkownika lub modyfikacji.  
  
## <a name="example"></a>Przykład  
 Aby zapobiec modyfikowaniu zawartości <xref:System.Windows.Controls.TextBox> kontrolować, ustaw <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atrybutu **true**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atrybutu dotyczy tylko danych wejściowych użytkownika; nie ma wpływu na tekst w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] opis <xref:System.Windows.Controls.TextBox> formant lub programistycznie za pomocą tekstem <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.  
  
 Wartość domyślna <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> jest **false**.  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
