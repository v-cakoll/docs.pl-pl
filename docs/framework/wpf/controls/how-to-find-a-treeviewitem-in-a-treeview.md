---
title: 'Instrukcje: Znajdowanie elementu TreeViewItem w kontrolce TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219047"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="79786-102">Instrukcje: Znajdowanie elementu TreeViewItem w kontrolce TreeView</span><span class="sxs-lookup"><span data-stu-id="79786-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="79786-103"><xref:System.Windows.Controls.TreeView> Kontrola zapewnia wygodny sposób prezentują dane hierarchiczne.</span><span class="sxs-lookup"><span data-stu-id="79786-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="79786-104">Jeśli Twoje <xref:System.Windows.Controls.TreeView> jest powiązana ze źródłem danych <xref:System.Windows.Controls.TreeView.SelectedItem%2A> właściwość zapewnia wygodny sposób na szybkie pobranie obiektu wybranych danych.</span><span class="sxs-lookup"><span data-stu-id="79786-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="79786-105">Zazwyczaj najlepiej pracować z obiektu źródłowego danych, ale czasami konieczne może być programowe Zmienianie danych zawierające <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="79786-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="79786-106">Na przykład, konieczne może być programowo rozwiń <xref:System.Windows.Controls.TreeViewItem>, lub wybierz inny element w <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="79786-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="79786-107">Aby znaleźć <xref:System.Windows.Controls.TreeViewItem> zawierającą obiekt danych określonego, musi przechodzić przez każdy poziom <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="79786-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="79786-108">Elementy w <xref:System.Windows.Controls.TreeView> można także zwirtualizować poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="79786-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="79786-109">W przypadku których może być zwirtualizowane elementy, możesz również należy weź pod uwagę <xref:System.Windows.Controls.TreeViewItem> do sprawdzenia, czy zawiera on obiektu danych.</span><span class="sxs-lookup"><span data-stu-id="79786-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79786-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="79786-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="79786-111">Opis</span><span class="sxs-lookup"><span data-stu-id="79786-111">Description</span></span>  
 <span data-ttu-id="79786-112">Następujące przykładowe wyszukiwania <xref:System.Windows.Controls.TreeView> dla określonego obiektu i zwraca obiekt zawierający <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="79786-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="79786-113">Przykład zapewnia, że każdy <xref:System.Windows.Controls.TreeViewItem> zostanie uruchomiony, tak aby jego elementy podrzędne, które mogą być wyszukiwane.</span><span class="sxs-lookup"><span data-stu-id="79786-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="79786-114">W tym przykładzie działa także w przypadku <xref:System.Windows.Controls.TreeView> nie używa elementów zwirtualizowanych.</span><span class="sxs-lookup"><span data-stu-id="79786-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79786-115">Poniższy przykład działa w przypadku każdej <xref:System.Windows.Controls.TreeView>, niezależnie od podstawowego modelu danych i wyszukiwań co <xref:System.Windows.Controls.TreeViewItem> aż do znalezienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="79786-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="79786-116">Inna technika, która ma lepszą wydajność jest wyszukiwanie modelu danych dla określonego obiektu, informacje o lokalizacji w hierarchii danych i następnie znajdź odpowiedni <xref:System.Windows.Controls.TreeViewItem> w <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="79786-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="79786-117">Jednak technika, która ma lepszą wydajność wymaga wiedzy na temat modelu danych i nie mogą być uogólnione dla dowolnej podanej <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="79786-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="79786-118">Kod</span><span class="sxs-lookup"><span data-stu-id="79786-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="79786-119">Poprzedni kod, który opiera się na niestandardowej <xref:System.Windows.Controls.VirtualizingStackPanel> który udostępnia metodę o nazwie `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="79786-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="79786-120">Poniższy kod definiuje niestandardową <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="79786-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="79786-121">Następujące XAML przedstawia sposób tworzenia <xref:System.Windows.Controls.TreeView> , który używa niestandardowego <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="79786-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="79786-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79786-122">See also</span></span>

- [<span data-ttu-id="79786-123">Poprawianie wydajności kontrolki TreeView</span><span class="sxs-lookup"><span data-stu-id="79786-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
