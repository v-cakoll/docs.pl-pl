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
ms.openlocfilehash: 01e10a4b0f0bf4959850caf3951ad4ea915edb4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762114"
---
# <a name="using-drawingvisual-objects"></a>Użycie obiektów DrawingVisual
Ten temat zawiera omówienie sposobu użycia <xref:System.Windows.Media.DrawingVisual> obiekty w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] warstwy visual.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Obiektów DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> To lekkie rysowania klasę, która jest używany do renderowania kształty, obrazy i tekst. Ta klasa jest uważany za uproszczone, ponieważ nie dostarcza obsługi układu lub zdarzeń, która zwiększa ich wydajność. Z tego powodu rysunki są doskonałe do tła i obiekty clipart.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual hosta kontenera  
 Aby można było używać <xref:System.Windows.Media.DrawingVisual> obiektów, należy utworzyć kontener hosta dla obiektów. Obiekt kontenera hosta musi pochodzić od klasy <xref:System.Windows.FrameworkElement> klasy, która dostarcza układ i obsługi zdarzeń pomocy technicznej, który <xref:System.Windows.Media.DrawingVisual> klasy nie ma. Obiekt kontenera hosta nie wyświetla żadnych widocznych właściwości, ponieważ ich głównym celem jest zawierają obiekty podrzędnych. Jednak <xref:System.Windows.UIElement.Visibility%2A> właściwości kontenera hosta musi być równa <xref:System.Windows.Visibility.Visible>; w przeciwnym razie będą widoczne żadne z jego elementów podrzędnych.  
  
 Podczas tworzenia obiektu kontenera hosta dla obiektów wizualnych chcesz przechować odwołania do obiektów visual w <xref:System.Windows.Media.VisualCollection>. Użyj <xref:System.Windows.Media.VisualCollection.Add%2A> metodę, aby dodać obiekt wizualny do kontenera hosta. W poniższym przykładzie tworzony jest obiekt kontenera hosta, a trzy obiekty wizualne są dodawane do jej <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Cały przykładowy kod z którego został wyodrębniony w poprzednim przykładzie kodu, można zobaczyć [trafień za pomocą DrawingVisuals próbkę](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Tworzenie obiektów DrawingVisual  
 Po utworzeniu <xref:System.Windows.Media.DrawingVisual> obiektu, nie ma jej rysowania zawartości. Można dodać tekst, grafikę lub zawartości obrazu, pobierając obiekt <xref:System.Windows.Media.DrawingContext> i rysowanie w nim. A <xref:System.Windows.Media.DrawingContext> jest zwracany przez wywołanie metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> obiektu.  
  
 Aby narysować prostokąt na <xref:System.Windows.Media.DrawingContext>, użyj <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu. Istnieją podobne metody rysowania innych typów zawartości. Gdy skończysz rysowania zawartości <xref:System.Windows.Media.DrawingContext>, wywołaj <xref:System.Windows.Media.DrawingContext.Close%2A> metodę, aby zamknąć <xref:System.Windows.Media.DrawingContext> i zachować zawartość.  
  
 W poniższym przykładzie <xref:System.Windows.Media.DrawingVisual> obiekt zostanie utworzony i prostokąt jest wstawiany do jego <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Tworzenie zastąpienia dla członków FrameworkElement  
 Obiekt kontenera hosta jest odpowiedzialny za zarządzanie jego kolekcja obiektów wizualnych. Wymaga to, że kontenera hosta implementacji elementu członkowskiego zastąpienia pochodnej <xref:System.Windows.FrameworkElement> klasy.  
  
 Na poniższej liście opisano dwa elementy członkowskie, których konieczne jest przesłonięcie:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Zwraca kolekcję elementów podrzędnych elementu podrzędnego wskazywanego przez określony indeks.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Pobiera liczbę elementów podrzędnych visual w ramach tego elementu.  
  
 W poniższym przykładzie wartości zastąpień dla dwóch <xref:System.Windows.FrameworkElement> elementy członkowskie są implementowane.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Zapewnianie obsługi testowania trafień  
 Obiekt kontenera hosta może zapewnić obsługi zdarzeń, nawet wtedy, gdy nie są wyświetlane wszystkie właściwości widocznych — jednak jego <xref:System.Windows.UIElement.Visibility%2A> właściwość musi być równa <xref:System.Windows.Visibility.Visible>. Dzięki temu można utworzyć zdarzenia obsługi procedury dla kontenera hosta, w którym można przechwytywać zdarzenia myszy, takie jak wersja lewego przycisku myszy. Procedura obsługi zdarzeń można zaimplementować testowania trafień za pomocą wywołania <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. Metoda <xref:System.Windows.Media.HitTestResultCallback> parametr odnosi się do zdefiniowanych przez użytkownika procedury używanego w celu określenia wynikowe działanie hit test.  
  
 W poniższym przykładzie trafień obsługę testów został zaimplementowany dla obiektu kontenera hosta i jego elementy podrzędne.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
