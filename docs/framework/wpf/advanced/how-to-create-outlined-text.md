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
ms.openlocfilehash: c79f5c1c6812b1175119133664e39995af29bd4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544968"
---
# <a name="how-to-create-outlined-text"></a>Jak utworzyć schemat tekstu
W większości przypadków, gdy dodajesz ornamentacji do ciągów tekstowych w Twojej [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, w przypadku używania tekstu pod względem zbiór znaków discrete lub symboli. Na przykład można utworzyć pędzla gradientu liniowego i zastosować je do <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.TextBox> obiektu. Podczas wyświetlania lub edytowania pola tekstowego, pędzla gradientu liniowego jest automatycznie stosowana w bieżącym zestawie znaków w ciągu tekstowym.  
  
 ![Tekst wyświetlany przy użyciu pędzla gradientu liniowego](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
Przykład pędzla gradientu liniowego stosowane do pola tekstowego  
  
 Jednak możesz również przeprowadzić konwersję tekstu do <xref:System.Windows.Media.Geometry> obiektów, pozwala na tworzenie innych typów wizualnie RTF. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konturu ciąg tekstowy.  
  
 ![Używanie pędzla gradientu liniowego konspektu tekstu](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Przykład pędzla gradientu liniowego stosowane do geometrii konspektu tekstu  
  
 Jeśli tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiektu, nie jest już zbiór znaków — nie można zmodyfikować znaków w ciągu tekstowym. Jednak może wpływać na wygląd tekst skonwertowany zmieniając jej obrysu i wypełnienie właściwości. Obrysu odwołuje się do konturu tekst skonwertowany; Wypełnienie odnosi się do obszaru w konturze tekst skonwertowany.  
  
 Poniższe przykłady przedstawiają kilka sposobów tworzenia efekty wizualne, modyfikując obrysu i wypełnienia przekonwertowanego tekstu.  
  
 ![Tekst z różnymi kolorami wypełnienia i pociągnięcia](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Przykładowa konfiguracja obrysu i wypełnienia do różnych kolorów  
  
 ![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Przykład pędzel obrazu na obrysu  
  
 Istnieje również możliwość modyfikowania obwiedni prostokąta pola lub wyróżnianie tekst skonwertowany. Poniższy przykład przedstawia sposób tworzenia efekty wizualne, modyfikując obrysu i wyróżnianie tekstu przekonwertowany.  
  
 ![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Przykład pędzel obrazu na obrysu i wyróżnienia  
  
## <a name="example"></a>Przykład  
 Klucz do konwersji tekstu do <xref:System.Windows.Media.Geometry> obiektu jest użycie <xref:System.Windows.Media.FormattedText> obiektu. Po utworzeniu tego obiektu można używać <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> i <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metod można przekonwertować na tekst, który <xref:System.Windows.Media.Geometry> obiektów. Pierwsza metoda zwraca geometrii tekst sformatowany; Druga metoda zwraca obwiedni geometrii tekst sformatowany. W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu i pobrać mają geometrię tekst sformatowany i jego pola ograniczającego.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Aby wyświetlić pobranej <xref:System.Windows.Media.Geometry> obiekty, musisz mieć dostęp <xref:System.Windows.Media.DrawingContext> obiektu, w którym jest wyświetlany tekst skonwertowany. W tym przykładzie kodu polega to na tworzenie obiektu kontrolki niestandardowej pochodzącej z klasy, która obsługuje renderowanie zdefiniowane przez użytkownika.  
  
 Aby wyświetlić <xref:System.Windows.Media.Geometry> obiektów w kontrolki niestandardowej, podaj zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody. Należy używać przesłoniętą metodę <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metodę, by narysować <xref:System.Windows.Media.Geometry> obiektów.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rysowanie formatowanego tekstu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
