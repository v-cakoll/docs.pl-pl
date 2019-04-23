---
title: 'Instrukcje: Tworzenie niestandardowego trybu widoku dla kontrolki ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: de11250a2e7529fba3b262e42b6714262738fa90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092893"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="1f7f7-102">Instrukcje: Tworzenie niestandardowego trybu widoku dla kontrolki ListView</span><span class="sxs-lookup"><span data-stu-id="1f7f7-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="1f7f7-103">W tym przykładzie pokazano, jak utworzyć niestandardową <xref:System.Windows.Controls.ListView.View%2A> tryb <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f7f7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f7f7-104">Example</span></span>  
 <span data-ttu-id="1f7f7-105">Należy użyć <xref:System.Windows.Controls.ViewBase> klasy po utworzeniu widok niestandardowy <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="1f7f7-106">W poniższym przykładzie przedstawiono sposób wyświetlania, która jest wywoływana `PlainView`, który pochodzi od <xref:System.Windows.Controls.ViewBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="1f7f7-107">Aby zastosować styl do widoku niestandardowego, należy użyć <xref:System.Windows.Style> klasy.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="1f7f7-108">W poniższym przykładzie zdefiniowano <xref:System.Windows.Style> dla `PlainView` trybu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="1f7f7-109">W poprzednim przykładzie ten styl jest ustawiona jako wartość <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> właściwość, która jest zdefiniowana dla `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="1f7f7-110">Aby zdefiniować układ danych w trybie widoku niestandardowego, należy zdefiniować <xref:System.Windows.DataTemplate> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="1f7f7-111">W poniższym przykładzie zdefiniowano <xref:System.Windows.DataTemplate> można wyświetlić dane w `PlainView` trybu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="1f7f7-112">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.ResourceKey> dla `PlainView` tryb widoku, który używa <xref:System.Windows.DataTemplate> zdefiniowanego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="1f7f7-113">A <xref:System.Windows.Controls.ListView> kontroli można użyć widoku niestandardowego, jeśli ustawisz <xref:System.Windows.Controls.ListView.View%2A> właściwości klucza zasobu.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="1f7f7-114">Poniższy przykład pokazuje, jak określić `PlainView` jako tryb widoku dla <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="1f7f7-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="1f7f7-115">Aby uzyskać pełny przykład, zobacz [ListView przy użyciu wielu widoków (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) lub [ListView przy użyciu wielu Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="1f7f7-115">For the complete sample, see [ListView with Multiple Views(C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f7f7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f7f7-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="1f7f7-117">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1f7f7-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="1f7f7-118">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="1f7f7-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="1f7f7-119">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="1f7f7-119">GridView Overview</span></span>](gridview-overview.md)
