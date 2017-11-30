---
title: "Jak dodać szczegóły wiersza do formantu DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 036e06d110df8900ab46f0d501f30b4a163c8eb9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Jak dodać szczegóły wiersza do formantu DataGrid
Korzystając z <xref:System.Windows.Controls.DataGrid> kontroli, prezentacji danych można dostosować, dodając sekcji Szczegóły wiersza. Dodawanie sekcji Szczegóły wiersza umożliwiają grupowanie niektóre dane w szablonie, który jest opcjonalnie widoczny czy zwinięty. Na przykład można dodać szczegółów wiersza do <xref:System.Windows.Controls.DataGrid> przedstawiający tylko podsumowanie danych dla każdego wiersza w <xref:System.Windows.Controls.DataGrid>, ale stanowi więcej pól danych, gdy użytkownik wybierze wiersza. Zdefiniuj szablon dla sekcji Szczegóły wiersza <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości. Na poniższej ilustracji przedstawiono przykład sekcji szczegółów wiersza.  
  
 ![DataGrid przedstawiono szczegóły wiersza](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Należy zdefiniować szablon szczegóły wiersza jako albo wbudowany plik XAML lub zasobu. Obu metod przedstawiono w poniższych procedurach. Szablon danych, który zostanie dodany jako zasób mogą być używane w całej projektu bez konieczności ponownego tworzenia szablonu. Szablon danych, która zostanie dodana jako wbudowany XAML jest dostępny tylko w formancie których jest zdefiniowana.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Aby wyświetlić szczegóły wiersza przy użyciu wbudowany plik XAML  
  
1.  Utwórz <xref:System.Windows.Controls.DataGrid> wyświetlający dane ze źródła danych.  
  
2.  W <xref:System.Windows.Controls.DataGrid> elementu, Dodaj <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.  
  
3.  Utwórz <xref:System.Windows.DataTemplate> która definiuje wygląd elementów w sekcji szczegółów wiersza.  
  
     Poniżej przedstawiono XAML <xref:System.Windows.Controls.DataGrid> oraz sposób definiowania <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> wbudowanego. <xref:System.Windows.Controls.DataGrid> Wyświetla trzy wartości w każdym wierszu i trzy więcej wartości po zaznaczeniu wiersza.  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Poniższy kod przedstawia zapytanie, które służy do wybierania danych, która jest wyświetlana w <xref:System.Windows.Controls.DataGrid>. W tym przykładzie zapytanie wybiera danych z jednostki, która zawiera informacje o kliencie.  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Aby wyświetlić szczegóły wiersza przy użyciu zasobu  
  
1.  Utwórz <xref:System.Windows.Controls.DataGrid> wyświetlający dane ze źródła danych.  
  
2.  Dodaj <xref:System.Windows.FrameworkElement.Resources%2A> elementu do elementu głównego takich jak <xref:System.Windows.Window> kontroli lub <xref:System.Windows.Controls.Page> kontrolować lub Dodaj <xref:System.Windows.Application.Resources%2A> elementu <xref:System.Windows.Application> klasy w pliku App.xaml (lub Application.xaml).  
  
3.  W elemencie zasobów należy utworzyć <xref:System.Windows.DataTemplate> która definiuje wygląd elementów w sekcji szczegółów wiersza.  
  
     Poniżej przedstawiono XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> zdefiniowane w <xref:System.Windows.Application> klasy.  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  Na <xref:System.Windows.DataTemplate>ustaw [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) wartości, który unikatowo identyfikuje szablonu danych.  
  
5.  W <xref:System.Windows.Controls.DataGrid> , ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości zasobów określone w poprzednich krokach. Przypisz zasobu jako zasób statycznych.  
  
     Poniżej przedstawiono XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwość zasobu z poprzedniego przykładu.  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Aby ustawić widoczność i zapobiec przewijanie w poziomie dla szczegółów wiersza  
  
1.  W razie potrzeby ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> właściwości <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> wartość.  
  
     Domyślnie ta wartość jest równa <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Można ją ustawić <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> celu pokazania szczegółów dla wszystkich wierszy lub <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> Aby ukryć szczegóły dla wszystkich wierszy.  
  
2.  W razie potrzeby ustaw <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> właściwości `true` zapobiegające wiersza szczegółów sekcji przewijanie w poziomie.
