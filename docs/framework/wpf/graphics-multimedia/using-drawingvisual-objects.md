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
ms.openlocfilehash: e76ac22d4b8205576c8ed9ab67482c143a52fbd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565317"
---
# <a name="using-drawingvisual-objects"></a>Użycie obiektów DrawingVisual
Ten temat zawiera omówienie sposobu użycia <xref:System.Windows.Media.DrawingVisual> obiekty w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual warstwy.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Obiekt DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> To lekkie rysowania klasy, który jest używany do renderowania kształty, obrazy i tekst. Ta klasa jest traktowane jako lekkie, ponieważ nie dostarcza obsługi układu lub zdarzeń, co zwiększa wydajność. Z tego powodu rysunki idealnie nadają się do tła i grafik przycinania.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>Kontener DrawingVisual hosta  
 Aby można było używać <xref:System.Windows.Media.DrawingVisual> obiektów, należy utworzyć kontener hosta dla obiektów. Obiekt kontenera hosta musi pochodzić od <xref:System.Windows.FrameworkElement> klasy, która dostarcza układ i obsługa zdarzeń obsługi, który <xref:System.Windows.Media.DrawingVisual> klasa nie ma. Obiekt kontenera hosta nie są wyświetlane wszystkie właściwości widoczne, od momentu jego głównym celem jest zawierają obiekty podrzędne. Jednak <xref:System.Windows.UIElement.Visibility%2A> musi mieć ustawioną właściwość kontenera hosta <xref:System.Windows.Visibility.Visible>; w przeciwnym razie żaden z jego elementów podrzędnych nie będzie widoczna.  
  
 Podczas tworzenia obiektu hosta kontenera obiektów visual należy przechowywać odwołania do obiektów visual w <xref:System.Windows.Media.VisualCollection>. Użyj <xref:System.Windows.Media.VisualCollection.Add%2A> metody w celu dodania do hosta kontenera obiektu visual. W poniższym przykładzie tworzony jest obiekt kontenera hosta i trzy obiekty widoczne są dodawane do jej <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Dla przykładu kompletny kod, z którego został wyodrębniony w poprzednim przykładzie kodu, zobacz [trafień przy użyciu DrawingVisuals próbki](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Tworzenie obiektów DrawingVisual  
 Po utworzeniu <xref:System.Windows.Media.DrawingVisual> obiektu, nie ma on rysowania zawartości. Można dodać tekstu, grafiki lub obrazu zawartości przez pobranie obiektu <xref:System.Windows.Media.DrawingContext> i rysowania do niego. A <xref:System.Windows.Media.DrawingContext> jest zwracany przez wywołanie metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> obiektu.  
  
 Rysowanie w prostokącie <xref:System.Windows.Media.DrawingContext>, użyj <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu. Istnieje podobnych metod rysowania innych typów zawartości. Gdy skończysz rysowania zawartości do <xref:System.Windows.Media.DrawingContext>, wywołaj <xref:System.Windows.Media.DrawingContext.Close%2A> metody, aby zamknąć <xref:System.Windows.Media.DrawingContext> i utrwala zawartości.  
  
 W poniższym przykładzie <xref:System.Windows.Media.DrawingVisual> obiekt jest tworzony i prostokąt jest rysowana w jego <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Tworzenie zastąpień dla członków FrameworkElement  
 Obiekt kontenera hosta jest odpowiedzialny za zarządzanie jego kolekcja obiektów visual. Wymaga to, że kontener hosta implementuje element członkowski pochodnej zastąpienia <xref:System.Windows.FrameworkElement> klasy.  
  
 Poniżej opisano dwa elementy członkowskie, należy zastąpić:  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Zwraca element podrzędny o określonym indeksie kolekcji elementów podrzędnych.  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Pobiera liczbę elementów podrzędnych visual w tym elemencie.  
  
 W poniższym przykładzie zastąpień dla dwóch <xref:System.Windows.FrameworkElement> są implementowane elementy członkowskie.  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Zapewnianie obsługi testowania trafień  
 Obiekt kontenera hosta zapewniają obsługę zdarzeń nawet wtedy, gdy nie są wyświetlane wszystkie właściwości widoczne — jednak jego <xref:System.Windows.UIElement.Visibility%2A> musi mieć ustawioną właściwość <xref:System.Windows.Visibility.Visible>. Dzięki temu można utworzyć zdarzenia obsługi procedury dla kontenera hosta, który może być stosowane do zdarzeń myszy, takich jak wersja lewego przycisku myszy. Obsługa procedury zdarzeń można zaimplementować testowania trafień za pomocą <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. Metoda <xref:System.Windows.Media.HitTestResultCallback> parametr odnosi się do zdefiniowanych przez użytkownika procedury, która służy do określenia wynikowy akcji testu trafienia.  
  
 W poniższym przykładzie trafień testowania obsługi został zaimplementowany dla obiekt kontenera hosta i jego elementów podrzędnych.  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Test trafienia w warstwie wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
