---
title: 'Instrukcje: zmienianie wyglądu składnika TabControl formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 05df05a52914f27a4b62cf7bde92e5d942b6ea06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331341"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="5f3ba-102">Instrukcje: zmienianie wyglądu składnika TabControl formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5f3ba-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="5f3ba-103">Można zmienić wygląd karty w formularzach Windows Forms za pomocą właściwości <xref:System.Windows.Forms.TabControl> i <xref:System.Windows.Forms.TabPage> obiektów, które składają się na poszczególnych kartach formantu.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="5f3ba-104">Przez ustawienie tych właściwości, można wyświetlanie obrazów na kartach, wyświetlanie kart w pionie zamiast w poziomie, wyświetlić wiele wierszy kart i włączyć lub wyłączyć karty programowo.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="5f3ba-105">Aby wyświetlić ikonę na części etykieta karty</span><span class="sxs-lookup"><span data-stu-id="5f3ba-105">To display an icon on the label part of a tab</span></span>  
  
1. <span data-ttu-id="5f3ba-106">Dodaj <xref:System.Windows.Forms.ImageList> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2. <span data-ttu-id="5f3ba-107">Dodawanie obrazów do listy obrazów.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="5f3ba-108">Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](imagelist-component-windows-forms.md) i [jak: Dodawanie lub usuwanie obrazów za pomocą Windows składnika ImageList formularzy](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="5f3ba-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3. <span data-ttu-id="5f3ba-109">Ustaw <xref:System.Windows.Forms.TabControl.ImageList%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.ImageList> kontroli.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4. <span data-ttu-id="5f3ba-110">Ustaw <xref:System.Windows.Forms.TabPage.ImageIndex%2A> właściwość <xref:System.Windows.Forms.TabPage> do indeksu odpowiedniego obrazu na liście.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="5f3ba-111">Aby utworzyć wiele wierszy kart</span><span class="sxs-lookup"><span data-stu-id="5f3ba-111">To create multiple rows of tabs</span></span>  
  
1. <span data-ttu-id="5f3ba-112">Dodaj numer strony kart, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-112">Add the number of tab pages you want.</span></span>  
  
2. <span data-ttu-id="5f3ba-113">Ustaw <xref:System.Windows.Forms.TabControl.Multiline%2A> właściwość <xref:System.Windows.Forms.TabControl> do `true`.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3. <span data-ttu-id="5f3ba-114">Jeśli karty nie ma już w wielu wierszach, ustaw <xref:System.Windows.Forms.Control.Width%2A> właściwość <xref:System.Windows.Forms.TabControl> być mniejsza niż wszystkie karty.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="5f3ba-115">Aby rozmieścić karty boku kontrolki</span><span class="sxs-lookup"><span data-stu-id="5f3ba-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="5f3ba-116">Ustaw <xref:System.Windows.Forms.TabControl.Alignment%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.TabAlignment.Left> lub <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="5f3ba-117">Aby programowo włączyć lub wyłączyć wszystkie kontrolki na karcie</span><span class="sxs-lookup"><span data-stu-id="5f3ba-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1. <span data-ttu-id="5f3ba-118">Ustaw <xref:System.Windows.Forms.TabPage.Enabled%2A> właściwość <xref:System.Windows.Forms.TabPage> do `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="5f3ba-119">Aby wyświetlić karty przyciski</span><span class="sxs-lookup"><span data-stu-id="5f3ba-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="5f3ba-120">Ustaw <xref:System.Windows.Forms.TabControl.Appearance%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.TabAppearance.Buttons> lub <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="5f3ba-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3ba-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f3ba-121">See also</span></span>

- [<span data-ttu-id="5f3ba-122">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5f3ba-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="5f3ba-123">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="5f3ba-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="5f3ba-124">Instrukcje: Dodawanie kontrolki do karty</span><span class="sxs-lookup"><span data-stu-id="5f3ba-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="5f3ba-125">Instrukcje: Wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="5f3ba-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="5f3ba-126">Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5f3ba-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
