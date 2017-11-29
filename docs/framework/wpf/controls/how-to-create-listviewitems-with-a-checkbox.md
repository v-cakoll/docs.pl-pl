---
title: "Jak utworzyć ListViewItems za pomocą CheckBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cc6ebb3671dcc65d690fde5d4796c9034553eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="0f1af-102">Jak utworzyć ListViewItems za pomocą CheckBox</span><span class="sxs-lookup"><span data-stu-id="0f1af-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="0f1af-103">W tym przykładzie przedstawiono sposób wyświetlania kolumny <xref:System.Windows.Controls.CheckBox> formantów w <xref:System.Windows.Controls.ListView> formant, który używa <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="0f1af-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f1af-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f1af-104">Example</span></span>  
 <span data-ttu-id="0f1af-105">Aby utworzyć kolumnę zawierającą <xref:System.Windows.Controls.CheckBox> formantów w <xref:System.Windows.Controls.ListView>, Utwórz <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="0f1af-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="0f1af-106">Następnie ustaw <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> z <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="0f1af-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="0f1af-107">W poniższym przykładzie przedstawiono <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="0f1af-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="0f1af-108">Przykład wiąże <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> właściwość <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> wartość właściwości <xref:System.Windows.Controls.ListViewItem> go zawiera.</span><span class="sxs-lookup"><span data-stu-id="0f1af-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="0f1af-109">W związku z tym, kiedy <xref:System.Windows.Controls.ListViewItem> zawierający <xref:System.Windows.Controls.CheckBox> jest zaznaczone, <xref:System.Windows.Controls.CheckBox> jest zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="0f1af-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="0f1af-110">Poniższy przykład pokazuje, jak można utworzyć kolumny z <xref:System.Windows.Controls.CheckBox> formantów.</span><span class="sxs-lookup"><span data-stu-id="0f1af-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="0f1af-111">Aby utworzyć kolumnę zestawy przykład <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> właściwość <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="0f1af-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="0f1af-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f1af-112">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="0f1af-113">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="0f1af-113">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="0f1af-114">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="0f1af-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="0f1af-115">Omówienie widoku GridView</span><span class="sxs-lookup"><span data-stu-id="0f1af-115">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
