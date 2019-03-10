---
title: 'Instrukcje: Zakotwiczenia formantów na formularzach Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: d3dd413793c8a6da900acbf60cc5a20edf908906
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720374"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="255fe-102">Instrukcje: Zakotwiczenia formantów na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="255fe-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="255fe-103">W przypadku projektowania formularza, który użytkownik może zmienić rozmiar w czasie wykonywania, kontrolek w formularzu należy zmienić rozmiar i odpowiednio zmienić położenie.</span><span class="sxs-lookup"><span data-stu-id="255fe-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="255fe-104">Aby zmienić rozmiar kontrolki dynamicznej z formularza, można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="255fe-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="255fe-105"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwość definiuje pozycji zakotwiczenia dla formantu.</span><span class="sxs-lookup"><span data-stu-id="255fe-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="255fe-106">Gdy formant jest zakotwiczona do formularza i rozmiarów formularza, formant zachowuje odległość między formantem i pozycji zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="255fe-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="255fe-107">Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formant, który jest zakotwiczona lewy, prawy i dolną krawędzią formularza, jak rozmiarów formularza <xref:System.Windows.Forms.TextBox> kontrolować zmiany rozmiaru w poziomie, tak, aby utrzymuje tej samej odległości od lewej i prawej strony formularza.</span><span class="sxs-lookup"><span data-stu-id="255fe-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="255fe-108">Ponadto kontrolka umieszcza się w pionie tak, aby jego lokalizacja jest zawsze tej samej odległości od dolnej krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="255fe-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="255fe-109">Jeśli formant nie jest zakotwiczona rozmiarów formularza, położenie formantu względem krawędzi formularza jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="255fe-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="255fe-110"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwość wchodzi w interakcję z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="255fe-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="255fe-111">Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="255fe-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="255fe-112">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="255fe-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="255fe-113">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="255fe-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="255fe-114">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="255fe-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="255fe-115">Aby móc zakotwiczyć kontrolki na formularzu</span><span class="sxs-lookup"><span data-stu-id="255fe-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="255fe-116">Wybierz formant, który chcesz, aby móc zakotwiczyć.</span><span class="sxs-lookup"><span data-stu-id="255fe-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="255fe-117">Wiele kontrolek można zakotwiczyć jednocześnie, naciskając klawisz CTRL, klikając każdy formant, aby go zaznaczyć, a następnie postępuj zgodnie z pozostałą część tej procedury.</span><span class="sxs-lookup"><span data-stu-id="255fe-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="255fe-118">W **właściwości** okna, kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="255fe-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="255fe-119">Zostanie wyświetlony Edytor, pokazujący krzyżyk.</span><span class="sxs-lookup"><span data-stu-id="255fe-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="255fe-120">Aby ustawić elementu zakotwiczenia, kliknij lewym górnym rogu, po prawej stronie i dolną sekcję między środowiskami.</span><span class="sxs-lookup"><span data-stu-id="255fe-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="255fe-121">Kontrolki jest zakotwiczona u góry i pozostanie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="255fe-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="255fe-122">Aby wyczyścić boku formant, który został zakotwiczone, kliknij ten arm między środowiskami.</span><span class="sxs-lookup"><span data-stu-id="255fe-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="255fe-123">Aby zamknąć <xref:System.Windows.Forms.Control.Anchor%2A> Edytor właściwości, kliknij przycisk <xref:System.Windows.Forms.Control.Anchor%2A> ponownie nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="255fe-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="255fe-124">Gdy formularz jest wyświetlana w czasie wykonywania, pozostaje osiągniesz idealną pozycję w tej samej odległości od krawędzi formularza zmienia rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="255fe-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="255fe-125">Odległość od zakotwiczonej krawędzi zawsze pozostaje taki sam jak odległości określonej, gdy kontrolka jest umieszczany w Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="255fe-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="255fe-126">Niektóre kontrolki, takie jak <xref:System.Windows.Forms.ComboBox> sterowania, ma ograniczenia do ich wysokość.</span><span class="sxs-lookup"><span data-stu-id="255fe-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="255fe-127">Zakotwiczanie formantu do dołu formularza lub kontener nie może wymusić kontroli przekroczenie limitu wysokości.</span><span class="sxs-lookup"><span data-stu-id="255fe-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="255fe-128">Musi być dziedziczone formantów `Protected` mogli jest zakotwiczona.</span><span class="sxs-lookup"><span data-stu-id="255fe-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="255fe-129">Aby zmienić poziom dostępu formantu, ustaw jego `Modifiers` właściwość **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="255fe-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="255fe-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="255fe-130">See also</span></span>
- [<span data-ttu-id="255fe-131">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="255fe-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="255fe-132">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="255fe-132">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="255fe-133">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="255fe-133">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="255fe-134">Instrukcje: Dokowanie formantów na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="255fe-134">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="255fe-135">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="255fe-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="255fe-136">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="255fe-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="255fe-137">Przewodnik: Układania Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize</span><span class="sxs-lookup"><span data-stu-id="255fe-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
