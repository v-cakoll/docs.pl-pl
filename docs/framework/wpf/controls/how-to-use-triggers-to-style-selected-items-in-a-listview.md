---
title: 'Instrukcje: Używanie wyzwalaczy do nadawania stylu wybranym elementom w kontrolce ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: ad64382b871bae9114a1e63257de3f8595376923
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696201"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="649d7-102">Instrukcje: Używanie wyzwalaczy do nadawania stylu wybranym elementom w kontrolce ListView</span><span class="sxs-lookup"><span data-stu-id="649d7-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="649d7-103">Ten przykład pokazuje jak zdefiniować <xref:System.Windows.Style.Triggers%2A> dla <xref:System.Windows.Controls.ListViewItem> kontroli, aby po wartości właściwości <xref:System.Windows.Controls.ListViewItem> zmian <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> zmianach w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="649d7-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="649d7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="649d7-104">Example</span></span>  
 <span data-ttu-id="649d7-105">Jeśli chcesz <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> zmiany w odpowiedzi na zmiany właściwości, zdefiniuj <xref:System.Windows.Style.Triggers%2A> dla <xref:System.Windows.Style> zmiany.</span><span class="sxs-lookup"><span data-stu-id="649d7-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="649d7-106">W poniższym przykładzie zdefiniowano <xref:System.Windows.Trigger> określająca <xref:System.Windows.Controls.Control.Foreground%2A> właściwości <xref:System.Windows.Media.Brushes.Blue%2A> i zmienia <xref:System.Windows.FrameworkElement.Cursor%2A> do wyświetlenia <xref:System.Windows.Input.CursorType.Hand> podczas <xref:System.Windows.UIElement.IsMouseOver%2A> zmiany właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="649d7-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="649d7-107">W poniższym przykładzie zdefiniowano <xref:System.Windows.MultiTrigger> określająca <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.ListViewItem> do <xref:System.Windows.Media.Brushes.Yellow%2A> podczas <xref:System.Windows.Controls.ListViewItem> wybranego elementu i ma fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="649d7-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="649d7-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="649d7-108">See also</span></span>

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="649d7-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="649d7-109">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="649d7-110">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="649d7-110">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="649d7-111">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="649d7-111">GridView Overview</span></span>](gridview-overview.md)
