---
title: Ukrywanie kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: c5344e10a69d86b1733f5462f9c2df0f0e71b8d5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628842"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="3ec00-102">Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3ec00-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="3ec00-103">Czasami chcesz wyświetlić tylko niektóre kolumny, które są dostępne w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3ec00-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3ec00-104">Na przykład możesz chcieć wyświetlić kolumnę wynagrodzenia pracownika dla użytkowników z poświadczeniami zarządzania, jednocześnie ukrywając ją od innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="3ec00-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="3ec00-105">Alternatywnie można powiązać formant ze źródłem danych zawierającym wiele kolumn, tylko niektóre elementy, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="3ec00-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="3ec00-106">W takim przypadku zwykle usuniesz kolumny, które nie są wyświetlane, zamiast ukrywania.</span><span class="sxs-lookup"><span data-stu-id="3ec00-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="3ec00-107">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="3ec00-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="3ec00-108">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="3ec00-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3ec00-109">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3ec00-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="3ec00-110">Aby ukryć kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3ec00-110">To hide a column using the designer</span></span>

1. <span data-ttu-id="3ec00-111">Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.</span><span class="sxs-lookup"><span data-stu-id="3ec00-111">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="3ec00-112">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="3ec00-112">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="3ec00-113">W siatce **Właściwości kolumny** ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> na `false`.</span><span class="sxs-lookup"><span data-stu-id="3ec00-113">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3ec00-114">Możesz również ukryć kolumnę podczas dodawania jej, czyszcząc pole wyboru **widoczny** w oknie dialogowym **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="3ec00-114">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ec00-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ec00-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3ec00-116">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3ec00-116">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="3ec00-117">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ec00-117">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="3ec00-118">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ec00-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
