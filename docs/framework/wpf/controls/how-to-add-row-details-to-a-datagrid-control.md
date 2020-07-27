---
title: 'Instrukcje: dodawanie szczegółów wiersza do kontrolki DataGrid'
description: Dowiedz się, jak dostosować prezentację danych przy użyciu kontrolki DataGrid Windows Presentation Foundation, dodając sekcję Szczegóły wiersza.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164950"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Instrukcje: dodawanie szczegółów wiersza do kontrolki DataGrid
Korzystając z <xref:System.Windows.Controls.DataGrid> kontrolki, można dostosować prezentację danych, dodając sekcję Szczegóły wiersza. Dodanie sekcji Szczegóły wiersza umożliwia grupowanie niektórych danych w szablonie, który jest opcjonalnie widoczny lub zwinięty. Na przykład można dodać Szczegóły wierszy do obiektu, <xref:System.Windows.Controls.DataGrid> który przedstawia tylko podsumowanie danych dla każdego wiersza w <xref:System.Windows.Controls.DataGrid> , ale wyświetla więcej pól danych, gdy użytkownik wybierze wiersz. Zdefiniuj szablon dla sekcji Szczegóły wiersza w <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości. Na poniższej ilustracji przedstawiono przykład sekcji Szczegóły wiersza.  
  
 ![Siatka danych wyświetlana z szczegółami wiersza](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Szablon Szczegóły wiersza definiuje się jako wbudowany kod XAML lub jako zasób. Oba podejścia przedstawiono w poniższych procedurach. Szablon danych, który jest dodawany jako zasób, może być używany w całym projekcie bez ponownego tworzenia szablonu. Szablon danych, który jest dodawany jako wbudowany kod XAML jest dostępny tylko z kontrolki, w której jest zdefiniowany.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Aby wyświetlić szczegóły wiersza przy użyciu wbudowanego języka XAML  
  
1. Utwórz <xref:System.Windows.Controls.DataGrid> , który wyświetla dane ze źródła danych.  
  
2. W <xref:System.Windows.Controls.DataGrid> elemencie Dodaj <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.  
  
3. Utwórz <xref:System.Windows.DataTemplate> , który definiuje wygląd sekcji Szczegóły wiersza.  
  
     Poniższy kod XAML przedstawia <xref:System.Windows.Controls.DataGrid> i sposób definiowania <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> wbudowanej metody. <xref:System.Windows.Controls.DataGrid>Po wybraniu wiersza wyświetlane są trzy wartości w każdym wierszu i trzy więcej wartości.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Poniższy kod przedstawia zapytanie, które jest używane do wybierania danych, które są wyświetlane w <xref:System.Windows.Controls.DataGrid> . W tym przykładzie zapytanie wybiera dane z jednostki, która zawiera informacje o kliencie.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Aby wyświetlić szczegóły wiersza za pomocą zasobu  
  
1. Utwórz <xref:System.Windows.Controls.DataGrid> , który wyświetla dane ze źródła danych.  
  
2. Dodaj <xref:System.Windows.FrameworkElement.Resources%2A> element do elementu głównego, takiego jak <xref:System.Windows.Window> kontrolka lub <xref:System.Windows.Controls.Page> kontrolka, lub Dodaj <xref:System.Windows.Application.Resources%2A> element do <xref:System.Windows.Application> klasy w pliku App. XAML (lub Application. XAML).  
  
3. W elemencie Resources Utwórz, <xref:System.Windows.DataTemplate> który definiuje wygląd sekcji Szczegóły wiersza.  
  
     Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> zdefiniowane w <xref:System.Windows.Application> klasie.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. W <xref:System.Windows.DataTemplate> , ustaw dla [dyrektywy x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) wartość, która jednoznacznie identyfikuje szablon danych.  
  
5. W <xref:System.Windows.Controls.DataGrid> elemencie Ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> Właściwość na zasób zdefiniowany w poprzednich krokach. Przypisz zasób jako zasób statyczny.  
  
     Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> Właściwość ustawioną dla zasobu z poprzedniego przykładu.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Aby ustawić widoczność i uniemożliwić przewijanie w poziomie dla szczegółów wiersza  
  
1. W razie potrzeby ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> Właściwość na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> wartość.  
  
     Domyślnie wartość jest równa <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> . Można ustawić, aby <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> wyświetlić szczegóły wszystkich wierszy lub <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> ukryć szczegóły dla wszystkich wierszy.  
  
2. W razie potrzeby ustaw <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> Właściwość na, `true` Aby zapobiec przewijaniu sekcji Szczegóły wiersza w poziomie.
