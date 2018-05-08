---
title: 'Optymalizacja wydajności: układ i projekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 9c9921e664d69038480e73ee6779ca9e48b81c7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-layout-and-design"></a>Optymalizacja wydajności: układ i projekt
Projekt sieci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji może wpłynąć na jego wydajność, tworząc niepotrzebnego obciążenia obliczania układ i sprawdzanie poprawności odwołania do obiektów. Konstrukcja obiektów, szczególnie w czasie wykonywania mogą wpłynąć na charakterystykę wydajności aplikacji.  
  
 Ten temat zawiera zalecenia dotyczące wydajności w następujących obszarach.  
  
## <a name="layout"></a>Układ  
 Termin "przebiegu układu" opisano proces pomiarów i rozmieszczanie elementów członkowskich <xref:System.Windows.Controls.Panel>-pochodnych kolekcję elementów podrzędnych, a następnie je na ekranie rysowania obiektu. Przebiegu układ jest procesem ze sobą matematycznie intensywnie — im jest większa liczba elementów podrzędnych w kolekcji, im większa liczba wyliczenia wymagane. Na przykład po każdej aktualizacji elementu podrzędnego <xref:System.Windows.UIElement> obiektu w kolekcji zmianę położenia, ma możliwość wyzwolenia nowy przebieg przez system układu. Z powodu zamknięcia relacji między właściwości obiektu i zachowanie układu ważne jest zrozumienie typ zdarzenia, które może wywołać układu systemu. Aplikacji będą działać lepiej zmniejszając możliwie przekazać wszelkie niepotrzebne wywołania układu.  
  
 Układ systemu wykonuje dwie przejścia dla każdego elementu podrzędnego w kolekcji: przebiegu miary i przekazać Rozmieść. Każdy obiekt podrzędny zawiera własną implementację przesłoniętych <xref:System.Windows.UIElement.Measure%2A> i <xref:System.Windows.UIElement.Arrange%2A> metody w celu zapewnienia zachowania określonych układu. W najprostszym układu to system cyklicznej, który prowadzi do elementu trwa o rozmiarze, znajduje się i rysowane na ekranie.  
  
-   Element podrzędny <xref:System.Windows.UIElement> obiektu rozpoczyna proces układu przez jego właściwości core mierzony uprzedniego.  
  
-   Obiektu <xref:System.Windows.FrameworkElement> właściwości, które są związane z rozmiar, takich jak <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, i <xref:System.Windows.FrameworkElement.Margin%2A>, są sprawdzane.  
  
-   <xref:System.Windows.Controls.Panel>— Logika charakterystyczna zostanie zastosowana, takich jak <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość <xref:System.Windows.Controls.DockPanel>, lub <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwość <xref:System.Windows.Controls.StackPanel>.  
  
-   Zawartość jest rozmieszczone lub znajduje się po zostały zmierzone wszystkich obiektów podrzędnych.  
  
-   Kolekcja obiektów podrzędnych jest rysowana na ekranie.  
  
 Proces przekazywania układ jest wywoływana ponownie, jeśli wystąpienia któregokolwiek z następujących czynności:  
  
-   Obiekt podrzędny jest dodawany do kolekcji.  
  
-   A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> jest stosowany do obiektu podrzędnego.  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda jest wywoływana dla obiekt podrzędny.  
  
-   Gdy nastąpi zmiana wartości właściwości zależności, która jest oznaczony atrybutem metadanych wpływających na miary lub rozmieszczania przebiegów.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Skorzystaj z panelu najbardziej efektywne, gdy jest to możliwe  
 Złożoności procesu układu bezpośrednio opiera się na zachowanie układu <xref:System.Windows.Controls.Panel>-używasz elementów pochodnych. Na przykład <xref:System.Windows.Controls.Grid> lub <xref:System.Windows.Controls.StackPanel> kontroli udostępnia znacznie więcej funkcji niż <xref:System.Windows.Controls.Canvas> formantu. Cena za większy wzrost funkcji jest większa wzrost wydajności kosztów. Jednak jeśli nie potrzebujesz funkcji który <xref:System.Windows.Controls.Grid> zawiera formant, należy użyć mniej kosztowne rozwiązań alternatywnych, takich jak <xref:System.Windows.Controls.Canvas> lub niestandardowy panel.  
  
 Aby uzyskać więcej informacji, zobacz [omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Zaktualizuj zamiast zastąpić właściwość RenderTransform  
 Można aktualizować <xref:System.Windows.Media.Transform> zamiast zastąpienie jako wartość <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Jest to szczególnie istotne w scenariuszach obejmujących animacji. Aktualizacja istniejącej <xref:System.Windows.Media.Transform>, można uniknąć, inicjowanie obliczeń niepotrzebnych układu.  
  
### <a name="build-your-tree-top-down"></a>Tworzenie z drzewa góra dół  
 Gdy węzeł zostanie dodany lub usunięty z drzewa logicznego, pojawienia się właściwości invalidations nadrzędnego węzła i wszystkich jego obiektów podrzędnych. W związku z tym wzorzec konstrukcji góra dół zawsze można wykonać w celu uniknięcia koszt niepotrzebnych invalidations w węzłach, które już zostały zatwierdzone. W poniższej tabeli przedstawiono różnice szybkość wykonywania między tworzenia drzewa góra dół w zależności od dołu do góry, gdzie drzewa jest 150 poziomów w głąb za pomocą jednej <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.DockPanel> na każdym poziomie.  
  
|**Akcja**|**Drzewo kompilacji (w ms)**|**Renderowanie — zawiera drzewa kompilacji (w ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|Dołu do góry|366|454|  
|Góra dół|11|96|  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia top drzewa w dół.  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Aby uzyskać więcej informacji na drzewie logicznym, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Układ](../../../../docs/framework/wpf/advanced/layout.md)
