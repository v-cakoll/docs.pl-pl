---
title: 'Instrukcje: Tworzenie stylu dla przeciąganego nagłówka kolumny kontrolki GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: dbcdd38e0397b8e637aff962420a2959f33203df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910887"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="cdab7-102">Instrukcje: Tworzenie stylu dla przeciąganego nagłówka kolumny kontrolki GridView</span><span class="sxs-lookup"><span data-stu-id="cdab7-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="cdab7-103">W tym przykładzie pokazano, jak zmienić wygląd przeciąganego <xref:System.Windows.Controls.GridViewColumnHeader> po użytkownik zmienia pozycję kolumny.</span><span class="sxs-lookup"><span data-stu-id="cdab7-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdab7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cdab7-104">Example</span></span>  
 <span data-ttu-id="cdab7-105">Przeciągnięcie nagłówka kolumny do innej lokalizacji w <xref:System.Windows.Controls.ListView> , który używa <xref:System.Windows.Controls.GridView> trybu wyświetlania, kolumna jest przenoszony do nowej pozycji.</span><span class="sxs-lookup"><span data-stu-id="cdab7-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="cdab7-106">Gdy przeciągasz nagłówek kolumny, oprócz oryginalnego nagłówka pojawia się ruchomy kopię nagłówka.</span><span class="sxs-lookup"><span data-stu-id="cdab7-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="cdab7-107">Nagłówek kolumny w <xref:System.Windows.Controls.GridView> jest reprezentowany przez <xref:System.Windows.Controls.GridViewColumnHeader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cdab7-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="cdab7-108">Aby dostosować wygląd zmiennoprzecinkowy a wersją z oryginalnego nagłówków, możesz ustawić <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> do modyfikowania <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="cdab7-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="cdab7-109">Te <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> są stosowane po <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> wartość właściwości jest `true` i <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> wartość właściwości jest <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="cdab7-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="cdab7-110">Gdy użytkownik naciśnie przycisk myszy i przechowuje w dół, gdy mysz <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> ulega zmianie wartość właściwości do `true`.</span><span class="sxs-lookup"><span data-stu-id="cdab7-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="cdab7-111">Podobnie, gdy użytkownik rozpoczyna się operacja przeciągania <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> zmiany właściwości <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="cdab7-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="cdab7-112">Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> zmienić <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.Background%2A> kolory nagłówków oryginalnego i zmiennoprzecinkowych, gdy użytkownik przeciągnie kolumny do nowej pozycji.</span><span class="sxs-lookup"><span data-stu-id="cdab7-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="cdab7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdab7-113">See also</span></span>

- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="cdab7-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="cdab7-114">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="cdab7-115">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="cdab7-115">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="cdab7-116">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="cdab7-116">GridView Overview</span></span>](gridview-overview.md)
