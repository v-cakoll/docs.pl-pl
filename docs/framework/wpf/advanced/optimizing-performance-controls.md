---
title: "Optymalizacja wydajności: kontrolki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1b414aee19082196ab242706c7730c031cf3a76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-controls"></a>Optymalizacja wydajności: kontrolki
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zawiera wiele wspólnych składników interfejsu użytkownika (UI), które są używane w większości aplikacji systemu Windows. Ten temat zawiera techniki zwiększanie wydajności interfejsu użytkownika.  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>Wyświetlanie dużych zestawów danych  
 Określa WPF, takich jak <xref:System.Windows.Controls.ListView> i <xref:System.Windows.Controls.ComboBox> służą do wyświetlania listy elementów w aplikacji. Jeśli na liście, aby wyświetlić jest duży, może mieć wpływ na wydajność aplikacji. Ponieważ układ standardowy system tworzy kontener układu dla każdego elementu skojarzony z formantem listy i oblicza układ rozmiar i położenie. Zazwyczaj nie trzeba wyświetlić wszystkie elementy w tym samym czasie; Zamiast tego wyświetlana podzbiór, a użytkownik przewija listy. W takim przypadku warto użyć interfejsu użytkownika *wirtualizacji*, co oznacza, że generowania elementu kontenera i skojarzone obliczeń układ dla elementu została odroczona, dopóki ten element jest widoczny.  
  
 Wirtualizacja interfejsu użytkownika jest ważnym aspektem kontrolki listy. Wirtualizacja interfejsu użytkownika nie należy mylić z wirtualizacji danych. Interfejs użytkownika wirtualizacji magazynów tylko widocznych elementów w pamięci, ale w przypadku wiązania danych przechowuje struktury danych w pamięci. W przypadku danych wirtualizacji przechowuje elementów danych, które są widoczne na ekranie w pamięci.  
  
 Domyślnie wirtualizacja interfejsu użytkownika jest włączona dla <xref:System.Windows.Controls.ListView> i <xref:System.Windows.Controls.ListBox> kontrolki, gdy ich elementy listy są związane z danymi. <xref:System.Windows.Controls.TreeView>można włączyć wirtualizacji przez ustawienie <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing` dołączona właściwość do `true`. Jeśli chcesz włączyć wirtualizacji interfejsu użytkownika dla formantów niestandardowych, które pochodzą z <xref:System.Windows.Controls.ItemsControl> lub istniejący element określa, które używają <xref:System.Windows.Controls.StackPanel> klas, takich jak <xref:System.Windows.Controls.ComboBox>, można ustawić <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> do <xref:System.Windows.Controls.VirtualizingStackPanel> i ustaw <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> do `true`. Niestety można wyłączyć wirtualizacji interfejsu użytkownika dla tych kontrolek bez wiedzy. Poniżej znajduje się lista warunków, które wirtualizacji interfejsu użytkownika jest wyłączona.  
  
-   Element kontenery zostaną dodane bezpośrednio do <xref:System.Windows.Controls.ItemsControl>. Na przykład, jeśli aplikacja jawnie dodaje <xref:System.Windows.Controls.ListBoxItem> obiekty do <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> nie wirtualizację <xref:System.Windows.Controls.ListBoxItem> obiektów.  
  
-   Element kontenerów w <xref:System.Windows.Controls.ItemsControl> są różnych typów. Na przykład <xref:System.Windows.Controls.Menu> używającą <xref:System.Windows.Controls.Separator> obiektów nie może implementować elementu odtwarzania, ponieważ <xref:System.Windows.Controls.Menu> zawiera obiekty typu <xref:System.Windows.Controls.Separator> i <xref:System.Windows.Controls.MenuItem>.  
  
-   Ustawienie <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> do `false`.  
  
-   Ustawienie <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>--> `IsVirtualizing` do `false`.    
  
 Ważną kwestią podczas wirtualizacji kontenery elementu jest, czy masz stanu dodatkowe informacje skojarzone z kontenera elementu, który należy do elementu. W takim przypadku należy zapisać dodatkowe stanu. Na przykład może być element zawarty w <xref:System.Windows.Controls.Expander> kontroli i <xref:System.Windows.Controls.Expander.IsExpanded%2A> stanu jest powiązany z elementu w kontenerze, a nie sam element. Gdy kontener zostanie ponownie użyty dla nowego elementu bieżącą wartość <xref:System.Windows.Controls.Expander.IsExpanded%2A> jest używany dla nowego elementu. Ponadto stary element utraci poprawny <xref:System.Windows.Controls.Expander.IsExpanded%2A> wartość.  
  
 Obecnie nie formantów WPF oferuje wbudowaną obsługę wirtualizacji danych.  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>Kontener odtwarzania  
 Optymalizacja do wirtualizacji interfejsu użytkownika dodany do programu .NET Framework 3.5 SP1 dla formantów, które dziedziczą z <xref:System.Windows.Controls.ItemsControl> jest *kontenera odtwarzania,* mogą także podnieść wydajność przewijania.  Gdy <xref:System.Windows.Controls.ItemsControl> czy wirtualizacji interfejsu użytkownika używa zostanie wypełnione, tworzy kontener elementu dla każdego elementu, który jest przewijane w widoku i niszczy element kontenera dla każdego elementu, który przewija niewidocznymi. *Odtwarzanie kontenera* umożliwia kontrolę do ponownego użycia istniejących kontenery elementu różne elementy danych, dzięki czemu kontenery elementu ciągle nie są tworzone i niszczone, gdy użytkownik przewija <xref:System.Windows.Controls.ItemsControl>. Można wybrać umożliwić odzyskiwanie przez ustawienie elementu <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> dołączona właściwość do <xref:System.Windows.Controls.VirtualizationMode.Recycling>.  
  
 Wszelkie <xref:System.Windows.Controls.ItemsControl> obsługującego wirtualizacji, można użyć kontenera odtwarzania.  Przykład sposobu włączania kontenera odtwarzanie na <xref:System.Windows.Controls.ListBox>, zobacz [poprawić wydajność przewijanie ListBox](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>Obsługa dwukierunkowych wirtualizacji  
 <xref:System.Windows.Controls.VirtualizingStackPanel>udostępnia wbudowaną obsługę wirtualizacji interfejsu użytkownika w jednym kierunku, poziomo czy pionowo. Jeśli chcesz użyć wirtualizacji dwukierunkowego dla formantów, musi implementować niestandardowe panelu, rozszerzający <xref:System.Windows.Controls.VirtualizingStackPanel> klasy. <xref:System.Windows.Controls.VirtualizingStackPanel> Klasy udostępnia metody wirtualnej, takie jak <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, i <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Te metody wirtualne umożliwiają wykrywa zmian w widoczną część listy i odpowiednio je obsłużyć.  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>Optymalizacja szablonów  
 Drzewa wizualnego zawiera wszystkie elementy wizualne w aplikacji.  Oprócz obiekty utworzone bezpośrednio także zawiera obiekty z powodu rozszerzeń szablonu.  Na przykład podczas tworzenia <xref:System.Windows.Controls.Button>, możesz również uzyskać <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> i <xref:System.Windows.Controls.ContentPresenter> obiektów w drzewie wizualnym.  Jeśli szablony formantu nie jest optymalizowane, może być utworzeniem partii bardzo niepotrzebnych obiektów w drzewie wizualnym.   Aby uzyskać więcej informacji na drzewie wizualnym, zobacz [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>Odroczone przewijania  
 Domyślnie gdy użytkownik przeciąga stronie przycisku suwaka na pasek przewijania, widok zawartości stale aktualizuje.  Jeśli przewijanie jest powolne formantu, należy rozważyć przy użyciu odroczone przewijania.  W odroczonego przewijanie zawartości jest aktualizowany tylko wtedy, gdy użytkownik zwolni stronie przycisku suwaka.  
  
 Aby zaimplementować odroczonego przewijania, ustaw <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> właściwości `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>dołączona właściwość a może ustawić na <xref:System.Windows.Controls.ScrollViewer> i żadnego formantu, który ma <xref:System.Windows.Controls.ScrollViewer> w szablonie formantu.  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>Formanty, które implementuje funkcje wydajności  
 W poniższej tabeli wymieniono wspólne kontrolki do wyświetlania danych i ich obsługi funkcji wydajności.  Zobacz poprzednich sekcjach, aby uzyskać informacje o sposobie włączania tych funkcji.  
  
|Formant|Wirtualizacja|Kontener odtwarzania|Odroczone przewijania|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Można włączyć|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.ContextMenu>|Można włączyć|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.DocumentViewer>|Niedostępne|Niedostępne|Można włączyć|  
|<xref:System.Windows.Controls.ListBox>|Domyślny|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.ListView>|Domyślny|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.TreeView>|Można włączyć|Można włączyć|Można włączyć|  
|<xref:System.Windows.Controls.ToolBar>|Niedostępne|Niedostępne|Można włączyć|  
  
> [!NOTE]
>  Przykład sposobu włączania wirtualizacji i kontener odtwarzanie na <xref:System.Windows.Controls.TreeView>, zobacz [poprawić wydajność w elemencie TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Układ](../../../../docs/framework/wpf/advanced/layout.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Formanty](../../../../docs/framework/wpf/controls/index.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Wskazówki: Buforowania danych aplikacji w aplikacji WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
