---
title: 'Instrukcje: nadawanie kolumnom statusu tylko do odczytu w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 6bdd561c863a461f43a5a7aac025fead1f971bb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039811"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="9222e-102">Instrukcje: nadawanie kolumnom statusu tylko do odczytu w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9222e-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="9222e-103">Domyślnie użytkownicy mogą modyfikować dane tekstowe i liczbowe wyświetlane w kontrolce Windows Forms <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="9222e-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9222e-104">Aby wyświetlić dane, które nie są przeznaczone do modyfikacji, należy wprowadzić kolumny zawierające dane tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="9222e-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="9222e-105">Aby uzyskać informacje na temat sposobu, w jaki formant ma być całkowicie tylko [do odczytu, zobacz How to: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="9222e-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="9222e-106">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="9222e-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9222e-107">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9222e-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="9222e-108">Aby utworzyć kolumnę tylko do odczytu przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9222e-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="9222e-109">Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wybierz pozycję **Edytuj kolumny**.</span><span class="sxs-lookup"><span data-stu-id="9222e-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="9222e-110">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="9222e-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="9222e-111">W siatce **Właściwości kolumny** Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="9222e-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9222e-112">Możesz również wprowadzić kolumnę tylko do odczytu, gdy dodasz ją, zaznaczając pole wyboru **tylko do odczytu** w oknie dialogowym **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="9222e-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="9222e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9222e-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9222e-114">Instrukcje: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9222e-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="9222e-115">Instrukcje: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9222e-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="9222e-116">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9222e-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="9222e-117">Instrukcje: Dodawanie formantów do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9222e-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
