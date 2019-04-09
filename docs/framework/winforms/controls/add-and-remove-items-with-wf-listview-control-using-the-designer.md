---
title: 'Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 37e793104eb29c21e67b975a7caa372cc817e57f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143887"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="1b6f8-102">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="1b6f8-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="1b6f8-103">Proces dodawania elementu do formularzy Windows <xref:System.Windows.Forms.ListView> kontroli składa się przede wszystkim określenie elementu i przypisywanie właściwości do niego.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="1b6f8-104">Dodawanie lub usuwanie pozycji listy może odbywać się w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="1b6f8-105">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="1b6f8-106">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1b6f8-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b6f8-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1b6f8-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1b6f8-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1b6f8-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="1b6f8-110">Aby dodać lub usunąć elementy przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="1b6f8-110">To add or remove items using the designer</span></span>  
  
1.  <span data-ttu-id="1b6f8-111">Wybierz <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="1b6f8-112">W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-112">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="1b6f8-113">**ListViewItem — Edytor kolekcji** pojawia się.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="1b6f8-114">Aby dodać element, kliknij przycisk **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="1b6f8-115">Następnie można ustawić właściwości nowego elementu, takie jak <xref:System.Windows.Forms.ListView.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4.  <span data-ttu-id="1b6f8-116">Aby usunąć element, wybierz ją, a następnie kliknij przycisk **Usuń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1b6f8-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b6f8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b6f8-117">See also</span></span>

- [<span data-ttu-id="1b6f8-118">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1b6f8-118">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="1b6f8-119">Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b6f8-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="1b6f8-120">Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b6f8-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="1b6f8-121">Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b6f8-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="1b6f8-122">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="1b6f8-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="1b6f8-123">Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b6f8-123">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
