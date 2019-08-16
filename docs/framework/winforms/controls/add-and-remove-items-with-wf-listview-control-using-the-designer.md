---
title: 'Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040086"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="4e689-102">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="4e689-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="4e689-103">Proces dodawania elementu do kontrolki Windows Forms <xref:System.Windows.Forms.ListView> składa się głównie z określania elementu i przypisywania do niego właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e689-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="4e689-104">Dodawanie lub usuwanie elementów listy można wykonać w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="4e689-104">Adding or removing list items can be done at any time.</span></span>

<span data-ttu-id="4e689-105">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="4e689-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="4e689-106">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4e689-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="4e689-107">Aby dodać lub usunąć elementy przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="4e689-107">To add or remove items using the designer</span></span>

1. <span data-ttu-id="4e689-108"><xref:System.Windows.Forms.ListView> Zaznacz kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="4e689-108">Select the <xref:System.Windows.Forms.ListView> control.</span></span>

2. <span data-ttu-id="4e689-109">W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.ListView.Items%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e689-109">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="4e689-110">Zostanie wyświetlony **Edytor kolekcji ListViewItem** .</span><span class="sxs-lookup"><span data-stu-id="4e689-110">The **ListViewItem Collection Editor** appears.</span></span>

3. <span data-ttu-id="4e689-111">Aby dodać element, kliknij przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="4e689-111">To add an item, click the **Add** button.</span></span> <span data-ttu-id="4e689-112">Następnie można ustawić właściwości nowego elementu, <xref:System.Windows.Forms.ListView.Text%2A> na przykład właściwości i. <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="4e689-112">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

4. <span data-ttu-id="4e689-113">Aby usunąć element, zaznacz go i kliknij przycisk **Usuń** .</span><span class="sxs-lookup"><span data-stu-id="4e689-113">To remove an item, select it and click the **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e689-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e689-114">See also</span></span>

- [<span data-ttu-id="4e689-115">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="4e689-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="4e689-116">Instrukcje: Dodawanie kolumn do kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e689-116">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4e689-117">Instrukcje: Wyświetlanie elementów SubItems w kolumnach za pomocą kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e689-117">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4e689-118">Instrukcje: Wyświetl ikony dla kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e689-118">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4e689-119">Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4e689-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="4e689-120">Instrukcje: Grupuj elementy w Windows Forms formancie ListView</span><span class="sxs-lookup"><span data-stu-id="4e689-120">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
