---
title: 'Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: e82fbcf63047873ebc6e5c40b8b9fbeb14a672e5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038181"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="6b7e2-102">Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="6b7e2-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="6b7e2-103">Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać wiele kolumn dla każdego elementu listy w widoku **szczegółów** .</span><span class="sxs-lookup"><span data-stu-id="6b7e2-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="6b7e2-104">Możesz użyć kolumn, aby wyświetlić kilka typów informacji dotyczących każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="6b7e2-105">Na przykład lista plików może zawierać nazwę pliku, typ pliku, rozmiar i datę ostatniej modyfikacji pliku.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="6b7e2-106">Aby uzyskać informacje na temat wypełniania kolumn po ich utworzeniu [, zobacz How to: Wyświetlaj elementy SubItems w kolumnach za pomocą](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)kontrolki ListView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="6b7e2-107">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="6b7e2-108">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6b7e2-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="6b7e2-109">Aby dodać kolumny w projektancie</span><span class="sxs-lookup"><span data-stu-id="6b7e2-109">To add columns in the designer</span></span>

1. <span data-ttu-id="6b7e2-110">W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość kontrolki na <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="6b7e2-111">W oknie **Właściwości** kliknij przycisk wielokropka ( ![przycisk wielokropka (...) w okno właściwości programu Visual <xref:System.Windows.Forms.ListView.Columns%2A> Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="6b7e2-112">Zostanie wyświetlony **Edytor kolekcji ColumnHeader** .</span><span class="sxs-lookup"><span data-stu-id="6b7e2-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="6b7e2-113">Użyj przycisku **Dodaj** , aby dodać nowe kolumny.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="6b7e2-114">Następnie można wybrać nagłówek kolumny i ustawić jego tekst (podpis kolumny), wyrównanie tekstu i szerokość.</span><span class="sxs-lookup"><span data-stu-id="6b7e2-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b7e2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b7e2-115">See also</span></span>

- [<span data-ttu-id="6b7e2-116">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6b7e2-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="6b7e2-117">Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b7e2-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="6b7e2-118">Instrukcje: Wyświetlanie elementów SubItems w kolumnach za pomocą kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b7e2-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="6b7e2-119">Instrukcje: Wyświetl ikony dla kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b7e2-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="6b7e2-120">Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6b7e2-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
