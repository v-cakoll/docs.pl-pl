---
title: Jak utworzyć schemat tekstu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: d0ce46b9895589fd4635b567136204368a6431ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186856"
---
# <a name="how-to-create-outlined-text"></a>Jak utworzyć schemat tekstu
W większości przypadków podczas dodawania ornamentacji do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ciągów tekstowych w aplikacji, używasz tekstu pod względem kolekcji znaków dyskretnych lub glifów. Na przykład można utworzyć pędzel gradientu liniowego <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.TextBox> zastosować go do właściwości obiektu. Podczas wyświetlania lub edytowania pola tekstowego liniowy pędzel gradientowy jest automatycznie stosowany do bieżącego zestawu znaków w ciągu tekstowym.  
  
 ![Tekst wyświetlany za pomocą liniowego pędzla gradientowego](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 Można jednak również konwertować tekst na <xref:System.Windows.Media.Geometry> obiekty, co pozwala na tworzenie innych typów wizualnie tekstu sformatowany. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiekt na podstawie konturu ciągu tekstowego.  
  
 ![Kontur tekstu przy użyciu pędzla gradientu liniowego](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Gdy tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiekt, nie jest już kolekcją znaków — nie można modyfikować znaków w ciągu tekstowym. Można jednak wpłynąć na wygląd przekonwertowanego tekstu, modyfikując jego właściwości obrysu i wypełnienia. Obrys odnosi się do konturu przekonwertowanego tekstu; wypełnienie odnosi się do obszaru wewnątrz konturu przekonwertowanego tekstu.  
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia efektów wizualnych przez modyfikowanie obrysu i wypełnienia przekonwertowanego tekstu.  
  
 ![Tekst o różnych kolorach wypełnienia i obrysu](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Możliwe jest również zmodyfikowanie prostokąta obwiedni lub podświetlenia przekonwertowanego tekstu. Poniższy przykład ilustruje sposób tworzenia efektów wizualnych przez modyfikowanie obrysu i wyróżnienia przekonwertowanego tekstu.  
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu i podświetlenia](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>Przykład  
 Kluczem do konwersji <xref:System.Windows.Media.Geometry> tekstu do obiektu <xref:System.Windows.Media.FormattedText> jest użycie obiektu. Po utworzeniu tego obiektu można <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> użyć <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody i metody, aby przekonwertować tekst na <xref:System.Windows.Media.Geometry> obiekty. Pierwsza metoda zwraca geometrię sformatowanego tekstu; druga metoda zwraca geometrię obwiedni sformatowanego tekstu. Poniższy przykład kodu pokazuje, <xref:System.Windows.Media.FormattedText> jak utworzyć obiekt i pobrać geometrie sformatowanego tekstu i jego obwiedni.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Aby wyświetlić pobrane <xref:System.Windows.Media.Geometry> obiekty, należy uzyskać <xref:System.Windows.Media.DrawingContext> dostęp do obiektu, który wyświetla przekonwertowany tekst. W tych przykładach kodu odbywa się to przez utworzenie niestandardowego obiektu kontrolnego, który jest pochodną klasy, która obsługuje renderowanie zdefiniowane przez użytkownika.  
  
 Aby <xref:System.Windows.Media.Geometry> wyświetlić obiekty w formancie niestandardowym, podaj zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody. Nadpisana metoda powinna <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> używać metody <xref:System.Windows.Media.Geometry> do rysowania obiektów.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Źródło przykładowego obiektu sterującego użytkownika niestandardowego można znaleźć [w OutlineTextControl.cs dla języka C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) i [OutlineTextControl.vb dla języka Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).
  
## <a name="see-also"></a>Zobacz też

- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
