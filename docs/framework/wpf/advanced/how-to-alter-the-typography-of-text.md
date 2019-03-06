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
ms.openlocfilehash: eeed93f62802a942915511db060c0e6c029579e0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365788"
---
# <a name="how-to-alter-the-typography-of-text"></a>Instrukcje: Zmień typografię tekstu
Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Documents.TextElement.Typography%2A> atrybutu, za pomocą <xref:System.Windows.Documents.Paragraph> jako element przykładu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](./media/textelement-typog.png "TextElement_Typog")  
  
 Z kolei na poniższej ilustracji pokazano, jak uzyskać podobny przykład przy użyciu domyślnych właściwości związane z typografią renderuje.  
  
 ![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](./media/textelement-typog-default.png "TextElement_Typog_Default")  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.TextBox.Typography%2A> właściwość programowo.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd dokumentu przepływu](flow-document-overview.md)
