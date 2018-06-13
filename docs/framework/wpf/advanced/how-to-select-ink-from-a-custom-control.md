---
title: 'Porady: wybrać atrament w niestandardowej kontrolce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 6c85855cda4f74d557539ed7aea3f725550512e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548371"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>Porady: wybrać atrament w niestandardowej kontrolce
Dodając <xref:System.Windows.Ink.IncrementalLassoHitTester> do formantu niestandardowego można włączyć formantu, dzięki czemu użytkownik może wybrać odręczne za pomocą narzędzia lasso, podobnie jak <xref:System.Windows.Controls.InkCanvas> wybiera z pewnymi lasso.  
  
 W tym przykładzie przyjęto założenie, że znasz tworzenia włączone odręczne kontrolek niestandardowych.  Aby utworzyć niestandardowego formantu, który akceptuje odręczne, zobacz [tworzenia kontrolki wprowadzania odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
## <a name="example"></a>Przykład  
 Gdy użytkownik wprowadzi lasso <xref:System.Windows.Ink.IncrementalLassoHitTester> prognozuje linie, które będą w granicach ścieżki lasso po podaniu polu.  Kreślone okażą się w granicach ścieżki lasso można traktować jako zaznaczony.  Wybranych pociągnięć może również zostać usunięte.  Na przykład, jeśli użytkownik zmieni kierunek podczas rysowania lasso <xref:System.Windows.Ink.IncrementalLassoHitTester> może usunąć zaznaczenie niektórych pociągnięć.  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> Zgłasza <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzeń, dzięki czemu formantu niestandardowego podczas rysowania polu użytkownika.  Na przykład można zmienić wygląd pociągnięć, ponieważ użytkownik wybiera i usuwa je.  
  
## <a name="managing-the-ink-mode"></a>Zarządzanie trybie odręcznego  
 Jest przydatne do użytkownika, jeśli polu pojawia się inaczej niż pismo odręczne na formantu. W tym celu formantu niestandardowego należy zachować informacje o czy zapisywania lub wybranie odręczne użytkownika. W tym celu najłatwiej zadeklarować wyliczenie z dwóch wartości: jedna, aby wskazać zapisuje użytkownika i odręcznego jedna, aby wskazać, że użytkownik wybiera odręczne.  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Następnie dodaj dwie <xref:System.Windows.Ink.DrawingAttributes> do klasy: należy użyć, gdy użytkownik zapisuje odręczne, należy użyć, gdy użytkownik wybierze odręczne.  W Konstruktorze zainicjować <xref:System.Windows.Ink.DrawingAttributes> i Dołącz zarówno <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> zdarzenia do tej procedury obsługi zdarzeń. Następnie ustaw <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> właściwość <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do pisma odręcznego <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Dodaj właściwości, która udostępnia tryb zaznaczania. Gdy użytkownik zmieni tryb zaznaczania, ustaw <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> właściwość <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do odpowiedniego <xref:System.Windows.Ink.DrawingAttributes> obiekt, a następnie ponownie dołączyć <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> właściwości <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Udostępnianie <xref:System.Windows.Ink.DrawingAttributes> jako właściwości, dzięki czemu aplikacje można określić wygląd pociągnięć i wyboru pociągnięć.  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Gdy właściwość <xref:System.Windows.Ink.DrawingAttributes> obiekt zmian, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> musi zostać ponownie nałożona do <xref:System.Windows.Controls.InkPresenter>.  W obsłudze zdarzeń dla <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> zdarzeń, podłącz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> do <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>Przy użyciu IncrementalLassoHitTester  
 Utwórz i zainicjuj <xref:System.Windows.Ink.StrokeCollection> zawierający wybranych pociągnięć.  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Uruchomienia użytkownika do rysowania pociągnięcia odręczne lub lasso, usuń zaznaczenie żadnych wybranych pociągnięć. Następnie, jeśli użytkownik jest rysowania lasso, Utwórz <xref:System.Windows.Ink.IncrementalLassoHitTester> przez wywołanie metody <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subskrybować <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzeń i wywołania <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Ten kod może być metodą oddzielne i wywoływać z <xref:System.Windows.UIElement.OnStylusDown%2A> i <xref:System.Windows.UIElement.OnMouseDown%2A> metody.  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Dodawanie punktów Pióro do <xref:System.Windows.Ink.IncrementalLassoHitTester> podczas, gdy użytkownik wprowadzi polu.  Wywołanie następującej metody z <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, i <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Obsługa <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> zdarzeń odpowiadać, gdy użytkownik wybiera i usuwa pociągnięć.  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> Klasa ma <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> i <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> właściwości, które pobierają pociągnięć, które zostały zaznaczony i niezaznaczony, odpowiednio.  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Gdy użytkownik zakończy rysowania w polu, subskrypcję <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzeń i wywołania <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Wprowadzanie wszystkich ze sobą.  
 Poniższy przykład jest kontrolki niestandardowej, która umożliwia użytkownikowi wybranie z pewnymi lasso.  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [Tworzenie kontrolki danych wejściowych pisma odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
