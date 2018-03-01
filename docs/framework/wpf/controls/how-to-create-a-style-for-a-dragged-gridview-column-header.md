---
title: "Jak utworzyć styl dla przeciągniętego nagłówka kolumny GridView"
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
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 001d0ec45ad990ef366e7fc1216a7370aade9cb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="975e9-102">Jak utworzyć styl dla przeciągniętego nagłówka kolumny GridView</span><span class="sxs-lookup"><span data-stu-id="975e9-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="975e9-103">W tym przykładzie pokazano, jak zmienić wygląd przeciąganego <xref:System.Windows.Controls.GridViewColumnHeader> gdy użytkownik zmienia pozycję kolumny.</span><span class="sxs-lookup"><span data-stu-id="975e9-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="975e9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="975e9-104">Example</span></span>  
 <span data-ttu-id="975e9-105">Przeciągnięcie nagłówka kolumny w inne miejsce <xref:System.Windows.Controls.ListView> używającą <xref:System.Windows.Controls.GridView> trybu widoku kolumny jest przenoszony do nowego położenia.</span><span class="sxs-lookup"><span data-stu-id="975e9-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="975e9-106">W trakcie są przeciągnięcie nagłówka kolumny, oprócz oryginalny nagłówek jest wyświetlana kopię przestawne nagłówka.</span><span class="sxs-lookup"><span data-stu-id="975e9-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="975e9-107">Nagłówek kolumny w <xref:System.Windows.Controls.GridView> jest reprezentowana przez <xref:System.Windows.Controls.GridViewColumnHeader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="975e9-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="975e9-108">Aby dostosować wygląd zmiennoprzecinkowych i oryginalnego nagłówki, można ustawić <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> do modyfikowania <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="975e9-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="975e9-109">Te <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> są stosowane po <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> wartość właściwości jest `true` i <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> wartość właściwości jest <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="975e9-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="975e9-110">Gdy użytkownik naciśnie przycisk myszy i zawiera, gdy wskaźnik myszy zatrzyma się w <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> zmiany wartości właściwości na `true`.</span><span class="sxs-lookup"><span data-stu-id="975e9-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="975e9-111">Podobnie, gdy użytkownik rozpoczyna operację przeciągania <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> zmiany właściwości <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="975e9-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="975e9-112">Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> zmienić <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.Background%2A> kolory nagłówków oryginalny i przestawne, gdy użytkownik przeciąga kolumny do nowej pozycji.</span><span class="sxs-lookup"><span data-stu-id="975e9-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="975e9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="975e9-113">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="975e9-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="975e9-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="975e9-115">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="975e9-115">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="975e9-116">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="975e9-116">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
