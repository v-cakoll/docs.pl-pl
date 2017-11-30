---
title: "Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a97899d544dcc0d9f9ad59cbb34a01da76ef5fe5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="59df3-102">Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="59df3-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="59df3-103">Gdy użytkownicy wyświetlać dane wyświetlane w formularzach systemu Windows <xref:System.Windows.Forms.DataGridView> kontroli, czasami muszą odwoływać się do jednej kolumny lub zestaw kolumn często.</span><span class="sxs-lookup"><span data-stu-id="59df3-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="59df3-104">Na przykład podczas wyświetlania informacji klienta, który zawiera wiele kolumn tabeli, jest przydatne w przypadku można wyświetlić nazwę klienta przez cały czas podczas włączania obsługi innych kolumn przewinięcia poza region widoczny.</span><span class="sxs-lookup"><span data-stu-id="59df3-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="59df3-105">Aby osiągnąć ten problem, można zablokować kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="59df3-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="59df3-106">Po zablokowaniu kolumny zablokowanych również wszystkich kolumn po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej).</span><span class="sxs-lookup"><span data-stu-id="59df3-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="59df3-107">Zablokowane kolumny pozostają bez zmian, gdy mogą być przewijane w innych kolumn.</span><span class="sxs-lookup"><span data-stu-id="59df3-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="59df3-108">Jeśli włączono zmiany układu kolumn zablokowane kolumny są traktowane jako grupę różne od kolumny.</span><span class="sxs-lookup"><span data-stu-id="59df3-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="59df3-109">Użytkownicy można zmienić kolumny w każdej grupie, ale nie może przenieść kolumny z jednej grupy, do drugiego.</span><span class="sxs-lookup"><span data-stu-id="59df3-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="59df3-110">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="59df3-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="59df3-111">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="59df3-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59df3-112">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="59df3-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="59df3-113">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="59df3-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="59df3-114">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="59df3-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="59df3-115">Aby zablokować kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="59df3-115">To freeze a column using the designer</span></span>  
  
1.  <span data-ttu-id="59df3-116">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli, a następnie wybierz **Edytowanie kolumn**.</span><span class="sxs-lookup"><span data-stu-id="59df3-116">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="59df3-117">Wybierz kolumny z **wybrane kolumny** listy.</span><span class="sxs-lookup"><span data-stu-id="59df3-117">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="59df3-118">W **właściwości kolumny** siatki, ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="59df3-118">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59df3-119">Możesz również zablokować kolumnę podczas dodawania go, wybierając **zablokowane** polu **Dodaj kolumnę** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="59df3-119">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59df3-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59df3-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="59df3-121">Porady: Dodawanie i usuwanie kolumn w oknach formularzy formantu DataGridView, przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="59df3-121">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="59df3-122">Porady: Włączanie zmiany układu kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="59df3-122">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="59df3-123">Porady: wyświetlanie tekstu od prawej do lewej w formularzach systemu Windows dla globalizacji</span><span class="sxs-lookup"><span data-stu-id="59df3-123">How to: Display Right-to-Left Text in Windows Forms for Globalization</span></span>](http://msdn.microsoft.com/en-us/f0663385-2354-4c65-8676-706422283b14)  
 [<span data-ttu-id="59df3-124">Porady: Tworzenie projektu aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="59df3-124">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="59df3-125">Porady: dodawanie formantów do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="59df3-125">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
