---
title: "Jak utworzyć niestandardowy tryb widoku dla ListView"
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
helpviewer_keywords: ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c62bcb14f444490991b36dc21eb7676a67007906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="86852-102">Jak utworzyć niestandardowy tryb widoku dla ListView</span><span class="sxs-lookup"><span data-stu-id="86852-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="86852-103">W tym przykładzie przedstawiono sposób tworzenia niestandardowego <xref:System.Windows.Controls.ListView.View%2A> tryb <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="86852-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86852-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="86852-104">Example</span></span>  
 <span data-ttu-id="86852-105">Należy użyć <xref:System.Windows.Controls.ViewBase> klasy utworzenie widoku niestandardowego służącego do <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="86852-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="86852-106">W poniższym przykładzie przedstawiono sposób wyświetlania, które jest wywoływane w `PlainView`, która jest pochodną <xref:System.Windows.Controls.ViewBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="86852-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="86852-107">Aby zastosować styl widok niestandardowy, należy użyć <xref:System.Windows.Style> klasy.</span><span class="sxs-lookup"><span data-stu-id="86852-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="86852-108">W poniższym przykładzie zdefiniowano <xref:System.Windows.Style> dla `PlainView` trybu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="86852-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="86852-109">W poprzednim przykładzie ten styl jest ustawiony jako wartość <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> właściwość, która jest zdefiniowana dla `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="86852-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="86852-110">Aby zdefiniować układ danych w trybie Widok niestandardowy, należy zdefiniować <xref:System.Windows.DataTemplate> obiektu.</span><span class="sxs-lookup"><span data-stu-id="86852-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="86852-111">W poniższym przykładzie zdefiniowano <xref:System.Windows.DataTemplate> można wyświetlić dane w `PlainView` trybu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="86852-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="86852-112">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.ResourceKey> dla `PlainView` trybu wyświetlania, która używa <xref:System.Windows.DataTemplate> zdefiniowanego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="86852-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="86852-113">A <xref:System.Windows.Controls.ListView> kontroli służy widok niestandardowy, jeśli ustawisz <xref:System.Windows.Controls.ListView.View%2A> klucz zasobu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="86852-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="86852-114">Poniższy przykład przedstawia sposób określić `PlainView` jako tryb widoku <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="86852-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="86852-115">Pełny przykład, zobacz [element ListView z wielu widoków próbki](http://go.microsoft.com/fwlink/?LinkID=160013).</span><span class="sxs-lookup"><span data-stu-id="86852-115">For the complete sample, see [ListView with Multiple Views Sample](http://go.microsoft.com/fwlink/?LinkID=160013).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86852-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86852-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="86852-117">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="86852-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="86852-118">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="86852-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="86852-119">Omówienie widoku GridView</span><span class="sxs-lookup"><span data-stu-id="86852-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
