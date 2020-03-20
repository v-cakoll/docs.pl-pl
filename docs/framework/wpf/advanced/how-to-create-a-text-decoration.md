---
title: Jak utworzyć dekorację tekstu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185920"
---
# <a name="how-to-create-a-text-decoration"></a>Jak utworzyć dekorację tekstu
Obiekt <xref:System.Windows.TextDecoration> jest ozdobą wizualną, którą można dodać do tekstu. Istnieją cztery typy dekoracji tekstu: podkreślenie, linia bazowa, przekreślenie i linia zbyta. W poniższym przykładzie przedstawiono lokalizacje dekoracji tekstu względem tekstu.  
  
 ![Diagram typów dekoracji tekstu](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 Aby dodać dekorację tekstu do <xref:System.Windows.TextDecoration> tekstu, utwórz obiekt i zmodyfikuj jego właściwości. Użyj <xref:System.Windows.TextDecoration.Location%2A> właściwości, aby określić, gdzie pojawia się dekoracja tekstu, takich jak podkreślenie. Użyj <xref:System.Windows.TextDecoration.Pen%2A> właściwości, aby określić wygląd dekoracji tekstu, na przykład pełny kolor wypełnienia lub gradientu. Jeśli nie określisz wartości <xref:System.Windows.TextDecoration.Pen%2A> właściwości, dekoracje domyślnie mają ten sam kolor co tekst. Po zdefiniowaniu <xref:System.Windows.TextDecoration> obiektu dodaj go <xref:System.Windows.TextDecorations> do kolekcji żądanego obiektu tekstowego.  
  
 W poniższym przykładzie przedstawiono dekorację tekstu stylizowaną za pomocą pędzla gradientu liniowego i pióra przerywanego.  
  
 ![Dekoracja tekstu z podkreśleniem gradientu liniowego](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 Obiekt <xref:System.Windows.Documents.Hyperlink> jest elementem zawartości przepływu na poziomie wbudowanym, który umożliwia hostować hiperłącza w zawartości przepływu. Domyślnie <xref:System.Windows.Documents.Hyperlink> obiekt jest <xref:System.Windows.TextDecoration> używany do wyświetlania podkreślenia. <xref:System.Windows.TextDecoration>obiekty mogą być intensywnie wydajne do wystąpienia, <xref:System.Windows.Documents.Hyperlink> szczególnie jeśli masz wiele obiektów. Jeśli szeroko korzystać <xref:System.Windows.Documents.Hyperlink> z elementów, można rozważyć pokazano podkreślenie tylko podczas <xref:System.Windows.ContentElement.MouseEnter> wyzwalania zdarzenia, takich jak zdarzenie.  
  
 W poniższym przykładzie podkreślenie łącza "Moje MSN" jest <xref:System.Windows.ContentElement.MouseEnter> dynamiczne — pojawia się tylko wtedy, gdy zdarzenie jest wyzwalane.  
  
 ![Hiperłącza wyświetlające dekoracje tekstowe](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 Aby uzyskać więcej informacji, zobacz [Określanie, czy hiperłącze jest podkreślone](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu dekoracja tekstu podkreślenia używa domyślnej wartości czcionki.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 W poniższym przykładzie kodu zostanie utworzona dekoracja tekstu podkreślenia za pomocą pędzla z jednolitym kolorem pióra.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 W poniższym przykładzie kodu zostanie utworzona dekoracja tekstu podkreślenia za pomocą pędzla gradientu liniowego dla pióra przerywanego.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Określanie, czy hiperlink jest podkreślony](how-to-specify-whether-a-hyperlink-is-underlined.md)
