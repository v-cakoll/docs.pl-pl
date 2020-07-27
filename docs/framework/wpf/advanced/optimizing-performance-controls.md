---
title: Optymalizowanie wydajności kontroli
description: Windows Presentation Foundation zawiera wiele typowych składników, które są używane w większości aplikacji systemu Windows. Dowiedz się, jak poprawić wydajność interfejsu użytkownika.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: de348dd93e5710b5b81af035ec7aa56e01dc4981
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168311"
---
# <a name="optimizing-performance-controls"></a>Optymalizacja wydajności: kontrolki

Windows Presentation Foundation (WPF) zawiera wiele typowych składników interfejsu użytkownika, które są używane w większości aplikacji systemu Windows. Ten temat zawiera techniki ulepszania wydajności interfejsu użytkownika.

## <a name="displaying-large-data-sets"></a>Wyświetlanie dużych zestawów danych

Formanty WPF, takie jak i, służą <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ComboBox> do wyświetlania list elementów w aplikacji. Jeśli lista, która ma zostać wyświetlona, jest duża, może to wpłynąć na wydajność aplikacji. Wynika to z faktu, że standardowy układ układu tworzy kontener układu dla każdego elementu skojarzonego z kontrolką listy i oblicza jego rozmiar i położenie układu. Zazwyczaj nie ma potrzeby wyświetlania wszystkich elementów w tym samym czasie; Zamiast tego zostanie wyświetlony podzestaw, a użytkownik przewija listę. W tym przypadku warto używać *wirtualizacji*interfejsu użytkownika, co oznacza, że generowanie kontenera elementów i powiązane obliczenia układu dla elementu są odroczone do momentu wyświetlenia elementu.

Wirtualizacja interfejsu użytkownika jest ważnym aspektem formantów listy. Wirtualizacja interfejsu użytkownika nie należy mylić z wirtualizacją danych. Wirtualizacja interfejsu użytkownika przechowuje tylko widoczne elementy w pamięci, ale w scenariuszu powiązania danych przechowuje całą strukturę danych w pamięci. W przeciwieństwie do wirtualizacji danych są przechowywane tylko te elementy danych, które są widoczne na ekranie w pamięci.

Domyślnie Wirtualizacja interfejsu użytkownika jest włączona dla <xref:System.Windows.Controls.ListView> formantów i, <xref:System.Windows.Controls.ListBox> gdy ich elementy listy są powiązane z danymi. <xref:System.Windows.Controls.TreeView>wirtualizację można włączyć, ustawiając <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> przyłączoną właściwość na `true` . Jeśli chcesz włączyć wirtualizację interfejsu użytkownika dla kontrolek niestandardowych, które pochodzą z <xref:System.Windows.Controls.ItemsControl> lub istniejące kontrolki elementu, które używają <xref:System.Windows.Controls.StackPanel> klasy, na przykład <xref:System.Windows.Controls.ComboBox> , można ustawić na <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> <xref:System.Windows.Controls.VirtualizingStackPanel> i ustawić <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> na `true` . Niestety, można wyłączyć wirtualizację interfejsu użytkownika dla tych kontrolek bez jej realizacji. Poniżej znajduje się lista warunków, które wyłączają wirtualizację interfejsu użytkownika.

- Kontenery elementów są dodawane bezpośrednio do <xref:System.Windows.Controls.ItemsControl> . Na przykład, jeśli aplikacja jawnie dodaje <xref:System.Windows.Controls.ListBoxItem> obiekty do <xref:System.Windows.Controls.ListBox> , program nie będzie <xref:System.Windows.Controls.ListBox> wirtualizacji <xref:System.Windows.Controls.ListBoxItem> obiektów.

- Kontenery elementów w programie <xref:System.Windows.Controls.ItemsControl> mają różne typy. Na przykład, <xref:System.Windows.Controls.Menu> który używa <xref:System.Windows.Controls.Separator> obiektów nie może zaimplementować odtwarzania elementu, ponieważ <xref:System.Windows.Controls.Menu> zawiera obiekty typu <xref:System.Windows.Controls.Separator> i <xref:System.Windows.Controls.MenuItem> .

- Ustawienie <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> `false` .

- Ustawienie <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> `false` .

Ważnym zagadnieniem podczas wirtualizacji kontenerów elementów jest fakt, że masz dodatkowe informacje o stanie skojarzone z kontenerem elementu, który należy do elementu. W takim przypadku należy zapisać dodatkowy stan. Na przykład może istnieć element zawarty w <xref:System.Windows.Controls.Expander> kontrolce, a <xref:System.Windows.Controls.Expander.IsExpanded%2A> stan jest powiązany z kontenerem elementu, a nie do samego elementu. Gdy kontener zostanie ponownie użyty dla nowego elementu, bieżąca wartość <xref:System.Windows.Controls.Expander.IsExpanded%2A> jest używana dla nowego elementu. Ponadto stary element traci poprawną <xref:System.Windows.Controls.Expander.IsExpanded%2A> wartość.

Obecnie żadna kontrolka WPF nie oferuje wbudowanej obsługi wirtualizacji danych.

## <a name="container-recycling"></a>Odtwarzanie kontenera

Optymalizacja do wirtualizacji interfejsu użytkownika dodana w .NET Framework 3,5 SP1 dla formantów dziedziczących po <xref:System.Windows.Controls.ItemsControl> jest *odtwarzaniem kontenerów,* co może również zwiększyć wydajność przewijania. Gdy <xref:System.Windows.Controls.ItemsControl> zostanie wypełniony program korzystający z wirtualizacji interfejsu użytkownika, tworzy kontener elementów dla każdego elementu, który przewija do widoku i niszczy kontener elementów dla każdego elementu, który jest przewijany do widoku. *Odtwarzanie kontenera* umożliwia kontrolce ponowne użycie istniejących kontenerów elementów dla różnych elementów danych, dzięki czemu kontenery elementów nie są stale tworzone i niszczone, gdy użytkownik przewinie <xref:System.Windows.Controls.ItemsControl> . Można wybrać opcję włączenia odtwarzania elementu, ustawiając <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> Właściwość dołączone na <xref:System.Windows.Controls.VirtualizationMode.Recycling> .

Wszystkie <xref:System.Windows.Controls.ItemsControl> obsługujące wirtualizację mogą używać odtwarzania kontenerów. Aby zapoznać się z przykładem sposobu włączania odtwarzania kontenera na <xref:System.Windows.Controls.ListBox> , zobacz [Poprawianie wydajności przewijania listy](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)kontrolnej.

## <a name="supporting-bidirectional-virtualization"></a>Obsługa wirtualizacji dwukierunkowej

<xref:System.Windows.Controls.VirtualizingStackPanel>oferuje wbudowaną obsługę wirtualizacji interfejsu użytkownika w jednym kierunku w poziomie lub w pionie. Jeśli chcesz używać wirtualizacji dwukierunkowej dla kontrolek, musisz zaimplementować niestandardowy Panel, który rozszerza <xref:System.Windows.Controls.VirtualizingStackPanel> klasę. <xref:System.Windows.Controls.VirtualizingStackPanel>Klasa uwidacznia metody wirtualne, takie jak <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A> , <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A> , <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A> i <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A> . Te metody wirtualne pozwalają wykryć zmianę w widocznej części listy i odpowiednio ją obsłużyć.

## <a name="optimizing-templates"></a>Optymalizowanie szablonów

Drzewo wizualne zawiera wszystkie elementy wizualne w aplikacji. Oprócz obiektów tworzonych bezpośrednio, zawiera również obiekty z powodu rozwinięcia szablonu. Na przykład podczas tworzenia elementu <xref:System.Windows.Controls.Button> , można również uzyskać i wyświetlić <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.ContentPresenter> obiekty w drzewie wizualnym. Jeśli szablony kontroli nie zostały zoptymalizowane, można utworzyć wiele niepotrzebnych obiektów w drzewie wizualnym. Aby uzyskać więcej informacji na temat drzewa wizualnego, zobacz [Omówienie renderowania grafiki WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Przewijanie odroczone

Domyślnie, gdy użytkownik przeciąga element kciuka na pasku przewijania, widok zawartości jest ciągle aktualizowany. Jeśli przewijanie w kontrolce jest powolne, rozważ użycie przełożonego przewijania. W przypadku przewijania odroczonego zawartość jest aktualizowana tylko wtedy, gdy użytkownik zwolni przycisk przewijania.

Aby zaimplementować opóźnione przewijanie, ustaw <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> Właściwość na `true` . <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>jest dołączoną właściwością i można ją ustawić na <xref:System.Windows.Controls.ScrollViewer> i dowolną kontrolkę, która ma <xref:System.Windows.Controls.ScrollViewer> w szablonie kontrolki.

## <a name="controls-that-implement-performance-features"></a>Kontrolki implementujące funkcje wydajności

Poniższa tabela zawiera listę typowych kontrolek służących do wyświetlania danych i ich obsługi. Zapoznaj się z poprzednimi sekcjami, aby uzyskać informacje na temat włączania tych funkcji.

|Kontrola|Wirtualizacja|Odtwarzanie kontenera|Przewijanie odroczone|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Można włączyć|Można włączyć|Można włączyć|
|<xref:System.Windows.Controls.ContextMenu>|Można włączyć|Można włączyć|Można włączyć|
|<xref:System.Windows.Controls.DocumentViewer>|Niedostępne|Niedostępne|Można włączyć|
|<xref:System.Windows.Controls.ListBox>|Domyślne|Można włączyć|Można włączyć|
|<xref:System.Windows.Controls.ListView>|Domyślne|Można włączyć|Można włączyć|
|<xref:System.Windows.Controls.TreeView>|Można włączyć|Można włączyć|Można włączyć|
|<xref:System.Windows.Controls.ToolBar>|Niedostępne|Niedostępne|Można włączyć|

> [!NOTE]
> Aby zapoznać się z przykładem sposobu włączania wirtualizacji i odtwarzania kontenerów na serwerze <xref:System.Windows.Controls.TreeView> , zobacz [Poprawianie wydajności widoku TreeView](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Zobacz także

- [Układ](layout.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Formanty](../controls/index.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
