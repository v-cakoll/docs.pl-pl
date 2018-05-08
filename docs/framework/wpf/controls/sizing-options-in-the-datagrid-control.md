---
title: Opcje ustalania rozmiaru w formancie DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0019ac9ad82301506d2da279094b2c96e022e915
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sizing-options-in-the-datagrid-control"></a>Opcje ustalania rozmiaru w formancie DataGrid
Różne opcje są dostępne do kontroli jak <xref:System.Windows.Controls.DataGrid> sam rozmiar. <xref:System.Windows.Controls.DataGrid>i poszczególnych wierszy i kolumn w <xref:System.Windows.Controls.DataGrid>, może być ustawiony na rozmiar automatycznie, tak aby ich zawartość lub może być ustawiony na określone wartości. Domyślnie <xref:System.Windows.Controls.DataGrid> będzie wzrostu i zmniejszyć do rozmiaru jego zawartość.  
  
## <a name="sizing-the-datagrid"></a>Ustawianie rozmiaru formantu DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Ostrzeżenia, gdy przy użyciu automatycznej zmiany rozmiaru  
 Domyślnie <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości <xref:System.Windows.Controls.DataGrid> ustawiono <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" w języku XAML) i <xref:System.Windows.Controls.DataGrid> zostanie dostosowana do rozmiaru jego zawartość.  
  
 Gdy umieszczony wewnątrz kontenera, w którym nie ograniczają rozmiaru jego elementów podrzędnych, takich jak <xref:System.Windows.Controls.Canvas> lub <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.DataGrid> rozciąga poza granice widoczne kontenera i nie zostaną wyświetlone paski przewijania. Ten warunek ma wpływ zarówno użyteczność i wydajność.  
  
 Podczas wiązania z zestawem danych, jeśli <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> jest nie jest ograniczona, nadal będzie Dodaj wiersz dla każdego elementu danych w zestawie powiązania danych. Może to spowodować <xref:System.Windows.Controls.DataGrid> się poza granicami widoczne aplikacji dodanych wierszy. <xref:System.Windows.Controls.DataGrid> Nie zostanie wyświetlone paski przewijania w takim przypadku ponieważ jego <xref:System.Windows.FrameworkElement.Height%2A> będzie rosnąć w celu uwzględnienia nowych wierszy.  
  
 Obiekt jest tworzony dla każdego wiersza w <xref:System.Windows.Controls.DataGrid>. Jeśli pracujesz z dużych zestawów danych i umożliwia <xref:System.Windows.Controls.DataGrid> do automatycznie zmienia swój rozmiar, tworzenie dużą liczbę obiektów może mieć wpływ na wydajność aplikacji.  
  
 Aby uniknąć tych problemów podczas pracy z dużych zestawów danych, zalecane jest, w szczególności ustawienie <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> lub umieścić go w kontenerze, który ograniczy jego <xref:System.Windows.FrameworkElement.Height%2A>, takich jak <xref:System.Windows.Controls.Grid>. Gdy <xref:System.Windows.FrameworkElement.Height%2A> jest ograniczona, <xref:System.Windows.Controls.DataGrid> utworzy tylko wiersze, które zmieści się w jego określony <xref:System.Windows.FrameworkElement.Height%2A>i Odtwórz tych wierszy, zgodnie z potrzebami, aby wyświetlić nowe dane.  
  
### <a name="setting-the-datagrid-size"></a>Ustawianie rozmiaru formantu DataGrid  
 <xref:System.Windows.Controls.DataGrid> Można ustawić automatycznie rozmiar w określonych granic lub <xref:System.Windows.Controls.DataGrid> można ustawić określonego rozmiaru. W poniższej tabeli przedstawiono właściwości, które może być ustawiony na formant <xref:System.Windows.Controls.DataGrid> rozmiar.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Ustawia dla określonej wysokości <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Ustawia górna granica wysokość <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Będzie rosnąć w pionie, dopóki nie osiągnie ten wysokość.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Ustawia dolną granicę wysokość <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Zmniejsza się pionowo aż osiągnie ten wysokość.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Ustawia określonej szerokości dla <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Ustawia górna granica szerokość <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Będzie rosnąć w poziomie, dopóki nie osiągnie tej szerokości.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Ustawia dolną granicę szerokość <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Zmniejsza się poziomo aż do osiągnięcia tej szerokości.|  
  
## <a name="sizing-rows-and-row-headers"></a>Zmiana rozmiaru wierszy i nagłówków wierszy  
  
### <a name="datagrid-rows"></a>Wiersze DataGrid  
 Domyślnie <xref:System.Windows.Controls.DataGrid> wiersza <xref:System.Windows.FrameworkElement.Height%2A> właściwość jest ustawiona na <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" w języku XAML), i wysokość wiersza zostanie rozwinięty w celu rozmiar jego zawartości. Wysokość wszystkich wierszy w <xref:System.Windows.Controls.DataGrid> można określić przez ustawienie <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> właściwości. Użytkownicy mogą zmieniać wysokość wiersza sekcjami nagłówka wiersza.  
  
### <a name="datagrid-row-headers"></a>Nagłówki wierszy DataGrid  
 Aby wyświetlić nagłówki wierszy <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musi mieć ustawioną właściwość <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> lub <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Domyślnie nagłówki wierszy są wyświetlane i automatycznie rozmiar, aby dopasować jego zawartość. Nagłówki wierszy może mieć określonej szerokości przez ustawienie <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="sizing-columns-and-column-headers"></a>Ustawianie rozmiaru kolumn i nagłówków kolumn  
  
### <a name="datagrid-columns"></a>Kolumny Siatka danych  
 <xref:System.Windows.Controls.DataGrid> Używa wartości <xref:System.Windows.Controls.DataGridLength> i <xref:System.Windows.Controls.DataGridLengthUnitType> struktury określone tryby bezwzględne lub automatycznej zmiany rozmiaru.  
  
 W poniższej tabeli przedstawiono wartości podane przez <xref:System.Windows.Controls.DataGridLengthUnitType> struktury.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Domyślnie automatycznej zmiany rozmiaru w trybie rozmiary <xref:System.Windows.Controls.DataGrid> kolumn na podstawie zawartości komórek i nagłówków kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Automatycznie na podstawie komórki zmiany rozmiaru w trybie rozmiary <xref:System.Windows.Controls.DataGrid> kolumn na podstawie zawartości komórek w kolumnie nie włącznie z nagłówkami kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Automatycznie na podstawie nagłówka zmiany rozmiaru w trybie rozmiary <xref:System.Windows.Controls.DataGrid> kolumn na podstawie zawartości tylko w nagłówków kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Piksela na podstawie zmiany rozmiaru w trybie rozmiary <xref:System.Windows.Controls.DataGrid> kolumny oparte na podana wartość liczbową.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Tryb ustalania gwiazdy służy do dystrybucji dostępne miejsce ważoną proporcji.<br /><br /> W języku XAML gwiazdy wartości są wyrażane jako n oznacza wartość liczbową n *. 1\* jest odpowiednikiem \*. Na przykład, jeśli dwie kolumny w <xref:System.Windows.Controls.DataGrid> miał szerokości \* i 2\*, pierwsza kolumna otrzyma jedną część dostępne miejsce i drugiej kolumnie otrzyma dwie części dostępnego miejsca.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> Klasa może być używana do konwertowania danych między wartościami numeryczny lub ciąg i <xref:System.Windows.Controls.DataGridLength> wartości.  
  
 Domyślnie <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>i <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Jeśli ustawiono tryb ustalania <xref:System.Windows.Controls.DataGridLength.Auto%2A> lub <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, wzrośnie kolumny do szerokości ich najszerszych widocznej zawartości. Podczas przewijania, te tryby rozmiaru spowoduje, że kolumny do rozwinięcia, jeśli zawartość jest większy niż bieżący rozmiar kolumny jest wyświetlony w wyniku przewijania. Kolumna nie zmniejszy się po zawartości jest przewijane poza widoku.  
  
 Kolumn w <xref:System.Windows.Controls.DataGrid> można również ustawić automatycznie rozmiar tylko w określonych granic lub kolumny może być ustawiony na określony rozmiar. W poniższej tabeli przedstawiono właściwości, które można ustawić do kontrolowania rozmiarów kolumn.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Ustawia górna granica we wszystkich kolumnach <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Ustawia górna granica dla pojedynczej kolumny. Zastępuje <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Określa dolne ograniczenie dla wszystkich kolumn w <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Określa dolne ograniczenie dla pojedynczej kolumny. Zastępuje <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Ustawia określonej szerokości dla wszystkich kolumn w <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Ustawia określonej szerokości dla pojedynczej kolumny. Zastępuje <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>Nagłówki kolumn formantu DataGrid  
 Domyślnie <xref:System.Windows.Controls.DataGrid> nagłówki kolumn są wyświetlane. Aby ukryć nagłówki kolumn <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musi mieć ustawioną właściwość <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> lub <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Domyślnie jeśli nagłówki kolumny są wyświetlane, one automatycznie rozmiar dopasowana do ich zawartości. Nagłówki kolumn może mieć określonej wysokości przez ustawienie <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="resizing-with-the-mouse"></a>Zmiana rozmiaru przy użyciu myszy  
 Użytkownicy mogą zmieniać rozmiar <xref:System.Windows.Controls.DataGrid> wierszy i kolumn sekcjami nagłówków wierszy lub kolumn. <xref:System.Windows.Controls.DataGrid> Obsługuje również automatyczną zmianę rozmiaru wierszy i kolumn przez dwukrotne kliknięcie wierszy lub kolumn linię podziału nagłówka. Aby zapobiec zmiana rozmiaru kolumn określonego przez użytkownika, należy ustawić <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> właściwości `false` dla poszczególnych kolumn. Aby uniemożliwić użytkownikom zmienianie rozmiaru wszystkich kolumn, ustaw <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> właściwości `false`. Aby uniemożliwić użytkownikom zmienianie rozmiaru wszystkich wierszy, ustaw <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> właściwości `false`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGridColumn>  
 <xref:System.Windows.Controls.DataGridLength>  
 <xref:System.Windows.Controls.DataGridLengthConverter>
