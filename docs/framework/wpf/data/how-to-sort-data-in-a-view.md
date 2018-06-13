---
title: Jak sortować dane w widoku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 5c79261983fcf6200120bcfbf180d155aca3c3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556760"
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="61eb5-102">Jak sortować dane w widoku</span><span class="sxs-lookup"><span data-stu-id="61eb5-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="61eb5-103">W tym przykładzie przedstawiono sposób sortowania danych w widoku.</span><span class="sxs-lookup"><span data-stu-id="61eb5-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61eb5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="61eb5-104">Example</span></span>  
 <span data-ttu-id="61eb5-105">Poniższy przykład tworzy prosty <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="61eb5-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="61eb5-106"><xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obsługi zdarzeń przycisku zawiera logikę do sortowania elementów w <xref:System.Windows.Controls.ListBox> w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="61eb5-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="61eb5-107">Można to zrobić, ponieważ dodawanie elementów do <xref:System.Windows.Controls.ListBox> w ten sposób dodanie ich do <xref:System.Windows.Controls.ItemCollection> z <xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.ItemCollection> pochodną <xref:System.Windows.Data.CollectionView> klasy.</span><span class="sxs-lookup"><span data-stu-id="61eb5-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="61eb5-108">Są wiązane z <xref:System.Windows.Controls.ListBox> do kolekcji przy użyciu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości, tę samą metodę można użyć do sortowania.</span><span class="sxs-lookup"><span data-stu-id="61eb5-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="61eb5-109">Istnieje odwołanie do obiektu widoku używasz tę samą metodę sortowania zawartości z innymi widokami kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61eb5-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="61eb5-110">Na przykład sposobu uzyskiwania widoku zobacz [uzyskać widok domyślny zbierania danych](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="61eb5-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="61eb5-111">Na przykład innego, zobacz [sortowania w widoku GridView kolumny po kliknięciu nagłówka](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="61eb5-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="61eb5-112">Aby uzyskać więcej informacji o widokach, zobacz powiązania do kolekcji w [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="61eb5-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="61eb5-113">Przykład sposobu zastosował logikę sortowania [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], zobacz [sortowania i grupy danych przy użyciu widoku w języku XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="61eb5-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61eb5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61eb5-114">See Also</span></span>  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [<span data-ttu-id="61eb5-115">Sortowanie kolumny GridView po kliknięciu nagłówka</span><span class="sxs-lookup"><span data-stu-id="61eb5-115">Sort a GridView Column When a Header Is Clicked</span></span>](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [<span data-ttu-id="61eb5-116">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="61eb5-116">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="61eb5-117">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="61eb5-117">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="61eb5-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="61eb5-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
