---
title: 'Instrukcje: dodawanie szczegółów wiersza do kontrolki DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768647"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Instrukcje: dodawanie szczegółów wiersza do kontrolki DataGrid
Korzystając z <xref:System.Windows.Controls.DataGrid> kontrolki, prezentacji danych można dostosować, dodając sekcji Szczegóły wiersza. Dodawanie sekcji Szczegóły wiersza umożliwiają grupowanie niektóre dane w szablonie, który jest opcjonalnie widoczny czy zwinięty. Na przykład można dodać szczegóły wiersza do <xref:System.Windows.Controls.DataGrid> przedstawiające tylko podsumowanie danych dla każdego wiersza w <xref:System.Windows.Controls.DataGrid>, ale zabezpieczeniem więcej pól danych, gdy użytkownik wybierze wiersz. Zdefiniuj szablon dla sekcji Szczegóły wiersza w <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości. Na poniższej ilustracji przedstawiono przykład sekcji szczegółów wiersza.  
  
 ![DataGrid, przedstawiono szczegóły wiersza](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Należy zdefiniować szablon szczegóły wiersza, jako jako wbudowane XAML lub zasobu. Oba podejścia są wyświetlane w poniższych procedurach. Szablon danych, który jest dodawany jako zasób może służyć w całym projekcie, bez potrzeby ponownego tworzenia szablonu. Szablon danych, który jest dodawany jako wbudowane XAML jest dostępny tylko z formantu którym jest zdefiniowana.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Aby wyświetlić szczegóły wiersza przy użyciu wbudowanego XAML  
  
1. Utwórz <xref:System.Windows.Controls.DataGrid> wyświetlającą dane ze źródła danych.  
  
2. W <xref:System.Windows.Controls.DataGrid> elementu Dodawanie <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.  
  
3. Utwórz <xref:System.Windows.DataTemplate> która definiuje wygląd elementów w sekcji szczegółów wiersza.  
  
     Pokazano w poniższym XAML <xref:System.Windows.Controls.DataGrid> oraz sposób definiowania <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> wbudowanego. <xref:System.Windows.Controls.DataGrid> Wyświetla trzy wartości w każdym wierszu i trzy więcej wartości po zaznaczeniu wiersza.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Poniższy kod przedstawia zapytanie, które służy do wybierania danych, która jest wyświetlana w <xref:System.Windows.Controls.DataGrid>. W tym przykładzie zapytanie wybiera dane z jednostki zawierającej informacje o kliencie.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Aby wyświetlić szczegóły wiersza przy użyciu zasobów  
  
1. Utwórz <xref:System.Windows.Controls.DataGrid> wyświetlającą dane ze źródła danych.  
  
2. Dodaj <xref:System.Windows.FrameworkElement.Resources%2A> element do elementu głównego takich jak <xref:System.Windows.Window> kontroli lub <xref:System.Windows.Controls.Page> kontrolować lub dodać <xref:System.Windows.Application.Resources%2A> elementu <xref:System.Windows.Application> klasy w pliku App.xaml (lub Application.xaml).  
  
3. W elemencie resources Utwórz <xref:System.Windows.DataTemplate> która definiuje wygląd elementów w sekcji szczegółów wiersza.  
  
     Pokazano w poniższym XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> zdefiniowane w <xref:System.Windows.Application> klasy.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. Na <xref:System.Windows.DataTemplate>ustaw [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) wartość, która jednoznacznie identyfikuje szablon danych.  
  
5. W <xref:System.Windows.Controls.DataGrid> elementu, ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości zasobu, zdefiniowane w poprzednich krokach. Przypisuje zasób jako zasób statyczny.  
  
     Pokazano w poniższym XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwością do zasobu z poprzedniego przykładu.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Aby ustawić widoczność i zapobiec przewijanie w poziomie dla szczegółów wiersza  
  
1. Jeśli to konieczne, ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> właściwości <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> wartość.  
  
     Domyślnie ta wartość jest równa <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Możesz ustawić na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> Aby wyświetlić szczegółowe informacje dla wszystkich wierszy lub <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> na razie ukryć szczegóły we wszystkich wierszach.  
  
2. Jeśli to konieczne, ustaw <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> właściwość `true` zapobiegające wiersza szczegółów sekcji przewijanie w poziomie.
