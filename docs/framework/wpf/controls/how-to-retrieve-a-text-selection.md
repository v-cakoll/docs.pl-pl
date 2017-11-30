---
title: "Jak odzyskać wybór tekstu"
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
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d5e1c362c02d2d1d9e1840ea2a55df6875a80ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-a-text-selection"></a>Jak odzyskać wybór tekstu
W tym przykładzie pokazano sposób użycia <xref:System.Windows.Controls.TextBox.SelectedText%2A> właściwości do pobierania tekstu zaznaczonego w <xref:System.Windows.Controls.TextBox> formantu.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie pokazano definicję <xref:System.Windows.Controls.TextBox> kontrolki zawierającej tekst, który zostanie wybrana, a <xref:System.Windows.Controls.Button> kontroli z określonym <xref:System.Windows.Controls.Button.OnClick%2A> — metoda.  
  
 W tym przykładzie przycisk skojarzony <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń służy do pobierania zaznaczonego tekstu. Gdy użytkownik kliknie przycisk <xref:System.Windows.Controls.Button.OnClick%2A> metoda Kopiuje zaznaczony tekst w polu tekstowym na ciąg. Okoliczności za pomocą których zaznaczenie tekstu jest pobierana (kliknięcie przycisku), jak i akcji wykonanych za pomocą tego zaznaczenia (kopiowanie zaznaczenia tekstu do ciągu), można łatwo zmodyfikowane w celu uwzględnienia wielu różnych scenariuszach.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] przykładzie <xref:System.Windows.Controls.Button.OnClick%2A> programu obsługi zdarzeń dla przycisku zdefiniowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tym przykładzie.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
