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
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697145"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="13fd4-102">Jak powiązać ze źródłem danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="13fd4-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="13fd4-103">Ten przykład pokazuje, jak powiązać formant [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> z ADO.NET `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="13fd4-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="13fd4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="13fd4-104">Example</span></span>

<span data-ttu-id="13fd4-105">W tym przykładzie obiekt `OleDbConnection` jest używany do nawiązywania połączenia ze źródłem danych, który jest plikiem `Access MDB` określonym w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="13fd4-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="13fd4-106">Po nawiązaniu połączenia zostanie utworzony obiekt `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="13fd4-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="13fd4-107">Obiekt `OleDbDataAdapter` wykonuje instrukcję SELECT Structured Query Language (SQL), aby pobrać zestaw rekordów z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="13fd4-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="13fd4-108">Wyniki polecenia SQL są przechowywane w `DataTable` `DataSet` przez wywołanie metody `Fill` `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="13fd4-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="13fd4-109">@No__t-0 w tym przykładzie nosi nazwę `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="13fd4-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="13fd4-110">Następnie przykład ustawia właściwość <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.ListBox> na obiekt `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="13fd4-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="13fd4-111">Następnie można powiązać Właściwość <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> do `BookTable` `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="13fd4-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="13fd4-112">`BookItemTemplate` to <xref:System.Windows.DataTemplate> definiująca sposób wyświetlania danych:</span><span class="sxs-lookup"><span data-stu-id="13fd4-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="13fd4-113">@No__t-0 konwertuje `int` na kolor.</span><span class="sxs-lookup"><span data-stu-id="13fd4-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="13fd4-114">Przy użyciu tego konwertera kolor <xref:System.Windows.Controls.TextBlock.Background%2A> trzeciego <xref:System.Windows.Controls.TextBlock> pojawia się jako zielony, jeśli wartość `NumPages` jest mniejsza niż 350 i czerwona w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="13fd4-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="13fd4-115">Implementacja konwertera nie jest wyświetlana w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="13fd4-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="13fd4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13fd4-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="13fd4-117">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="13fd4-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="13fd4-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="13fd4-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
