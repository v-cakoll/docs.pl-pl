---
title: Użycie obiektów DrawingVisual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148325"
---
# <a name="using-drawingvisual-objects"></a>Użycie obiektów DrawingVisual
W tym temacie przedstawiono <xref:System.Windows.Media.DrawingVisual> omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sposobu używania obiektów w warstwie wizualnej.  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a>DrawingObiekt wizualny  
 Jest <xref:System.Windows.Media.DrawingVisual> to lekka klasa rysunku używana do renderowania kształtów, obrazów lub tekstu. Ta klasa jest uważana za lekką, ponieważ nie zapewnia obsługi układu lub zdarzeń, co zwiększa jej wydajność. Z tego powodu rysunki są idealne dla tła i obiektów clipart.  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a>Kontener hosta drawingvisual  
 Aby użyć <xref:System.Windows.Media.DrawingVisual> obiektów, należy utworzyć kontener hosta dla obiektów. Obiekt kontenera hosta musi <xref:System.Windows.FrameworkElement> pochodzić z klasy, która zapewnia <xref:System.Windows.Media.DrawingVisual> obsługę układu i obsługi zdarzeń, której brakuje klasy. Obiekt kontenera hosta nie wyświetla żadnych widocznych właściwości, ponieważ jego głównym celem jest zawieranie obiektów podrzędnych. Jednak <xref:System.Windows.UIElement.Visibility%2A> właściwość kontenera hosta musi <xref:System.Windows.Visibility.Visible>być ustawiona na ; w przeciwnym razie żaden z jego elementów podrzędnych nie będzie widoczny.  
  
 Podczas tworzenia obiektu kontenera hosta dla obiektów wizualnych należy przechowywać odniesienia do obiektów wizualnych w pliku <xref:System.Windows.Media.VisualCollection>. Użyj <xref:System.Windows.Media.VisualCollection.Add%2A> metody, aby dodać obiekt wizualny do kontenera hosta. W poniższym przykładzie tworzony jest obiekt kontenera hosta, <xref:System.Windows.Media.VisualCollection>a do jego programu są dodawane trzy obiekty wizualne.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Aby uzyskać pełny przykład kodu, z którego w poprzednim przykładzie kodu został wyodrębniony, zobacz [Hit Test using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a>Tworzenie rysunku Obiekty wizualne  
 Podczas tworzenia <xref:System.Windows.Media.DrawingVisual> obiektu nie ma zawartości rysunku. Zawartość tekstu, grafiki lub obrazu można dodawać, <xref:System.Windows.Media.DrawingContext> pobierając obiekt i do niego rysując. A <xref:System.Windows.Media.DrawingContext> jest zwracany <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> przez <xref:System.Windows.Media.DrawingVisual> wywołanie metody obiektu.  
  
 Aby narysować prostokąt do <xref:System.Windows.Media.DrawingContext>, <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> użyj metody <xref:System.Windows.Media.DrawingContext> obiektu. Podobne metody istnieją do rysowania innych typów zawartości. Po zakończeniu rysowania zawartości <xref:System.Windows.Media.DrawingContext>do <xref:System.Windows.Media.DrawingContext.Close%2A> , wywołać <xref:System.Windows.Media.DrawingContext> metodę, aby zamknąć i utrwalić zawartość.  
  
 W poniższym przykładzie <xref:System.Windows.Media.DrawingVisual> tworzony jest obiekt, a prostokąt <xref:System.Windows.Media.DrawingContext>jest wciągany do jego .  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a>Tworzenie zastępowania dla elementów członkowskich FrameworkElement  
 Obiekt kontenera hosta jest odpowiedzialny za zarządzanie jego kolekcji obiektów wizualnych. Wymaga to, że kontener hosta implementuje <xref:System.Windows.FrameworkElement> zastąpienia dla klasy pochodnej.  
  
 Na poniższej liście opisano dwa elementy członkowskie, które należy zastąpić:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Zwraca element podrzędny w określonym indeksie z kolekcji elementów podrzędnych.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Pobiera liczbę wizualnych elementów podrzędnych w tym elemencie.  
  
 W poniższym przykładzie są implementowane zastąpienia dla dwóch <xref:System.Windows.FrameworkElement> elementów członkowskich.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a>Zapewnienie pomocy w testowaniu trafień  
 Obiekt kontenera hosta może zapewnić obsługę zdarzeń, nawet jeśli nie <xref:System.Windows.UIElement.Visibility%2A> wyświetla żadnych widocznych właściwości — jednak jego właściwość musi być ustawiona na <xref:System.Windows.Visibility.Visible>. Dzięki temu można utworzyć procedurę obsługi zdarzeń dla kontenera hosta, który może zalewkować zdarzenia myszy, takie jak zwolnienie lewego przycisku myszy. Procedura obsługi zdarzeń można następnie zaimplementować testowanie trafień, wywołując <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę. <xref:System.Windows.Media.HitTestResultCallback> Parametr metody odnosi się do procedury zdefiniowanej przez użytkownika, której można użyć do określenia wynikowej akcji testu trafień.  
  
 W poniższym przykładzie obsługa testowania trafień jest implementowana dla obiektu kontenera hosta i jego elementów podrzędnych.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md)
- [Test trafienia w warstwie Visual](hit-testing-in-the-visual-layer.md)
