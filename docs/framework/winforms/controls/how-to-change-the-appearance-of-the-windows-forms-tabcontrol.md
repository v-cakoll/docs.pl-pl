---
title: Zmień wygląd elementu TabControl
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
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746612"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="2afd6-102">Porady: zmienianie wyglądu składnika TabControl formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2afd6-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="2afd6-103">Można zmienić wygląd kart w Windows Forms przy użyciu właściwości <xref:System.Windows.Forms.TabControl> i <xref:System.Windows.Forms.TabPage> obiektów, które tworzą poszczególne karty w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="2afd6-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="2afd6-104">Ustawiając te właściwości, można wyświetlać obrazy na kartach, wyświetlać tabulatory w pionie zamiast w poziomie, wyświetlać wiele wierszy kart i programowo włączać lub wyłączać karty.</span><span class="sxs-lookup"><span data-stu-id="2afd6-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="2afd6-105">Aby wyświetlić ikonę na etykiecie części karty</span><span class="sxs-lookup"><span data-stu-id="2afd6-105">To display an icon on the label part of a tab</span></span>  
  
1. <span data-ttu-id="2afd6-106">Dodaj kontrolkę <xref:System.Windows.Forms.ImageList> do formularza.</span><span class="sxs-lookup"><span data-stu-id="2afd6-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2. <span data-ttu-id="2afd6-107">Dodaj obrazy do listy obrazów.</span><span class="sxs-lookup"><span data-stu-id="2afd6-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="2afd6-108">Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnik ImageList](imagelist-component-windows-forms.md) i [instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="2afd6-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3. <span data-ttu-id="2afd6-109">Ustaw właściwość <xref:System.Windows.Forms.TabControl.ImageList%2A> <xref:System.Windows.Forms.TabControl> na kontrolkę <xref:System.Windows.Forms.ImageList>.</span><span class="sxs-lookup"><span data-stu-id="2afd6-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4. <span data-ttu-id="2afd6-110">Ustaw właściwość <xref:System.Windows.Forms.TabPage.ImageIndex%2A> <xref:System.Windows.Forms.TabPage> na indeks odpowiedniego obrazu na liście.</span><span class="sxs-lookup"><span data-stu-id="2afd6-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="2afd6-111">Aby utworzyć wiele wierszy kart</span><span class="sxs-lookup"><span data-stu-id="2afd6-111">To create multiple rows of tabs</span></span>  
  
1. <span data-ttu-id="2afd6-112">Dodaj liczbę żądanych stron kart.</span><span class="sxs-lookup"><span data-stu-id="2afd6-112">Add the number of tab pages you want.</span></span>  
  
2. <span data-ttu-id="2afd6-113">Ustaw właściwość <xref:System.Windows.Forms.TabControl.Multiline%2A> <xref:System.Windows.Forms.TabControl> na `true`.</span><span class="sxs-lookup"><span data-stu-id="2afd6-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3. <span data-ttu-id="2afd6-114">Jeśli karty nie pojawiają się jeszcze w wielu wierszach, ustaw właściwość <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.TabControl> na węższe niż wszystkie karty.</span><span class="sxs-lookup"><span data-stu-id="2afd6-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="2afd6-115">Aby rozmieścić karty po stronie kontrolki</span><span class="sxs-lookup"><span data-stu-id="2afd6-115">To arrange tabs on the side of the control</span></span>  
  
- <span data-ttu-id="2afd6-116">Ustaw właściwość <xref:System.Windows.Forms.TabControl.Alignment%2A> <xref:System.Windows.Forms.TabControl> na <xref:System.Windows.Forms.TabAlignment.Left> lub <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="2afd6-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="2afd6-117">Aby programowo włączyć lub wyłączyć wszystkie kontrolki na karcie</span><span class="sxs-lookup"><span data-stu-id="2afd6-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1. <span data-ttu-id="2afd6-118">Ustaw właściwość <xref:System.Windows.Forms.TabPage.Enabled%2A> <xref:System.Windows.Forms.TabPage> na `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="2afd6-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="2afd6-119">Aby wyświetlić karty jako przyciski</span><span class="sxs-lookup"><span data-stu-id="2afd6-119">To display tabs as buttons</span></span>  
  
- <span data-ttu-id="2afd6-120">Ustaw właściwość <xref:System.Windows.Forms.TabControl.Appearance%2A> <xref:System.Windows.Forms.TabControl> na <xref:System.Windows.Forms.TabAppearance.Buttons> lub <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="2afd6-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afd6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2afd6-121">See also</span></span>

- [<span data-ttu-id="2afd6-122">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="2afd6-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="2afd6-123">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2afd6-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="2afd6-124">Instrukcje: dodawanie kontrolki do karty</span><span class="sxs-lookup"><span data-stu-id="2afd6-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="2afd6-125">Instrukcje: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="2afd6-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="2afd6-126">Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2afd6-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
