---
title: "Jak znaleźć TreeViewItem w TreeView"
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
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 696a9e2d92b9c44e4aedbcc200b41e5548cd7411
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="539f5-102">Jak znaleźć TreeViewItem w TreeView</span><span class="sxs-lookup"><span data-stu-id="539f5-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="539f5-103"><xref:System.Windows.Controls.TreeView> Kontrola zapewnia wygodny sposób wyświetlania danych hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="539f5-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="539f5-104">Jeśli Twoje <xref:System.Windows.Controls.TreeView> jest powiązany ze źródłem danych <xref:System.Windows.Controls.TreeView.SelectedItem%2A> właściwość umożliwia dogodny można szybko pobrać obiektu wybranych danych.</span><span class="sxs-lookup"><span data-stu-id="539f5-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="539f5-105">Zazwyczaj najlepiej pracować z źródłowy obiekt danych, ale niekiedy konieczne może być programowane manipulowania zawierające dane <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="539f5-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="539f5-106">Na przykład konieczne może być programowane rozwiń <xref:System.Windows.Controls.TreeViewItem>, lub wybierz inny element w <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="539f5-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="539f5-107">Aby znaleźć <xref:System.Windows.Controls.TreeViewItem> zawiera obiekt określonych danych, musi przechodzić przez każdy poziom <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="539f5-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="539f5-108">Elementy w <xref:System.Windows.Controls.TreeView> można także zwirtualizować w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="539f5-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="539f5-109">W przypadku których może zwirtualizowane elementy, można również musi zrealizować <xref:System.Windows.Controls.TreeViewItem> do sprawdzenia, czy zawiera on obiektu danych.</span><span class="sxs-lookup"><span data-stu-id="539f5-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="539f5-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="539f5-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="539f5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="539f5-111">Description</span></span>  
 <span data-ttu-id="539f5-112">Następujące przykładowe wyszukiwania <xref:System.Windows.Controls.TreeView> dla określonego obiektu i zwraca obiekt zawierający <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="539f5-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="539f5-113">Przykład gwarantuje, że każdy <xref:System.Windows.Controls.TreeViewItem> zostanie uruchomiony, dzięki czemu można przeszukiwać jej elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="539f5-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="539f5-114">W tym przykładzie działa również wtedy, gdy <xref:System.Windows.Controls.TreeView> nie używa elementów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="539f5-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="539f5-115">Poniższy przykład działa dla każdego <xref:System.Windows.Controls.TreeView>, niezależnie od tego, czy odpowiedni model danych i wyszukiwań co <xref:System.Windows.Controls.TreeViewItem> aż do znalezienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="539f5-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="539f5-116">Innej metody, która ma większą wydajność jest wyszukiwanie modelu danych dla określonego obiektu, informacje o lokalizacji w hierarchii danych, a następnie znajdź odpowiadającego <xref:System.Windows.Controls.TreeViewItem> w <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="539f5-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="539f5-117">Jednak tę metodę, która ma większą wydajność wymaga znajomości modelu danych i nie można uogólnić dla żadnej podanej <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="539f5-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="539f5-118">Kod</span><span class="sxs-lookup"><span data-stu-id="539f5-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="539f5-119">Poprzedni kod zależy od niestandardowego <xref:System.Windows.Controls.VirtualizingStackPanel> która udostępnia metodę o nazwie `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="539f5-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="539f5-120">Poniższy kod definiuje niestandardowe <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="539f5-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="539f5-121">Następujące XAML przedstawiono sposób tworzenia <xref:System.Windows.Controls.TreeView> używającej niestandardowego <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="539f5-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="539f5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="539f5-122">See Also</span></span>  
 [<span data-ttu-id="539f5-123">Poprawianie wydajności kontrolki TreeView</span><span class="sxs-lookup"><span data-stu-id="539f5-123">Improve the Performance of a TreeView</span></span>](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
