---
title: "Jak zmienić typografię tekstu"
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
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ab2f0b8f167e042243e8859187674d079cd8c2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-alter-the-typography-of-text"></a>Jak zmienić typografię tekstu
Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Documents.TextElement.Typography%2A> atrybutu przy użyciu <xref:System.Windows.Documents.Paragraph> jako element przykład.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: Tekst z zmieniony typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Z kolei na poniższej ilustracji przedstawiono, jak renderuje podobny przykład związane z typografią właściwości domyślnej.  
  
 ![Zrzut ekranu: Tekst z zmieniony typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Controls.TextBox.Typography%2A> właściwości programowo.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd dokumentu przepływu](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
