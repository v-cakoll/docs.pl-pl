---
title: Jak zmienić typografię tekstu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: fcc9c894970934bb5a69debef2f4e38297f82198
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
