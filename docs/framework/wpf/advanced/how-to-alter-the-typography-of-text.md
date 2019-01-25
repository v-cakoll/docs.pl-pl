---
title: 'Instrukcje: Zmień typografię tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: f04c873e542ad02c1d2a20b770ded4464af7a6d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645408"
---
# <a name="how-to-alter-the-typography-of-text"></a>Instrukcje: Zmień typografię tekstu
Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Documents.TextElement.Typography%2A> atrybutu, za pomocą <xref:System.Windows.Documents.Paragraph> jako element przykładu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Z kolei na poniższej ilustracji pokazano, jak uzyskać podobny przykład przy użyciu domyślnych właściwości związane z typografią renderuje.  
  
 ![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.TextBox.Typography%2A> właściwość programowo.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd dokumentu przepływu](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
