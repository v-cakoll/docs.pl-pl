---
title: Jak utworzyć niestandardowy tryb widoku dla ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243222"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="bc58d-102">Jak: Tworzenie niestandardowego trybu widoku dla widoku listview</span><span class="sxs-lookup"><span data-stu-id="bc58d-102">How to: Create a custom view mode for a ListView</span></span>

<span data-ttu-id="bc58d-103">W tym przykładzie pokazano, jak utworzyć tryb niestandardowy <xref:System.Windows.Controls.ListView.View%2A> dla formantu. <xref:System.Windows.Controls.ListView></span><span class="sxs-lookup"><span data-stu-id="bc58d-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc58d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc58d-104">Example</span></span>  
 <span data-ttu-id="bc58d-105">Należy użyć <xref:System.Windows.Controls.ViewBase> klasy podczas tworzenia widoku niestandardowego dla formantu. <xref:System.Windows.Controls.ListView></span><span class="sxs-lookup"><span data-stu-id="bc58d-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="bc58d-106">Poniższy przykład przedstawia tryb `PlainView` widoku o nazwie, <xref:System.Windows.Controls.ViewBase> który pochodzi od klasy.</span><span class="sxs-lookup"><span data-stu-id="bc58d-106">The following example shows a view mode called `PlainView` that's derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="bc58d-107">Aby zastosować styl do widoku niestandardowego, <xref:System.Windows.Style> użyj klasy.</span><span class="sxs-lookup"><span data-stu-id="bc58d-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="bc58d-108">Poniższy przykład definiuje <xref:System.Windows.Style> tryb `PlainView` widoku dla widoku.</span><span class="sxs-lookup"><span data-stu-id="bc58d-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="bc58d-109">W poprzednim przykładzie ten styl jest ustawiany jako wartość właściwości zdefiniowanej <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> dla `PlainView`programu .</span><span class="sxs-lookup"><span data-stu-id="bc58d-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that's defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="bc58d-110">Aby zdefiniować układ danych w trybie <xref:System.Windows.DataTemplate> widoku niestandardowego, należy zdefiniować obiekt.</span><span class="sxs-lookup"><span data-stu-id="bc58d-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="bc58d-111">Poniższy przykład <xref:System.Windows.DataTemplate> definiuje, który może służyć do `PlainView` wyświetlania danych w trybie widoku.</span><span class="sxs-lookup"><span data-stu-id="bc58d-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="bc58d-112">W poniższym <xref:System.Windows.ResourceKey> przykładzie pokazano, `PlainView` jak zdefiniować <xref:System.Windows.DataTemplate> dla trybu widoku, który używa tego, który jest zdefiniowany w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bc58d-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="bc58d-113">Formant <xref:System.Windows.Controls.ListView> może użyć widoku niestandardowego, jeśli ustawisz <xref:System.Windows.Controls.ListView.View%2A> właściwość na klucz zasobu.</span><span class="sxs-lookup"><span data-stu-id="bc58d-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="bc58d-114">W poniższym przykładzie `PlainView` pokazano, jak <xref:System.Windows.Controls.ListView>określić jako tryb widoku dla pliku .</span><span class="sxs-lookup"><span data-stu-id="bc58d-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="bc58d-115">Aby uzyskać pełną próbkę, zobacz [ListView z wieloma widokami (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) lub [ListView z wieloma widokami (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="bc58d-115">For the complete sample, see [ListView with Multiple Views (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc58d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc58d-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="bc58d-117">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="bc58d-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="bc58d-118">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="bc58d-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="bc58d-119">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="bc58d-119">GridView Overview</span></span>](gridview-overview.md)
