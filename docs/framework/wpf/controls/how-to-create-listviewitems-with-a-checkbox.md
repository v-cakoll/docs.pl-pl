---
title: 'Instrukcje: Tworzenie kontrolki ListViewItems za pomocą kontrolki CheckBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: b09d5ad11b0961febf524cec1e19cb1e59832e44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083110"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="6e8ea-102">Instrukcje: Tworzenie kontrolki ListViewItems za pomocą kontrolki CheckBox</span><span class="sxs-lookup"><span data-stu-id="6e8ea-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="6e8ea-103">W tym przykładzie przedstawiono sposób wyświetlania kolumny <xref:System.Windows.Controls.CheckBox> kontrolki w <xref:System.Windows.Controls.ListView> formant, który używa <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e8ea-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e8ea-104">Example</span></span>  
 <span data-ttu-id="6e8ea-105">Aby utworzyć kolumnę zawierającą <xref:System.Windows.Controls.CheckBox> kontrolki w <xref:System.Windows.Controls.ListView>, Utwórz <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="6e8ea-106">Następnie ustaw <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> z <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="6e8ea-107">W poniższym przykładzie przedstawiono <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="6e8ea-108">Przykład wiąże <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> właściwość <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> wartość właściwości <xref:System.Windows.Controls.ListViewItem> zawierający go.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="6e8ea-109">W związku z tym, kiedy <xref:System.Windows.Controls.ListViewItem> zawierający <xref:System.Windows.Controls.CheckBox> jest zaznaczone, <xref:System.Windows.Controls.CheckBox> jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="6e8ea-110">Poniższy przykład pokazuje, jak utworzyć kolumnę <xref:System.Windows.Controls.CheckBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="6e8ea-111">Aby utworzyć kolumnę przykład ustawia <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> właściwość <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="6e8ea-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e8ea-112">See also</span></span>

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="6e8ea-113">ListView — Przegląd</span><span class="sxs-lookup"><span data-stu-id="6e8ea-113">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="6e8ea-114">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="6e8ea-114">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="6e8ea-115">GridView — Przegląd</span><span class="sxs-lookup"><span data-stu-id="6e8ea-115">GridView Overview</span></span>](gridview-overview.md)
