---
title: Dodawanie kolumn do formantu ListView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744606"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="b48ba-102">Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="b48ba-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="b48ba-103">Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać wiele kolumn dla każdego elementu listy w widoku **szczegółów** .</span><span class="sxs-lookup"><span data-stu-id="b48ba-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="b48ba-104">Możesz użyć kolumn, aby wyświetlić kilka typów informacji dotyczących każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="b48ba-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="b48ba-105">Na przykład lista plików może zawierać nazwę pliku, typ pliku, rozmiar i datę ostatniej modyfikacji pliku.</span><span class="sxs-lookup"><span data-stu-id="b48ba-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="b48ba-106">Aby uzyskać informacje na temat wypełniania kolumn po ich utworzeniu, zobacz [How to: Display SubItems in Columns with Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b48ba-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="b48ba-107">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="b48ba-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="b48ba-108">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b48ba-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="b48ba-109">Aby dodać kolumny w projektancie</span><span class="sxs-lookup"><span data-stu-id="b48ba-109">To add columns in the designer</span></span>

1. <span data-ttu-id="b48ba-110">W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.ListView.View%2A> kontrolki na <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="b48ba-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="b48ba-111">W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="b48ba-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="b48ba-112">Zostanie wyświetlony **Edytor kolekcji ColumnHeader** .</span><span class="sxs-lookup"><span data-stu-id="b48ba-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="b48ba-113">Użyj przycisku **Dodaj** , aby dodać nowe kolumny.</span><span class="sxs-lookup"><span data-stu-id="b48ba-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="b48ba-114">Następnie można wybrać nagłówek kolumny i ustawić jego tekst (podpis kolumny), wyrównanie tekstu i szerokość.</span><span class="sxs-lookup"><span data-stu-id="b48ba-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="b48ba-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b48ba-115">See also</span></span>

- [<span data-ttu-id="b48ba-116">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="b48ba-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="b48ba-117">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b48ba-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b48ba-118">Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b48ba-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b48ba-119">Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b48ba-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b48ba-120">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b48ba-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
