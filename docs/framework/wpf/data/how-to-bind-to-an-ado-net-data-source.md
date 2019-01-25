---
title: 'Instrukcje: Powiąż ze źródłem danych ADO.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 774262b33ceda3e8881fb92bcbc70a3dd5361f39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746651"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Instrukcje: Powiąż ze źródłem danych ADO.NET
W tym przykładzie pokazano, jak powiązać [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> kontrolę [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `OleDbConnection` obiekt jest używany do łączenia się ze źródłem danych, która jest `Access MDB` pliku, który jest określony w parametrach połączenia. Po nawiązaniu połączenia `OleDbDataAdpater` obiekt zostanie utworzony. `OleDbDataAdpater` Obiektu wykonuje select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] instrukcję, aby pobrać zestaw rekordów z bazy danych. Wyniki z [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] polecenia są przechowywane w `DataTable` z `DataSet` przez wywołanie metody `Fill` metody `OleDbDataAdapter`. `DataTable` w tym przykładzie nosi nazwę `BookTable`. Następnie w przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.ListBox> do `DataSet` obiektu.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Firma Microsoft może następnie powiązać <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> do `BookTable` z `DataSet`:  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate` jest <xref:System.Windows.DataTemplate> definiuje sposób wyświetlania danych:  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` Konwertuje `int` na kolor. Przy użyciu tego konwertera <xref:System.Windows.Controls.TextBlock.Background%2A> kolor trzeciego <xref:System.Windows.Controls.TextBlock> pojawi się jako zielony Jeśli wartość `NumPages` jest mniejsza niż 350 i czerwone. Implementacja konwerter nie został tutaj pokazany.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Data.BindingListCollectionView>
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
