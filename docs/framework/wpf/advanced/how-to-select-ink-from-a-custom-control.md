---
title: 'Instrukcje: Wybierz atrament w niestandardowej kontrolce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 02f02dfc3c4086d5b34711eed5eb98fb043ddee8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671840"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>Instrukcje: Wybierz atrament w niestandardowej kontrolce
Dodając <xref:System.Windows.Ink.IncrementalLassoHitTester> do formantu niestandardowego, można włączyć Twoją kontrolą, dzięki czemu użytkownik może wybrać atrament za pomocą narzędzia lasso, podobnie jak <xref:System.Windows.Controls.InkCanvas> wybiera atrament za pomocą lasso.  
  
 W tym przykładzie przyjęto założenie, że czytelnik zna utworzenie niestandardowej kontrolki z obsługą pisma odręcznego.  Aby utworzyć formant niestandardowy, który akceptuje dane wejściowe pisma odręcznego, zobacz [tworzenia sterowanie wejściem pisma odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
## <a name="example"></a>Przykład  
 Gdy użytkownik wprowadzi lasso <xref:System.Windows.Ink.IncrementalLassoHitTester> przewiduje linie, które będą w granicach ścieżki lasso po użytkownik kończy polu.  Pociągnięć, które są określone w granicach ścieżki lasso można traktować jako zaznaczony.  Wybranych pociągnięć może również stać się niezaznaczone.  Na przykład, jeśli użytkownik zmieni kierunek podczas rysowania lasso <xref:System.Windows.Ink.IncrementalLassoHitTester> może usunąć zaznaczenie niektórych pociągnięć.  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> Zgłasza <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzenie, które umożliwia niestandardową kontrolkę podczas rysowania polu użytkownika.  Na przykład można zmienić wygląd pociągnięć, kiedy użytkownik wybierze i usuwa je.  
  
## <a name="managing-the-ink-mode"></a>Zarządzanie tryb pisma odręcznego  
 Może to być pomocne dla użytkowników, w przypadku polu pojawia się inaczej niż pisma odręcznego na Twoją kontrolą. Aby to osiągnąć, niestandardową kontrolkę musi zachować informacje o czy użytkownik jest zapisu czy Wybieranie pisma odręcznego. W tym celu najłatwiej Aby zadeklarować wyliczenie z dwóch wartości: jeden do wskazania, że użytkownik zapisuje pisma odręcznego i jeden do wskazania, że użytkownik jest wybór pisma odręcznego.  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Następnie dodaj dwa <xref:System.Windows.Ink.DrawingAttributes> do klasy: należy użyć, gdy użytkownik zapisze pisma odręcznego, należy użyć, gdy użytkownik wybierze pisma odręcznego.  W konstruktorze, zainicjuj <xref:System.Windows.Ink.DrawingAttributes> i Dołącz oba <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> zdarzeń do tego samego programu obsługi zdarzeń. Następnie ustaw <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> właściwość <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do pisma odręcznego <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Dodaj właściwość, która udostępnia tryb wyboru. Gdy użytkownik zmieni trybu zaznaczania, ustaw <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> właściwość <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do odpowiedniego <xref:System.Windows.Ink.DrawingAttributes> obiektu, a następnie ponownie dołączyć <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> właściwość <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Udostępnianie <xref:System.Windows.Ink.DrawingAttributes> jako właściwości, dzięki czemu aplikacje można określić wygląd pociągnięć odręcznych i wyboru pociągnięć.  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Gdy właściwość <xref:System.Windows.Ink.DrawingAttributes> obiektu zmian <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> musi zostać ponownie dołączyć do <xref:System.Windows.Controls.InkPresenter>.  W procedurze obsługi zdarzeń dla <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> zdarzenia, ponownie Dołącz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> do <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>Za pomocą IncrementalLassoHitTester  
 Tworzenie i Inicjowanie <xref:System.Windows.Ink.StrokeCollection> zawierający wybranych pociągnięć.  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Uruchomienia użytkownika do rysowania pociągnięcia odręczne lub lasso, usuń zaznaczenie wszelkich wybranych pociągnięć. Następnie, jeśli użytkownik jest rysowanie lasso, Utwórz <xref:System.Windows.Ink.IncrementalLassoHitTester> przez wywołanie metody <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, Subskrybuj <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzenia i wywołania <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Ten kod może być oddzielnych metodach i wywoływane z <xref:System.Windows.UIElement.OnStylusDown%2A> i <xref:System.Windows.UIElement.OnMouseDown%2A> metody.  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Dodaj punkty Pióro do <xref:System.Windows.Ink.IncrementalLassoHitTester> podczas, gdy użytkownik wprowadzi w polu.  Wywołać następującą metodę z <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, i <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Obsługa <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> zdarzenie, aby odpowiadać, gdy użytkownik wybiera i usuwa pociągnięć.  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> Klasa ma <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> i <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> właściwości, które pobierają pociągnięć, które zostały zaznaczone i niezaznaczone, odpowiednio.  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Gdy użytkownik zakończy Rysowanie w polu, Anuluj subskrypcję <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzenia i wywołania <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Umieszczenie wszystkich ze sobą.  
 Poniższy przykład jest formant niestandardowy, który umożliwia użytkownikowi wybranie atrament za pomocą lasso.  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Ink.IncrementalLassoHitTester>
- <xref:System.Windows.Ink.StrokeCollection>
- <xref:System.Windows.Input.StylusPointCollection>
- [Tworzenie kontrolki danych wejściowych pisma odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
