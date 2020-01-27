---
title: Określanie kolumn jako tylko do odczytu w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 51d9488ef83f7d2c1c01c9ffd756edf8944d738d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744975"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="e7d81-102">Porady: nadawanie kolumnom statusu tylko do odczytu w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e7d81-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="e7d81-103">Domyślnie użytkownicy mogą modyfikować dane tekstowe i liczbowe wyświetlane w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e7d81-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e7d81-104">Aby wyświetlić dane, które nie są przeznaczone do modyfikacji, należy wprowadzić kolumny zawierające dane tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="e7d81-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="e7d81-105">Aby uzyskać informacje na temat sposobu, w jaki formant ma być całkowicie tylko do odczytu, zobacz [How to: zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e7d81-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="e7d81-106">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="e7d81-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e7d81-107">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e7d81-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="e7d81-108">Aby utworzyć kolumnę tylko do odczytu przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e7d81-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="e7d81-109">Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.</span><span class="sxs-lookup"><span data-stu-id="e7d81-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="e7d81-110">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="e7d81-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="e7d81-111">W siatce **Właściwości kolumny** ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="e7d81-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e7d81-112">Możesz również wprowadzić kolumnę tylko do odczytu, gdy dodasz ją, zaznaczając pole wyboru **tylko do odczytu** w oknie dialogowym **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="e7d81-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7d81-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7d81-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e7d81-114">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e7d81-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="e7d81-115">Instrukcje: zapobieganie dodawaniu i usuwaniu wierszy do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e7d81-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="e7d81-116">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7d81-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="e7d81-117">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7d81-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
