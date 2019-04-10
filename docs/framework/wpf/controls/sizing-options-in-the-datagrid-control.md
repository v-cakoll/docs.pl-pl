---
title: Opcje ustalania rozmiaru w formancie DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 6d100fb17b1ee3e652985a637d333d9f65e20d36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219203"
---
# <a name="sizing-options-in-the-datagrid-control"></a>Opcje ustalania rozmiaru w formancie DataGrid
Różne opcje są dostępne do kontroli sposób, w jaki <xref:System.Windows.Controls.DataGrid> rozciąga się. <xref:System.Windows.Controls.DataGrid>, A poszczególne wiersze i kolumny w <xref:System.Windows.Controls.DataGrid>, można ustawić rozmiar automatycznie, aby ich zawartość lub może być ustawiona na określone wartości. Domyślnie <xref:System.Windows.Controls.DataGrid> będzie rosnąć i Dopasuj przez zmniejszenie rozmiaru jego zawartość.  
  
## <a name="sizing-the-datagrid"></a>Ustalanie rozmiaru DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Ostrzeżenia w przypadku korzystania z automatycznej zmiany rozmiaru  
 Domyślnie <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości <xref:System.Windows.Controls.DataGrid> są ustawione na <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" w XAML), a <xref:System.Windows.Controls.DataGrid> zostanie dostosowana do rozmiaru jego zawartość.  
  
 Po umieszczeniu w kontenerze, który nie ogranicza rozmiar jego elementy podrzędne, takie jak <xref:System.Windows.Controls.Canvas> lub <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.DataGrid> rozciągana poza granice kontenera widoczne i nie będą wyświetlane paski przewijania. Ten problem ma wpływ zarówno użyteczność i wydajność.  
  
 Podczas wiązania z zestawem danych, jeśli <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> jest nie jest ograniczona, nadal będzie Dodaj wiersz dla każdego elementu danych w zestawie danych powiązanych. Może to spowodować <xref:System.Windows.Controls.DataGrid> się poza granicami widoczne aplikacji wiersze są dodawane. <xref:System.Windows.Controls.DataGrid> Będą wyświetlały paski przewijania w tym przypadku ponieważ jej <xref:System.Windows.FrameworkElement.Height%2A> będą w dalszym ciągu Rozwijaj w celu uwzględnienia nowych wierszy.  
  
 Obiekt jest tworzony dla każdego wiersza w <xref:System.Windows.Controls.DataGrid>. Jeśli pracujesz z dużym zestawem danych i zezwolisz na <xref:System.Windows.Controls.DataGrid> automatycznie sam rozmiar, tworzenia dużą liczbę obiektów może mieć wpływ na wydajność aplikacji.  
  
 Aby uniknąć tych problemów podczas pracy z dużymi zestawami danych, zaleca się, że specjalnie skonfigurować <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> lub umieścić go w kontenerze, który ograniczy jego <xref:System.Windows.FrameworkElement.Height%2A>, takich jak <xref:System.Windows.Controls.Grid>. Gdy <xref:System.Windows.FrameworkElement.Height%2A> jest ograniczona, <xref:System.Windows.Controls.DataGrid> utworzy tylko wiersze, które zmieści się w jego określonego <xref:System.Windows.FrameworkElement.Height%2A>i odtworzenie tych wierszy, zgodnie z potrzebami, aby wyświetlić nowe dane.  
  
### <a name="setting-the-datagrid-size"></a>Ustawianie rozmiaru DataGrid  
 <xref:System.Windows.Controls.DataGrid> Można ustawić, aby automatycznie rozmiar w granicach określonego lub <xref:System.Windows.Controls.DataGrid> może być ustawiona na określonym rozmiarze. W poniższej tabeli przedstawiono właściwości, które można ustawić kontroli <xref:System.Windows.Controls.DataGrid> rozmiar.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Ustawia określone wysokość dla mierników <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Określa górną granicę wysokość <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Będzie rosnąć w pionie, aż do osiągnięcia tego wysokość.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Ustawia dolną granicę wysokość <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Będzie się zmniejszać pionowo aż do osiągnięcia tego wysokość.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Ustawia szerokość określonych <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Określa górną granicę szerokości <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Będzie rosnąć w poziomie, aż do osiągnięcia tej szerokości.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Ustawia dolną granicę szerokości <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Będzie się zmniejszać poziomo aż do osiągnięcia tej szerokości.|  
  
## <a name="sizing-rows-and-row-headers"></a>Zmiana rozmiaru wierszy i nagłówków wierszy  
  
### <a name="datagrid-rows"></a>Wiersze DataGrid  
 Domyślnie <xref:System.Windows.Controls.DataGrid> wiersza <xref:System.Windows.FrameworkElement.Height%2A> właściwość jest ustawiona na <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" w XAML), i wiersze o nierównej wysokości rozwinie się do rozmiaru jego zawartość. Wysokość wszystkich wierszy w <xref:System.Windows.Controls.DataGrid> można określić, ustawiając <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> właściwości. Użytkownicy mogą zmieniać wysokość wiersza sekcjami nagłówek wiersza.  
  
### <a name="datagrid-row-headers"></a>Nagłówki wierszy DataGrid  
 Aby wyświetlić nagłówki wierszy <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> właściwość musi być równa <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> lub <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Domyślnie nagłówki wierszy są wyświetlane, i automatycznie rozmiar, aby zmieścić ich zawartości. Nagłówki wierszy można podać określonej szerokości, ustawiając <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="sizing-columns-and-column-headers"></a>Zmiana rozmiaru kolumn i nagłówków kolumn  
  
### <a name="datagrid-columns"></a>Kolumny DataGrid  
 <xref:System.Windows.Controls.DataGrid> Używa wartości <xref:System.Windows.Controls.DataGridLength> i <xref:System.Windows.Controls.DataGridLengthUnitType> struktury do określenia trybów zmieniania rozmiaru ścieżką bezwzględną lub automatyczne.  
  
 W poniższej tabeli przedstawiono wartości dostarczone przez <xref:System.Windows.Controls.DataGridLengthUnitType> struktury.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Domyślne automatycznej zmiany rozmiaru w trybie rozmiary <xref:System.Windows.Controls.DataGrid> kolumn na podstawie zawartości komórek i nagłówków kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Automatycznie na podstawie komórka rozmiaru rozmiary tryb <xref:System.Windows.Controls.DataGrid> kolumn na podstawie zawartości komórek w kolumnie, nie wliczając nagłówków kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Automatyczne opartej na nagłówkach zmiany rozmiaru w trybie rozmiary <xref:System.Windows.Controls.DataGrid> kolumn na podstawie zawartości tylko nagłówki kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Piksela na podstawie rozmiaru rozmiary tryb <xref:System.Windows.Controls.DataGrid> kolumny oparte na podana wartość liczbową.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Tryb gwiazdki zmiany rozmiaru służy do rozpowszechniania dostępnego miejsca przez ważona proporcji.<br /><br /> W XAML gwiazdki wartości są wyrażane jako n * n oznacza wartość liczbową. 1\* jest odpowiednikiem \*. Na przykład, jeśli dwie kolumny w <xref:System.Windows.Controls.DataGrid> ma szerokość kontrolki \* i 2\*, pierwszą kolumnę otrzyma jedną część dostępnego miejsca, i druga kolumna otrzyma dostępnego miejsca na dwie części.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> Klasy można przekonwertować danych między wartościami numeryczny lub ciąg i <xref:System.Windows.Controls.DataGridLength> wartości.  
  
 Domyślnie <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>i <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Jeśli tryb zmiany rozmiaru jest równa <xref:System.Windows.Controls.DataGridLength.Auto%2A> lub <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, będzie się zwiększać do szerokości ich jak najszerszego widocznej zawartości kolumny. Podczas przewijania, tych trybów zmieniania rozmiaru spowoduje, że kolumny do rozwinięcia w przypadku zawartości, które jest większy niż bieżący rozmiar kolumny jest przewijane do widoku. Kolumna nie będzie się zmniejszać, po zawartości jest przewijane poza widokiem.  
  
 Kolumny w <xref:System.Windows.Controls.DataGrid> można również ustawić automatycznie rozmiar tylko w granicach określonego lub kolumny może być ustawiona na określonym rozmiarze. W poniższej tabeli przedstawiono właściwości, które można ustawić, aby kontrolować rozmiarów kolumn.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Określa górną granicę dla wszystkich kolumn w <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Określa górną granicę dla poszczególnych kolumn. Zastępuje <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Ustawia dolną granicę dla wszystkich kolumn w <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Ustawia dolną granicę dla poszczególnych kolumn. Zastępuje <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Ustawia określona we wszystkich kolumnach <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Ustawia określonej szerokości dla poszczególnych kolumn. Zastępuje <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>Nagłówki kolumn DataGrid  
 Domyślnie <xref:System.Windows.Controls.DataGrid> nagłówki kolumn są wyświetlane. Aby ukryć nagłówki kolumn <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> właściwość musi być równa <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> lub <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Domyślnie gdy nagłówki kolumn są wyświetlane, są automatycznie rozmiar dopasowana do ich zawartości. Nagłówki kolumn można podać określonej wysokości, ustawiając <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="resizing-with-the-mouse"></a>Zmiana rozmiaru za pomocą myszy  
 Użytkownicy mogą zmieniać rozmiar <xref:System.Windows.Controls.DataGrid> wierszy i kolumn sekcjami nagłówek wiersza lub kolumny. <xref:System.Windows.Controls.DataGrid> Obsługuje również automatyczna zmiana rozmiaru wierszy i kolumn, klikając dwukrotnie wiersz lub kolumnę linii podziału nagłówka. Aby zapobiec zmiana rozmiaru kolumn określonej przez użytkownika, ustaw <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> właściwość `false` dla poszczególnych kolumn. Aby uniemożliwić użytkownikom zmienianie rozmiaru wszystkich kolumn, należy ustawić <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> właściwość `false`. Aby uniemożliwić użytkownikom zmienianie rozmiaru wszystkich wierszy, ustawianie <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> właściwość `false`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
