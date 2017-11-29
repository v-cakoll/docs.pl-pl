---
title: "Jak utworzyć dekorację tekstu"
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9229ce86dbe640c4eb960c455dd049ff40b38d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-text-decoration"></a>Jak utworzyć dekorację tekstu
A <xref:System.Windows.TextDecoration> obiekt jest visual ornamentacji, można dodać do tekstu. Istnieją cztery typy dekoracji tekstu: podkreślenia, linii bazowej, przekreślenia i nadkreślenia. W poniższym przykładzie przedstawiono lokalizacje dekoracji tekstu względem tekstu.  
  
 ![Diagram lokalizacji dekoracji tekstu](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
Przykład typów dekoracji tekstu  
  
 Aby dodać dekoracji tekstu do tekstu, należy utworzyć <xref:System.Windows.TextDecoration> obiektów i zmodyfikować jego właściwości. Użyj <xref:System.Windows.TextDecoration.Location%2A> właściwości w celu określenia, gdzie dekoracji tekstu jest wyświetlana, takie jak podkreślenie. Użyj <xref:System.Windows.TextDecoration.Pen%2A> właściwość, aby określić wygląd dekoracji tekstu, takiego jak wypełnieniem lub kolor gradientu. Jeśli nie określisz wartości <xref:System.Windows.TextDecoration.Pen%2A> właściwości, wartość domyślna dekoracje to kolor tekstu. Po zdefiniowaniu <xref:System.Windows.TextDecoration> obiektów, dodaj go do <xref:System.Windows.TextDecorations> kolekcji obiektu odpowiedni tekst.  
  
 W poniższym przykładzie przedstawiono dekoracji tekstu, który został wstawiony z pędzla gradientu liniowego i kreskowane pióra.  
  
 ![Dekoracji tekstu linią gradientu liniowego](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Przykład podkreślenie styl gradientu liniowego pędzla i kreskowane pióra  
  
 <xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływu, który umożliwia hiperłącza hosta w zawartości przepływu. Domyślnie <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.TextDecoration> obiektu do wyświetlenia podkreślenie. <xref:System.Windows.TextDecoration>obiekty mogą być znacznym można utworzyć wystąpienia, wydajność, szczególnie w przypadku wielu <xref:System.Windows.Documents.Hyperlink> obiektów. Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, warto rozważyć przedstawiający podkreślenie tylko wtedy, gdy wyzwolenie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń.  
  
 W poniższym przykładzie jest dynamiczny podkreślenia łącza "Mój MSN" — tylko wygląda na to, kiedy <xref:System.Windows.ContentElement.MouseEnter> zdarzenie zostanie wyzwolone.  
  
 ![Wyświetlanie właściwości TextDecorations hiperłącza](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Zdefiniowane za pomocą właściwości TextDecorations hiperłącza  
  
 Aby uzyskać więcej informacji, zobacz [Określ, czy hiperłącze jest podkreślona](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu dekoracji tekstu podkreślenie używa domyślnej wartości czcionki.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 W poniższym przykładzie kodu podkreślenie Dekoracja tekstu jest tworzony przy użyciu pędzla pełnego koloru pióra.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 W poniższym przykładzie kodu podkreślenie Dekoracja tekstu jest tworzony z liniowego pędzla gradientu kreskowane pióra.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [Określ, czy hiperłącze jest podkreślony.](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
