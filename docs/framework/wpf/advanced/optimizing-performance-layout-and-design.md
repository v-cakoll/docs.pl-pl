---
title: 'Optymalizacja wydajności: Układ i projekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: e62b439926465aa1a61abd39c7c942acf26732c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367950"
---
# <a name="optimizing-performance-layout-and-design"></a>Optymalizacja wydajności: Układ i projekt
Projekt usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji może mieć wpływ na jego wydajność, tworząc niepotrzebne koszty Obliczanie układu i sprawdzanie poprawności odwołania do obiektu. Konstrukcja obiektów, szczególnie w czasie wykonywania, może wpłynąć na charakterystykę wydajności aplikacji.  
  
 Ten temat zawiera zalecenia dotyczące wydajności w następujących obszarach.  
  
## <a name="layout"></a>Układ  
 Termin "przekazanie układu" w tym artykule opisano proces pomiaru i rozmieszczanie elementów członkowskich <xref:System.Windows.Controls.Panel>-pochodzi z obiektu kolekcji elementów podrzędnych, a następnie narysować je na ekranie. Przekazanie układu jest procesem ze sobą matematycznie intensywnie — im większa liczba elementów podrzędnych w kolekcji, większa liczba obliczeń wymagana. Na przykład każdym elementem podrzędnym <xref:System.Windows.UIElement> zmieni się jego położenie obiektu w kolekcji, ma możliwość wyzwalania nowy przebieg przez system układu. Ze względu na Zamknij relacji między właściwości obiektu i zachowanie układu ważne jest zrozumienie typ zdarzenia, które można wywołać system układu. Aplikacji będą działać lepiej dzięki zmniejszeniu możliwie przekazywania wszelkie niepotrzebne wywołania układu.  
  
 System układu wykonuje dwa przejścia dla każdego elementu podrzędnego w kolekcji: przebieg miary i przekazać Rozmieść. Każdy obiekt podrzędny zawiera własną implementację zgodnym z przesłoniętą <xref:System.Windows.UIElement.Measure%2A> i <xref:System.Windows.UIElement.Arrange%2A> metody, aby zapewnić zachowanie określonego układu. W najprostszym układ jest systemem cyklicznej, który prowadzi do bycia elementu o rozmiarze, umieszczony i rysowane na ekranie.  
  
-   Element podrzędny <xref:System.Windows.UIElement> obiektu rozpoczyna proces układ przez pierwszy jej podstawowe właściwości mierzone.  
  
-   Obiekt <xref:System.Windows.FrameworkElement> właściwości, które są powiązane z rozmiar, takich jak <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, i <xref:System.Windows.FrameworkElement.Margin%2A>, są oceniane.  
  
-   <xref:System.Windows.Controls.Panel>— Logika charakterystyczna zostanie zastosowana, takich jak <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość <xref:System.Windows.Controls.DockPanel>, lub <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwość <xref:System.Windows.Controls.StackPanel>.  
  
-   Zawartość jest uporządkowane lub umieszczone po wszystkich obiektów podrzędnych zostały zmierzone.  
  
-   Kolekcja obiektów podrzędnych jest rysowana na ekranie.  
  
 Proces — dostęp próbny układu zostanie wywołana ponownie, jeśli wystąpi dowolne z następujących czynności:  
  
-   Obiekt podrzędny zostanie dodany do kolekcji.  
  
-   Element <xref:System.Windows.FrameworkElement.LayoutTransform%2A> jest stosowany do obiektu podrzędnego.  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda jest wywoływana dla obiektu podrzędnego.  
  
-   Gdy wystąpi zmiana wartości właściwości zależności, który jest oznaczony za pomocą metadanych wpływających na miary lub Rozmieść przebiegów.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Skorzystaj z panelu najbardziej efektywny sposób, jeśli jest to możliwe  
 Złożoności procesu układ jest bezpośrednio oparty na podstawie zachowania układ <xref:System.Windows.Controls.Panel>-pochodnych elementy, możesz użyć. Na przykład <xref:System.Windows.Controls.Grid> lub <xref:System.Windows.Controls.StackPanel> control oferuje znacznie więcej funkcji niż <xref:System.Windows.Controls.Canvas> kontroli. Cena za to zwiększenie większą funkcjonalność jest większa wzrost kosztów wydajności. Jednakże jeśli nie potrzebujesz funkcji, <xref:System.Windows.Controls.Grid> udostępnia kontrolki, należy użyć mniej kosztowne rozwiązania alternatywne, takiego jak <xref:System.Windows.Controls.Canvas> lub niestandardowy panel.  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd panele](../controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Aktualizacji, a nie zamienić RenderTransform  
 Może być w stanie zaktualizować <xref:System.Windows.Media.Transform> zamiast zastąpienie jako wartość <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Jest to szczególnie istotne w scenariuszach obejmujących animacji. Aktualizacja istniejącego <xref:System.Windows.Media.Transform>, można uniknąć, inicjowanie obliczeń niepotrzebne układu.  
  
### <a name="build-your-tree-top-down"></a>Twórz swoje drzewa góra dół  
 Gdy węzeł jest dodawany lub usuwany z drzewa logicznego, invalidations właściwości są inicjowane na węzeł nadrzędny i wszystkich jego obiektów podrzędnych. W rezultacie wzorzec konstrukcji góra dół zawsze powinien być używany do uniknąć kosztów niepotrzebne invalidations w węzłach, które już zostały zweryfikowane. W poniższej tabeli przedstawiono różnice w szybkości wykonywania między kompilacją drzewa góra dół w zależności od dołu do góry, gdzie drzewa jest 150 poziomów w głąb za pomocą jednego <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.DockPanel> na każdym poziomie.  
  
|**Akcja**|**Drzewo kompilowania (w ms)**|**Renderowanie — zawiera drzewo kompilowania (w ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|Od dołu do góry|366|454|  
|Góra dół|11|96|  
  
 Poniższy przykład kodu demonstruje sposób tworzenia najwyższego drzewa w dół.  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](trees-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz także
- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
- [Układ](layout.md)
