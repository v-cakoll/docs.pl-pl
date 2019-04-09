---
title: 'Instrukcje: Zmienianie typografii tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: 4c027424632f8671ba8d7cae1c899ef3a53edc26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078866"
---
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="c2592-102">Instrukcje: Zmienianie typografii tekstu</span><span class="sxs-lookup"><span data-stu-id="c2592-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="c2592-103">Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Documents.TextElement.Typography%2A> atrybutu, za pomocą <xref:System.Windows.Documents.Paragraph> jako element przykładu.</span><span class="sxs-lookup"><span data-stu-id="c2592-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2592-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2592-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="c2592-105">Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c2592-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="c2592-106">![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](./media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="c2592-106">![Screenshot: Text with altered typography](./media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="c2592-107">Z kolei na poniższej ilustracji pokazano, jak uzyskać podobny przykład przy użyciu domyślnych właściwości związane z typografią renderuje.</span><span class="sxs-lookup"><span data-stu-id="c2592-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="c2592-108">![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](./media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="c2592-108">![Screenshot: Text with altered typography](./media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2592-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2592-109">Example</span></span>  
 <span data-ttu-id="c2592-110">Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.TextBox.Typography%2A> właściwość programowo.</span><span class="sxs-lookup"><span data-stu-id="c2592-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="c2592-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2592-111">See also</span></span>

- [<span data-ttu-id="c2592-112">Przegląd Dokument przepływu</span><span class="sxs-lookup"><span data-stu-id="c2592-112">Flow Document Overview</span></span>](flow-document-overview.md)
