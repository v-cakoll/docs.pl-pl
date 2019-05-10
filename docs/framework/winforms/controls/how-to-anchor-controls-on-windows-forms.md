---
title: 'Instrukcje: kotwiczenie kontrolek na formularzach systemu Windows'
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
ms.openlocfilehash: b48761bda2baad4f7d1e6db9b41d73d6d54bc081
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211271"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="653b6-102">Instrukcje: kotwiczenie kontrolek na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="653b6-102">How to: Anchor Controls on Windows Forms</span></span>

<span data-ttu-id="653b6-103">Projektując formularz, który użytkownik może zmienić rozmiar w czasie wykonywania, kontrolek w formularzu należy zmienić rozmiar i zmienić położenie prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="653b6-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="653b6-104">Aby zmienić rozmiar kontrolki dynamicznej z formularza, można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="653b6-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="653b6-105"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwość definiuje pozycji zakotwiczenia dla formantu.</span><span class="sxs-lookup"><span data-stu-id="653b6-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="653b6-106">Gdy formant jest zakotwiczona do formularza i rozmiarów formularza, formant zachowuje odległość między formantem i pozycji zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="653b6-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="653b6-107">Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formant, który jest zakotwiczona lewy, prawy i dolną krawędzią formularza, jak rozmiarów formularza <xref:System.Windows.Forms.TextBox> kontrolować zmiany rozmiaru w poziomie, tak, aby utrzymuje tej samej odległości od lewej i prawej strony formularza.</span><span class="sxs-lookup"><span data-stu-id="653b6-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="653b6-108">Ponadto kontrolka umieszcza się w pionie tak, aby jego lokalizacja jest zawsze tej samej odległości od dolnej krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="653b6-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="653b6-109">Jeśli formant nie jest zakotwiczona rozmiarów formularza, położenie formantu względem krawędzi formularza jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="653b6-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="653b6-110"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwość wchodzi w interakcję z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="653b6-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="653b6-111">Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="653b6-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="653b6-112">Zakotwicz formant w formularzu</span><span class="sxs-lookup"><span data-stu-id="653b6-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="653b6-113">W programie Visual Studio wybierz formant, który chcesz, aby móc zakotwiczyć.</span><span class="sxs-lookup"><span data-stu-id="653b6-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="653b6-114">Wiele kontrolek można zakotwiczyć jednocześnie, naciskając klawisz CTRL, klikając każdy formant, aby go zaznaczyć, a następnie postępuj zgodnie z pozostałą część tej procedury.</span><span class="sxs-lookup"><span data-stu-id="653b6-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="653b6-115">W **właściwości** okna, kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="653b6-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="653b6-116">Zostanie wyświetlony Edytor, pokazujący krzyżyk.</span><span class="sxs-lookup"><span data-stu-id="653b6-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="653b6-117">Aby ustawić elementu zakotwiczenia, kliknij lewym górnym rogu, po prawej stronie i dolną sekcję między środowiskami.</span><span class="sxs-lookup"><span data-stu-id="653b6-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="653b6-118">Kontrolki jest zakotwiczona u góry i pozostanie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="653b6-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="653b6-119">Aby wyczyścić boku formant, który został zakotwiczone, kliknij ten arm między środowiskami.</span><span class="sxs-lookup"><span data-stu-id="653b6-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="653b6-120">Aby zamknąć <xref:System.Windows.Forms.Control.Anchor%2A> Edytor właściwości, kliknij przycisk <xref:System.Windows.Forms.Control.Anchor%2A> ponownie nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="653b6-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="653b6-121">Gdy formularz jest wyświetlana w czasie wykonywania, pozostaje osiągniesz idealną pozycję w tej samej odległości od krawędzi formularza zmienia rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="653b6-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="653b6-122">Odległość od zakotwiczonej krawędzi zawsze pozostaje taki sam jak odległości określonej, gdy kontrolka jest umieszczany w Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="653b6-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="653b6-123">Niektóre kontrolki, takie jak <xref:System.Windows.Forms.ComboBox> sterowania, ma ograniczenia do ich wysokość.</span><span class="sxs-lookup"><span data-stu-id="653b6-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="653b6-124">Zakotwiczanie formantu do dołu formularza lub kontener nie może wymusić kontroli przekroczenie limitu wysokości.</span><span class="sxs-lookup"><span data-stu-id="653b6-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="653b6-125">Musi być dziedziczone formantów `Protected` mogli jest zakotwiczona.</span><span class="sxs-lookup"><span data-stu-id="653b6-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="653b6-126">Aby zmienić poziom dostępu formantu, ustaw jego `Modifiers` właściwość **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="653b6-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="653b6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="653b6-127">See also</span></span>

- [<span data-ttu-id="653b6-128">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="653b6-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="653b6-129">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="653b6-129">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="653b6-130">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="653b6-130">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="653b6-131">Instrukcje: Dokowanie formantów na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="653b6-131">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="653b6-132">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="653b6-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="653b6-133">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="653b6-133">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="653b6-134">Przewodnik: Układania Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize</span><span class="sxs-lookup"><span data-stu-id="653b6-134">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
