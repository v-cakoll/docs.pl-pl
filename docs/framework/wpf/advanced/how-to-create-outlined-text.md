---
title: 'Instrukcje: Tworzenie tekstu z konturem'
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
ms.openlocfilehash: 237bdc097cd2a3fbfff6dd79bce401c2d091e211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776771"
---
# <a name="how-to-create-outlined-text"></a>Instrukcje: Tworzenie tekstu z konturem
W większości przypadków, gdy dodajesz ornamentacji do ciągów tekstowych w swojej [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, w przypadku używania tekstu pod kątem zbiór znaków discrete lub symbole. Na przykład można utworzyć pędzel gradientów liniowych i zastosować je do <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.TextBox> obiektu. Podczas wyświetlania lub edytowania pola tekstowego, Pędzel gradientów liniowych jest automatycznie stosowany do bieżącego zestawu znaków w ciągu tekstowym.  
  
 ![Tekst wyświetlany za pomocą pędzel gradientów liniowych](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 Jednakże można także przekonwertować tekst do <xref:System.Windows.Media.Geometry> obiektów, co pozwala na tworzenie innych rodzajów wizualnie RTF. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konspekt ciąg tekstowy.  
  
 ![Kontur tekstu przy użyciu pędzel gradientów liniowych](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Jeśli tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiektu nie jest już zbioru znaków — nie można zmodyfikować znaków w ciągu tekstowym. Jednak może wpłynąć na wygląd tekstu przekonwertowany, modyfikując jej obrysu i wypełnienie właściwości. Stroke odwołuje się do konturu tekst skonwertowany; Wypełnienie odnosi się do obszaru w konturze tekst skonwertowany.  
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia efektów wizualnych, modyfikując obrysu i wypełnienia tekst skonwertowany.  
  
 ![Tekst w różnych kolorach wypełnienia i pociągnięcia](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Tekst z ImageBrush dotyczą pociągnięcia](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Istnieje również możliwość modyfikowania otaczający prostokąta pola lub wyróżnienie przekonwertowanego tekstu. Poniższy przykład ilustruje sposób tworzenia efektów wizualnych, modyfikując obrysu i wyróżnienie tekst skonwertowany.  
  
 ![Tekst z ImageBrush stosowane do obrysu i wyróżnienia](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>Przykład  
 Kluczem do konwertowania tekstu do <xref:System.Windows.Media.Geometry> obiektu jest użycie <xref:System.Windows.Media.FormattedText> obiektu. Po utworzeniu tego obiektu można użyć <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> i <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metod do konwertowania tekstu na <xref:System.Windows.Media.Geometry> obiektów. Pierwsza metoda zwraca geometrii tekstu sformatowanego. Druga metoda zwraca obwiedni geometrii tekstu sformatowanego. Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu i pobrać geometrii tekstu sformatowanego i jego obwiedni.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Aby wyświetlić pobrany <xref:System.Windows.Media.Geometry> obiektów i potrzebny jest dostęp do <xref:System.Windows.Media.DrawingContext> obiektu, na którym jest wyświetlany tekst skonwertowany. W tych przykładach kodu odbywa się przez utworzenie obiektu kontrolki niestandardowej, która jest pochodną klasę, która obsługuje renderowanie zdefiniowanych przez użytkownika.  
  
 Aby wyświetlić <xref:System.Windows.Media.Geometry> obiekty w formancie niestandardowym dostarczają zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody. Metoda zgodnym z przesłoniętą należy używać <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metodę, aby narysować <xref:System.Windows.Media.Geometry> obiektów.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Dla źródła obiektu przykładowego użytkownika niestandardowego formantu, zobacz [OutlineTextControl.cs dla C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) i [OutlineTextControl.vb dla języka Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb). 
  
## <a name="see-also"></a>Zobacz także

- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
