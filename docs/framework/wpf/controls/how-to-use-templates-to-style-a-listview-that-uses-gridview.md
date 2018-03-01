---
title: "Jak użyć szablonów do stylu ListView która korzysta z GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9abc19ca14cf512deff898f5f20d23870b8b7847
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="ce650-102">Jak użyć szablonów do stylu ListView która korzysta z GridView</span><span class="sxs-lookup"><span data-stu-id="ce650-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="ce650-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.DataTemplate> i <xref:System.Windows.Style> obiektów, aby określić wygląd <xref:System.Windows.Controls.ListView> formant, który używa <xref:System.Windows.Controls.GridView> trybu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="ce650-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce650-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce650-104">Example</span></span>  
 <span data-ttu-id="ce650-105">W poniższych przykładach pokazano <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> obiektów, które dostosowanie wyglądu nagłówek kolumny dla <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="ce650-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="ce650-106">Poniższy przykład przedstawia użycie tych <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> obiektów, aby ustawić <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> właściwości <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="ce650-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="ce650-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Właściwość definiuje zawartość komórki kolumny.</span><span class="sxs-lookup"><span data-stu-id="ce650-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="ce650-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> są tylko dwóch kilka właściwości, które można dostosować wygląd nagłówka kolumny <xref:System.Windows.Controls.GridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="ce650-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="ce650-109">Aby uzyskać więcej informacji, zobacz [Omówienie szablonów i style nagłówka kolumny w widoku GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce650-109">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="ce650-110">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.DataTemplate> który dostosowuje wygląd komórek w <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="ce650-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="ce650-111">Poniższy przykład przedstawia sposób użycia to <xref:System.Windows.DataTemplate> do definiowania zawartość <xref:System.Windows.Controls.GridViewColumn> komórki.</span><span class="sxs-lookup"><span data-stu-id="ce650-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="ce650-112">Ten szablon jest używany zamiast <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwość, która jest wyświetlana w poprzedniej <xref:System.Windows.Controls.GridViewColumn> przykład.</span><span class="sxs-lookup"><span data-stu-id="ce650-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="ce650-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce650-113">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="ce650-114">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="ce650-114">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="ce650-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ce650-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="ce650-116">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="ce650-116">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
