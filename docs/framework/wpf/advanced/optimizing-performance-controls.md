---
title: 'Optymalizacja wydajności: Formanty'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 0917b1555f98fca9cf48cb7d208992848bd8e4b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694636"
---
# <a name="optimizing-performance-controls"></a>Optymalizacja wydajności: Formanty
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawiera wiele wspólnych składników interfejsu użytkownika (UI), które są używane w większości aplikacji Windows. Ten temat zawiera technik poprawę wydajności interfejsu użytkownika.  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>Wyświetlanie dużych zestawów danych  
 Określa WPF, takich jak <xref:System.Windows.Controls.ListView> i <xref:System.Windows.Controls.ComboBox> są używane do wyświetlania listy elementów w aplikacji. W przypadku dużych listy, aby wyświetlić może mieć wpływ na wydajność aplikacji. Ponieważ system standardowego układu, tworzy kontener układu dla każdego elementu skojarzonego z kontrolką listy i oblicza układ rozmiar i położenie. Zazwyczaj nie trzeba wyświetlić wszystkie elementy w tym samym czasie; Zamiast tego wyświetlić podzbiór, a użytkownik przewija listy. W takim przypadku warto użyć interfejsu użytkownika *wirtualizacji*, która oznacza, że generowania kontenera elementu i skojarzonych obliczeń układu dla elementu jest odroczone do czasu element jest widoczny.  
  
 Wirtualizacja interfejsu użytkownika jest istotnym elementem kontrolki listy. Wirtualizacja interfejsu użytkownika nie należy mylić z wirtualizacji danych. Interfejs użytkownika wirtualizacji przechowywanie widoczne tylko dla elementów w pamięci, ale w przypadku powiązania danych przechowuje struktury danych w pamięci. Z kolei wirtualizacji danych przechowuje elementy danych, które są widoczne na ekranie w pamięci.  
  
 Domyślnie wirtualizacja interfejsu użytkownika jest włączona dla <xref:System.Windows.Controls.ListView> i <xref:System.Windows.Controls.ListBox> kontrolki, gdy ich elementy listy są powiązane z danymi. <xref:System.Windows.Controls.TreeView> można włączyć wirtualizacji, ustawiając <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing` dołączonych właściwości `true`. Jeśli chcesz włączyć wirtualizację interfejsu użytkownika w przypadku kontrolek niestandardowych, które wynikają z <xref:System.Windows.Controls.ItemsControl> lub istniejący element kontrolki używające <xref:System.Windows.Controls.StackPanel> klasy, takie jak <xref:System.Windows.Controls.ComboBox>, można ustawić <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> do <xref:System.Windows.Controls.VirtualizingStackPanel> i ustaw <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> do `true`. Niestety możesz wyłączyć wirtualizacji interfejsu użytkownika dla tych formantów bez wiedzy. Oto lista warunków, które wyłączają wirtualizacja interfejsu użytkownika.  
  
-   Element kontenery są dodawane bezpośrednio do <xref:System.Windows.Controls.ItemsControl>. Na przykład, jeśli aplikacja jawnie dodaje <xref:System.Windows.Controls.ListBoxItem> obiekty do <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> nie wirtualizacji <xref:System.Windows.Controls.ListBoxItem> obiektów.  
  
-   Element kontenerów w <xref:System.Windows.Controls.ItemsControl> są różnych typów. Na przykład <xref:System.Windows.Controls.Menu> , który używa <xref:System.Windows.Controls.Separator> obiektów nie może implementować elementu odtwarzania, ponieważ <xref:System.Windows.Controls.Menu> zawiera obiekty typu <xref:System.Windows.Controls.Separator> i <xref:System.Windows.Controls.MenuItem>.  
  
-   Ustawienie <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> do `false`.  
  
-   Ustawienie <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>--> `IsVirtualizing` do `false`.    
  
 Ważną kwestią w przypadku wirtualizacji kontenerów elementów jest, czy masz informacje o stanie dodatkowe związane z kontenera elementu, który należy z elementem. W takim przypadku należy zapisać dodatkowy stan. Na przykład, Niewykluczone, że element zawarty w <xref:System.Windows.Controls.Expander> kontroli i <xref:System.Windows.Controls.Expander.IsExpanded%2A> stanu jest powiązany element kontenera, a nie sam element. Gdy kontener jest ponownie dla nowego elementu, bieżąca wartość <xref:System.Windows.Controls.Expander.IsExpanded%2A> jest używany dla nowego elementu. Ponadto stary element utraci poprawny <xref:System.Windows.Controls.Expander.IsExpanded%2A> wartość.  
  
 Obecnie brak kontrolek WPF oferuje wbudowaną obsługę wirtualizacji danych.  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>Odtwarzanie kontenera  
 Optymalizacja do wirtualizacji interfejsu użytkownika dodano w .NET Framework 3.5 SP1 dla formantów, które dziedziczą z <xref:System.Windows.Controls.ItemsControl> jest *odtwarzanie kontenera,* może również zwiększyć wydajność.  Gdy <xref:System.Windows.Controls.ItemsControl> czy wirtualizacja interfejsu użytkownika używa jest wypełniana, tworzy kontener elementów dla każdego elementu, który stanie się widoczny i niszczy kontenera elementu dla każdego elementu, który przewija poza widokiem. *Odtwarzanie kontenera* umożliwia kontrolowanie, to ponowne użycie istniejących kontenerów elementów dla różne elementy danych, tak aby kontenerów elementów nie stale są tworzone i niszczone, gdy użytkownik przewija <xref:System.Windows.Controls.ItemsControl>. Można wybrać włączyć odzyskiwanie, ustawiając element <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling>.  
  
 Wszelkie <xref:System.Windows.Controls.ItemsControl> obsługiwanych przez wirtualizacji, można użyć odtwarzanie kontenera.  Przykład sposobu włączania kontenera odtwarzanie na <xref:System.Windows.Controls.ListBox>, zobacz [zwiększa wydajność przewijanie ListBox](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>Obsługa dwukierunkowych wirtualizacji  
 <xref:System.Windows.Controls.VirtualizingStackPanel> udostępnia wbudowaną obsługę wirtualizacja interfejsu użytkownika w jednym kierunku, poziomo czy pionowo. Jeśli chcesz korzystać z wirtualizacji dwukierunkowe dla formantów, musisz zaimplementować niestandardowy panel, która rozszerza <xref:System.Windows.Controls.VirtualizingStackPanel> klasy. <xref:System.Windows.Controls.VirtualizingStackPanel> Klasa udostępnia metody wirtualne <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, i <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Te metody wirtualne umożliwiają wykrywanie zmian w widoczna część listy i odpowiednio je obsłużyć.  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>Optymalizacja szablonów  
 Drzewo wizualne zawiera wszystkie elementy wizualne w aplikacji.  Oprócz obiektów utworzone bezpośrednio zawiera ona także obiekty z powodu rozszerzenie szablonu.  Na przykład po utworzeniu <xref:System.Windows.Controls.Button>, możesz także uzyskać <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> i <xref:System.Windows.Controls.ContentPresenter> obiektów w drzewie wizualnym.  Jeśli nie zostały zoptymalizowane pod kątem szablonów kontrolki, może być utworzeniem wiele dodatkowych niepotrzebne obiektów w drzewie wizualnym.   Aby uzyskać więcej informacji na temat drzewa wizualnego, zobacz [Przegląd Renderowanie grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>Odroczone przewijania  
 Domyślnie gdy użytkownik przeciągnie miniatury na scrollbar, widok zawartości stale aktualizowane.  Jeśli przewijanie odbywa się powoli w kontrolce, należy rozważyć przy użyciu odroczone przewijania.  W odroczonego przewijanie zawartości jest aktualizowana tylko wtedy, gdy użytkownik zwolni przycisku suwaka.  
  
 Aby zaimplementować odroczonego przewijania, ustaw <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> właściwość `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> dołączona właściwość a może ustawić na <xref:System.Windows.Controls.ScrollViewer> i dowolną kontrolkę, która ma <xref:System.Windows.Controls.ScrollViewer> w szablonie kontrolki.  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>Formanty, które implementują funkcje wydajności  
 W poniższej tabeli wymieniono wspólnych formantów do wyświetlania danych i ich obsługa funkcje wydajności.  Zobacz poprzednie sekcje, aby uzyskać informacje na temat włączyć te funkcje.  
  
|Formant|Wirtualizacja|Odtwarzanie kontenera|Odroczone przewijania|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Można włączyć|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.ContextMenu>|Można włączyć|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.DocumentViewer>|Niedostępne|Niedostępne|Można włączyć|  
|<xref:System.Windows.Controls.ListBox>|Domyślny|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.ListView>|Domyślny|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.TreeView>|Można włączyć|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.ToolBar>|Niedostępne|Niedostępne|Można włączyć|  
  
> [!NOTE]
>  Na przykład jak włączyć wirtualizacji i odtwarzanie na kontenera <xref:System.Windows.Controls.TreeView>, zobacz [poprawić wydajność TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Układ](../../../../docs/framework/wpf/advanced/layout.md)
- [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
- [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Kontrolki](../../../../docs/framework/wpf/controls/index.md)
- [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Przewodnik: Buforowanie danych aplikacji w aplikacji WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
