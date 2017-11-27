---
title: "Jak powiązać ze źródłem danych ADO.NET"
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
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0eb555bb9f21385d2d0b66fe0dd39112c8350dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Jak powiązać ze źródłem danych ADO.NET
W tym przykładzie pokazano, jak można powiązać [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> formant [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `OleDbConnection` obiektu służy do łączenia się ze źródłem danych, która jest `Access MDB` pliku, który określono w parametrach połączenia. Po nawiązaniu połączenia `OleDbDataAdpater` tworzony jest obiekt. `OleDbDataAdpater` Obiektu wykonuje select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] instrukcji, aby pobrać zestaw rekordów z bazy danych. Wyniki z [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] polecenia są przechowywane w `DataTable` z `DataSet` przez wywołanie metody `Fill` metody `OleDbDataAdapter`. `DataTable` w tym przykładzie nosi nazwę `BookTable`. Następnie w przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.ListBox> do `DataSet` obiektu.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Firma Microsoft może następnie powiązać <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> do `BookTable` z `DataSet`:  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate`jest <xref:System.Windows.DataTemplate> definiuje sposób wyświetlania danych:  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` Konwertuje `int` na kolor. Podczas korzystania z tego konwertera <xref:System.Windows.Controls.TextBlock.Background%2A> kolor trzeci <xref:System.Windows.Controls.TextBlock> zostanie wyświetlony zielony Jeśli wartość `NumPages` jest mniejsza niż 350 i czerwone. Implementacja konwerter nie jest wyświetlane w tym miejscu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
