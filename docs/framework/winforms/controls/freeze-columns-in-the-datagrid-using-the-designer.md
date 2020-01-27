---
title: Zablokuj kolumny w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: af8e07d7b1b0524e33688fd9d879818aa13be041
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745680"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="722a6-102">Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="722a6-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="722a6-103">Gdy użytkownicy będą wyświetlać dane wyświetlane w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms, czasami muszą odwoływać się do pojedynczej kolumny lub zestawu kolumn często.</span><span class="sxs-lookup"><span data-stu-id="722a6-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="722a6-104">Na przykład podczas wyświetlania tabeli informacji o kliencie, która zawiera wiele kolumn, warto wyświetlić nazwę klienta przez cały czas, jednocześnie włączając inne kolumny przewijane poza widocznym regionem.</span><span class="sxs-lookup"><span data-stu-id="722a6-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>

 <span data-ttu-id="722a6-105">Aby osiągnąć takie zachowanie, można zablokować kolumny w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="722a6-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="722a6-106">Po zablokowaniu kolumny wszystkie kolumny po lewej stronie (lub po prawej stronie w skrypcie języka od prawej do lewej) również są zamrożone.</span><span class="sxs-lookup"><span data-stu-id="722a6-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="722a6-107">Zablokowane kolumny pozostają na miejscu, gdy wszystkie inne kolumny można przewijać.</span><span class="sxs-lookup"><span data-stu-id="722a6-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="722a6-108">W przypadku włączenia zmiany kolejności kolumn zablokowane kolumny są traktowane jako odrębne dla grupy z odblokowanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="722a6-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="722a6-109">Użytkownicy mogą zmieniać położenie kolumn w jednej grupie, ale nie mogą przenosić kolumn z jednej grupy do drugiej.</span><span class="sxs-lookup"><span data-stu-id="722a6-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>

 <span data-ttu-id="722a6-110">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="722a6-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="722a6-111">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="722a6-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="722a6-112">Aby zablokować kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="722a6-112">To freeze a column using the designer</span></span>

1. <span data-ttu-id="722a6-113">Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.</span><span class="sxs-lookup"><span data-stu-id="722a6-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="722a6-114">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="722a6-114">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="722a6-115">W siatce **Właściwości kolumny** ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="722a6-115">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="722a6-116">Można także zablokować kolumnę podczas dodawania, zaznaczając pole **zablokowane** w oknie dialogowym **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="722a6-116">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="722a6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="722a6-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [<span data-ttu-id="722a6-118">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="722a6-118">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="722a6-119">Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="722a6-119">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- <span data-ttu-id="722a6-120">[Instrukcje: wyświetlanie tekstu od prawej do lewej w Windows Forms na potrzeby globalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="722a6-120">[How to: Display Right-to-Left Text in Windows Forms for Globalization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span></span>
- [<span data-ttu-id="722a6-121">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="722a6-121">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="722a6-122">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="722a6-122">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
