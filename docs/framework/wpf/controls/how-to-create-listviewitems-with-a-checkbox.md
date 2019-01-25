---
title: 'Instrukcje: Utwórz ListViewItems za pomocą CheckBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: 1ed623495529609c83c0ced68bfc1696c29d4570
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682245"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="cec8e-102">Instrukcje: Utwórz ListViewItems za pomocą CheckBox</span><span class="sxs-lookup"><span data-stu-id="cec8e-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="cec8e-103">W tym przykładzie przedstawiono sposób wyświetlania kolumny <xref:System.Windows.Controls.CheckBox> kontrolki w <xref:System.Windows.Controls.ListView> formant, który używa <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="cec8e-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec8e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cec8e-104">Example</span></span>  
 <span data-ttu-id="cec8e-105">Aby utworzyć kolumnę zawierającą <xref:System.Windows.Controls.CheckBox> kontrolki w <xref:System.Windows.Controls.ListView>, Utwórz <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="cec8e-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="cec8e-106">Następnie ustaw <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> z <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="cec8e-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="cec8e-107">W poniższym przykładzie przedstawiono <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="cec8e-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="cec8e-108">Przykład wiąże <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> właściwość <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> wartość właściwości <xref:System.Windows.Controls.ListViewItem> zawierający go.</span><span class="sxs-lookup"><span data-stu-id="cec8e-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="cec8e-109">W związku z tym, kiedy <xref:System.Windows.Controls.ListViewItem> zawierający <xref:System.Windows.Controls.CheckBox> jest zaznaczone, <xref:System.Windows.Controls.CheckBox> jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="cec8e-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="cec8e-110">Poniższy przykład pokazuje, jak utworzyć kolumnę <xref:System.Windows.Controls.CheckBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="cec8e-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="cec8e-111">Aby utworzyć kolumnę przykład ustawia <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> właściwość <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="cec8e-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="cec8e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cec8e-112">See also</span></span>
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="cec8e-113">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="cec8e-113">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
- [<span data-ttu-id="cec8e-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="cec8e-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [<span data-ttu-id="cec8e-115">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="cec8e-115">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
