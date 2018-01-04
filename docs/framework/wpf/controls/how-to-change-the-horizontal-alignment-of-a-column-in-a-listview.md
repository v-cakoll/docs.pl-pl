---
title: "Jak zmienić wyrównanie w poziomie kolumny w ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a465ae44d3b8a4c43e5e34eaeedcd739d328bff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a><span data-ttu-id="e59bc-102">Jak zmienić wyrównanie w poziomie kolumny w ListView</span><span class="sxs-lookup"><span data-stu-id="e59bc-102">How to: Change the Horizontal Alignment of a Column in a ListView</span></span>
<span data-ttu-id="e59bc-103">Domyślnie, zawartości każdej kolumny w <xref:System.Windows.Controls.ListViewItem> jest wyrównany.</span><span class="sxs-lookup"><span data-stu-id="e59bc-103">By default, the content of each column in a <xref:System.Windows.Controls.ListViewItem> is left-aligned.</span></span> <span data-ttu-id="e59bc-104">Wyrównanie każdej kolumny można zmienić, zapewniając <xref:System.Windows.DataTemplate> i ustawienie <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości w elemencie <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="e59bc-104">You can change the alignment of each column by providing a <xref:System.Windows.DataTemplate> and setting the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property on the element within the <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="e59bc-105">W tym temacie przedstawiono sposób <xref:System.Windows.Controls.ListView> Wyrównuje zawartość domyślnie i jak zmienić wyrównania jednej kolumny w <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="e59bc-105">This topic shows how a <xref:System.Windows.Controls.ListView> aligns its content by default and how to change the alignment of one column in a <xref:System.Windows.Controls.ListView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e59bc-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e59bc-106">Example</span></span>  
 <span data-ttu-id="e59bc-107">W poniższym przykładzie danych w `Title` i `ISBN` kolumn jest wyrównany.</span><span class="sxs-lookup"><span data-stu-id="e59bc-107">In the following example, the data in the `Title` and `ISBN` columns is left-aligned.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="e59bc-108">Aby zmienić wyrównania `ISBN` kolumny, należy określić, że <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwości każdego <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.HorizontalAlignment.Stretch>, tak aby elementy w każdym <xref:System.Windows.Controls.ListViewItem> może obejmować lub ją wzdłuż całego szerokość każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="e59bc-108">To change the alignment of the `ISBN` column, you need to specify that the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> property of each <xref:System.Windows.Controls.ListViewItem> is <xref:System.Windows.HorizontalAlignment.Stretch>, so that the elements in each <xref:System.Windows.Controls.ListViewItem> can span or be positioned along the entire width of each column.</span></span> <span data-ttu-id="e59bc-109">Ponieważ <xref:System.Windows.Controls.ListView> jest powiązany ze źródłem danych, należy utworzyć styl, który ustawia <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="e59bc-109">Because the <xref:System.Windows.Controls.ListView> is bound to a data source, you need to create a style that sets the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>.</span></span> <span data-ttu-id="e59bc-110">Następnie należy użyć <xref:System.Windows.DataTemplate> do wyświetlania zawartości zamiast <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e59bc-110">Next, you need to use a <xref:System.Windows.DataTemplate> to display the content instead of using the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property.</span></span> <span data-ttu-id="e59bc-111">Aby wyświetlić `ISBN` każdego szablonu <xref:System.Windows.DataTemplate> może zawierać tylko <xref:System.Windows.Controls.TextBlock> mający jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ustawioną właściwość <xref:System.Windows.HorizontalAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="e59bc-111">To display the `ISBN` of each template, the <xref:System.Windows.DataTemplate> can just contain a <xref:System.Windows.Controls.TextBlock> that has its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property set to <xref:System.Windows.HorizontalAlignment.Right>.</span></span>  
  
 <span data-ttu-id="e59bc-112">W poniższym przykładzie zdefiniowano styl i <xref:System.Windows.DataTemplate> dokonanie `ISBN` kolumny wyrównany do prawej, a zmiany <xref:System.Windows.Controls.GridViewColumn> do odwołania <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="e59bc-112">The following example defines the style and <xref:System.Windows.DataTemplate> necessary to make the `ISBN` column right-aligned, and changes the <xref:System.Windows.Controls.GridViewColumn> to reference the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e59bc-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e59bc-113">See Also</span></span>  
 [<span data-ttu-id="e59bc-114">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="e59bc-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="e59bc-115">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="e59bc-115">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="e59bc-116">Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath</span><span class="sxs-lookup"><span data-stu-id="e59bc-116">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="e59bc-117">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="e59bc-117">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
