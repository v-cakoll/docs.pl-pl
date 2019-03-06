---
title: 'Instrukcje: Użyj szablonów do stylu ListView która korzysta z GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: baef8bdee73d8493ba406f5eef1e3e3676680704
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355769"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="886ba-102">Instrukcje: Użyj szablonów do stylu ListView która korzysta z GridView</span><span class="sxs-lookup"><span data-stu-id="886ba-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="886ba-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.DataTemplate> i <xref:System.Windows.Style> obiektów, aby określić wygląd <xref:System.Windows.Controls.ListView> formant, który używa <xref:System.Windows.Controls.GridView> trybu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="886ba-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="886ba-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="886ba-104">Example</span></span>  
 <span data-ttu-id="886ba-105">W poniższych przykładach pokazano <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> obiekty, które dostosować wygląd nagłówek kolumny dla <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="886ba-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="886ba-106">Poniższy przykład pokazuje, jak używać tych <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> obiektów, aby ustawić <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> właściwości <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="886ba-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="886ba-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Właściwość definiuje zawartości komórek w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="886ba-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="886ba-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> są tylko dwa spośród wielu właściwości, które umożliwia dostosowywanie wyglądu nagłówek kolumny dla <xref:System.Windows.Controls.GridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="886ba-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="886ba-109">Aby uzyskać więcej informacji, zobacz [omówienie szablony i style nagłówków kolumn GridView](gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="886ba-109">For more information, see [GridView Column Header Styles and Templates Overview](gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="886ba-110">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.DataTemplate> który dostosowuje wyglądu komórek w <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="886ba-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="886ba-111">Poniższy przykład pokazuje, jak użyć tej funkcji <xref:System.Windows.DataTemplate> do definiowania zawartości <xref:System.Windows.Controls.GridViewColumn> komórki.</span><span class="sxs-lookup"><span data-stu-id="886ba-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="886ba-112">Ten szablon jest używany zamiast <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwość, która jest wyświetlana w ciągu poprzednich <xref:System.Windows.Controls.GridViewColumn> przykład.</span><span class="sxs-lookup"><span data-stu-id="886ba-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="886ba-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="886ba-113">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="886ba-114">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="886ba-114">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="886ba-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="886ba-115">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="886ba-116">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="886ba-116">ListView Overview</span></span>](listview-overview.md)
