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
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454825"
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="5c813-102">Jak sortować dane w widoku</span><span class="sxs-lookup"><span data-stu-id="5c813-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="5c813-103">W tym przykładzie opisano sposób sortowania danych w widoku.</span><span class="sxs-lookup"><span data-stu-id="5c813-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c813-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c813-104">Example</span></span>  
 <span data-ttu-id="5c813-105">Poniższy przykład tworzy proste <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="5c813-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="5c813-106">Procedura obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click> przycisku zawiera logikę do sortowania elementów w <xref:System.Windows.Controls.ListBox> w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="5c813-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="5c813-107">Można to zrobić, ponieważ dodawanie elementów do <xref:System.Windows.Controls.ListBox> w ten sposób dodaje je do <xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.ItemCollection> pochodzi od klasy <xref:System.Windows.Data.CollectionView>.</span><span class="sxs-lookup"><span data-stu-id="5c813-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="5c813-108">Jeśli powiążesz <xref:System.Windows.Controls.ListBox> z kolekcją przy użyciu właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, możesz użyć tej samej techniki do sortowania.</span><span class="sxs-lookup"><span data-stu-id="5c813-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="5c813-109">Tak długo, jak masz odwołanie do obiektu widoku, możesz użyć tej samej techniki, aby posortować zawartość innych widoków kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5c813-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="5c813-110">Aby zapoznać się z przykładem, jak uzyskać widok, zobacz temat [pobieranie widoku domyślnego kolekcji danych](how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="5c813-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="5c813-111">Aby uzyskać inny przykład, zobacz [Sortowanie kolumny GridView po kliknięciu nagłówka](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="5c813-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="5c813-112">Aby uzyskać więcej informacji o widokach, zobacz powiązanie z kolekcjami w temacie [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5c813-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="5c813-113">Aby zapoznać się z przykładem zastosowania logiki sortowania w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], zobacz [Sortowanie i grupowanie danych przy użyciu widoku w języku XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5c813-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c813-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c813-114">See also</span></span>

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [<span data-ttu-id="5c813-115">Sortowanie kolumny GridView po kliknięciu nagłówka</span><span class="sxs-lookup"><span data-stu-id="5c813-115">Sort a GridView Column When a Header Is Clicked</span></span>](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [<span data-ttu-id="5c813-116">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="5c813-116">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5c813-117">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="5c813-117">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="5c813-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="5c813-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
