---
title: Jak dodać szczegóły wiersza do formantu DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559680"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Jak dodać szczegóły wiersza do formantu DataGrid
Korzystając z formantu <xref:System.Windows.Controls.DataGrid>, można dostosować prezentację danych, dodając sekcję Szczegóły wiersza. Dodanie sekcji Szczegóły wiersza umożliwia grupowanie niektórych danych w szablonie, który jest opcjonalnie widoczny lub zwinięty. Na przykład można dodać Szczegóły wierszy do <xref:System.Windows.Controls.DataGrid>, które przedstawia tylko podsumowanie danych dla każdego wiersza w <xref:System.Windows.Controls.DataGrid>, ale wyświetla więcej pól danych, gdy użytkownik zaznaczy wiersz. Szablon sekcji Szczegóły wiersza można zdefiniować we właściwości <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>. Na poniższej ilustracji przedstawiono przykład sekcji Szczegóły wiersza.  
  
 ![Siatka danych wyświetlana z szczegółami wiersza](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Szablon Szczegóły wiersza definiuje się jako wbudowany kod XAML lub jako zasób. Oba podejścia przedstawiono w poniższych procedurach. Szablon danych, który jest dodawany jako zasób, może być używany w całym projekcie bez ponownego tworzenia szablonu. Szablon danych, który jest dodawany jako wbudowany kod XAML jest dostępny tylko z kontrolki, w której jest zdefiniowany.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Aby wyświetlić szczegóły wiersza przy użyciu wbudowanego języka XAML  
  
1. Utwórz <xref:System.Windows.Controls.DataGrid>, który wyświetla dane ze źródła danych.  
  
2. W <xref:System.Windows.Controls.DataGrid> elementu Dodawanie <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.  
  
3. Utwórz <xref:System.Windows.DataTemplate>, który definiuje wygląd sekcji Szczegóły wiersza.  
  
     Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid> i sposób definiowania <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> wbudowane. <xref:System.Windows.Controls.DataGrid> wyświetla trzy wartości w każdym wierszu i trzy więcej wartości po zaznaczeniu wiersza.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Poniższy kod przedstawia zapytanie, które jest używane do wybierania danych, które są wyświetlane w <xref:System.Windows.Controls.DataGrid>. W tym przykładzie zapytanie wybiera dane z jednostki, która zawiera informacje o kliencie.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Aby wyświetlić szczegóły wiersza za pomocą zasobu  
  
1. Utwórz <xref:System.Windows.Controls.DataGrid>, który wyświetla dane ze źródła danych.  
  
2. Dodaj element <xref:System.Windows.FrameworkElement.Resources%2A> do elementu głównego, takiego jak kontrolka <xref:System.Windows.Window> lub kontrolka <xref:System.Windows.Controls.Page> lub Dodaj element <xref:System.Windows.Application.Resources%2A> do klasy <xref:System.Windows.Application> w pliku App. XAML (lub Application. XAML).  
  
3. W elemencie Resources Utwórz <xref:System.Windows.DataTemplate>, który definiuje wygląd sekcji Szczegóły wiersza.  
  
     Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> zdefiniowane w klasie <xref:System.Windows.Application>.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. Na <xref:System.Windows.DataTemplate>Ustaw dla [dyrektywy x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) wartość, która jednoznacznie identyfikuje szablon danych.  
  
5. W elemencie <xref:System.Windows.Controls.DataGrid> ustaw właściwość <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> na zasób zdefiniowany w poprzednich krokach. Przypisz zasób jako zasób statyczny.  
  
     Poniższy kod XAML przedstawia Właściwość <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> ustawioną na zasób z poprzedniego przykładu.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Aby ustawić widoczność i uniemożliwić przewijanie w poziomie dla szczegółów wiersza  
  
1. W razie potrzeby ustaw właściwość <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> na wartość <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>.  
  
     Domyślnie wartość jest ustawiona na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Można ustawić <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>, aby wyświetlić szczegóły dla wszystkich wierszy lub <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>, aby ukryć szczegóły dla wszystkich wierszy.  
  
2. W razie potrzeby ustaw właściwość <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> na `true`, aby zapobiec przewijaniu sekcji Szczegóły wiersza w poziomie.
