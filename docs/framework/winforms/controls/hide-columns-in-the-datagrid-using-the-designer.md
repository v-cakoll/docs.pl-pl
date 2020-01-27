---
title: Ukrywanie kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 3c9a6bdeacbeb5929488e6af0054403db73c4239
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738658"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="c8450-102">Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c8450-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="c8450-103">Czasami chcesz wyświetlić tylko niektóre kolumny, które są dostępne w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8450-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c8450-104">Na przykład możesz chcieć wyświetlić kolumnę wynagrodzenia pracownika dla użytkowników z poświadczeniami zarządzania, jednocześnie ukrywając ją od innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="c8450-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="c8450-105">Alternatywnie można powiązać formant ze źródłem danych zawierającym wiele kolumn, tylko niektóre elementy, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="c8450-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="c8450-106">W takim przypadku zwykle usuniesz kolumny, które nie są wyświetlane, zamiast ukrywania.</span><span class="sxs-lookup"><span data-stu-id="c8450-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="c8450-107">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="c8450-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="c8450-108">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="c8450-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c8450-109">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c8450-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="c8450-110">Aby ukryć kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c8450-110">To hide a column using the designer</span></span>

1. <span data-ttu-id="c8450-111">Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.</span><span class="sxs-lookup"><span data-stu-id="c8450-111">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="c8450-112">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="c8450-112">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="c8450-113">W siatce **Właściwości kolumny** ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> na `false`.</span><span class="sxs-lookup"><span data-stu-id="c8450-113">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c8450-114">Możesz również ukryć kolumnę podczas dodawania jej, czyszcząc pole wyboru **widoczny** w oknie dialogowym **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="c8450-114">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8450-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8450-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c8450-116">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c8450-116">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="c8450-117">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8450-117">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="c8450-118">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8450-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
