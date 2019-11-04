---
title: Jak powiązać ze źródłem danych ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 0b3d7147f45bee5e8abd95bdc51c5f5f695cf830
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458408"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Jak powiązać ze źródłem danych ADO.NET

Ten przykład pokazuje, jak powiązać formant [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> z `DataSet`em ADO.NET.

## <a name="example"></a>Przykład

W tym przykładzie obiekt `OleDbConnection` jest używany do nawiązywania połączenia ze źródłem danych, który jest plikiem `Access MDB` określonym w parametrach połączenia. Po nawiązaniu połączenia zostanie utworzony obiekt `OleDbDataAdapter`. Obiekt `OleDbDataAdapter` wykonuje instrukcję SELECT Structured Query Language (SQL), aby pobrać zestaw rekordów z bazy danych. Wyniki polecenia SQL są przechowywane w `DataTable` `DataSet` przez wywołanie metody `Fill` `OleDbDataAdapter`. `DataTable` w tym przykładzie nosi nazwę `BookTable`. Następnie przykład ustawia właściwość <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.ListBox> do obiektu `DataSet`.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Następnie możemy powiązać <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość <xref:System.Windows.Controls.ListBox> z `BookTable` `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` jest <xref:System.Windows.DataTemplate>, który definiuje sposób wyświetlania danych:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` konwertuje `int` na kolor. Przy użyciu tego konwertera kolor <xref:System.Windows.Controls.TextBlock.Background%2A> trzeciego <xref:System.Windows.Controls.TextBlock> pojawia się jako zielony, jeśli wartość `NumPages` jest mniejsza niż 350 i czerwona w przeciwnym razie. Implementacja konwertera nie jest wyświetlana w tym miejscu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.BindingListCollectionView>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
