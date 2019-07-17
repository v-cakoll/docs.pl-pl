---
title: 'Instrukcje: Wiązanie ze źródłem danych ADO.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 96f846db3f705972a4749460bf2c410483258572
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238426"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="49ebc-102">Instrukcje: Wiązanie ze źródłem danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49ebc-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="49ebc-103">W tym przykładzie pokazano, jak powiązać [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> kontrolki ADO.NET `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="49ebc-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="49ebc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="49ebc-104">Example</span></span>

<span data-ttu-id="49ebc-105">W tym przykładzie `OleDbConnection` obiekt jest używany do łączenia się ze źródłem danych, która jest `Access MDB` pliku, który jest określony w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="49ebc-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="49ebc-106">Po nawiązaniu połączenia `OleDbDataAdapter` obiekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="49ebc-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="49ebc-107">`OleDbDataAdapter` Obiektu wykonuje select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] instrukcję, aby pobrać zestaw rekordów z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49ebc-107">The `OleDbDataAdapter` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="49ebc-108">Wyniki z [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] polecenia są przechowywane w `DataTable` z `DataSet` przez wywołanie metody `Fill` metody `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="49ebc-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="49ebc-109">`DataTable` w tym przykładzie nosi nazwę `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="49ebc-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="49ebc-110">Następnie w przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.ListBox> do `DataSet` obiektu.</span><span class="sxs-lookup"><span data-stu-id="49ebc-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="49ebc-111">Firma Microsoft może następnie powiązać <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> do `BookTable` z `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="49ebc-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="49ebc-112">`BookItemTemplate` jest <xref:System.Windows.DataTemplate> definiuje sposób wyświetlania danych:</span><span class="sxs-lookup"><span data-stu-id="49ebc-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="49ebc-113">`IntColorConverter` Konwertuje `int` na kolor.</span><span class="sxs-lookup"><span data-stu-id="49ebc-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="49ebc-114">Przy użyciu tego konwertera <xref:System.Windows.Controls.TextBlock.Background%2A> kolor trzeciego <xref:System.Windows.Controls.TextBlock> pojawi się jako zielony Jeśli wartość `NumPages` jest mniejsza niż 350 i czerwone.</span><span class="sxs-lookup"><span data-stu-id="49ebc-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="49ebc-115">Implementacja konwerter nie został tutaj pokazany.</span><span class="sxs-lookup"><span data-stu-id="49ebc-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="49ebc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49ebc-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="49ebc-117">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="49ebc-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="49ebc-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="49ebc-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
