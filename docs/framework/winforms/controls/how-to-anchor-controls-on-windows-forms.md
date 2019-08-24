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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94fa6fe90e5583a3bfecf376af59d53f6d8528af
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987492"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="1b7fc-102">Instrukcje: Kontrolki kotwicowe na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b7fc-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="1b7fc-103">Jeśli projektujesz formularz, którego użytkownik może zmienić rozmiar w czasie wykonywania, kontrolki w formularzu powinny zmieniać rozmiar i zmienić położenie odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="1b7fc-104">Aby dynamicznie zmieniać rozmiar kontrolek przy użyciu formularza, można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantów Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="1b7fc-105"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwość definiuje pozycję kotwicy dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="1b7fc-106">Gdy kontrolka jest zakotwiczona do formularza i zmieniany jest rozmiar formularza, formant utrzymuje odległość między kontrolką a położeniami zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="1b7fc-107">Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formant, który jest zakotwiczony do lewej, prawej i dolnej krawędzi formularza, w miarę zmieniania rozmiaru <xref:System.Windows.Forms.TextBox> formularza kontrolka zmienia rozmiar w poziomie tak, aby zachować taką samą odległość od prawej i lewej strony formularza.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="1b7fc-108">Ponadto kontrolka sama rozmieszczenie w pionie, tak aby jej lokalizacja była zawsze taka sama jak odległość od dolnej krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="1b7fc-109">Jeśli kontrolka nie jest zakotwiczona i rozmiar formularza zostanie zmieniony, pozycja kontrolki względem krawędzi formularza zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="1b7fc-110"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwość współdziała zwłaściwością<xref:System.Windows.Forms.Control.AutoSize%2A> .</span><span class="sxs-lookup"><span data-stu-id="1b7fc-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="1b7fc-111">Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b7fc-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="1b7fc-112">Zakotwiczenie kontrolki w formularzu</span><span class="sxs-lookup"><span data-stu-id="1b7fc-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="1b7fc-113">W programie Visual Studio Wybierz kontrolkę, którą chcesz zakotwiczyć.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1b7fc-114">Możesz zakotwiczyć wiele kontrolek jednocześnie, naciskając klawisz CTRL, klikając poszczególne kontrolki, aby je zaznaczyć, a następnie postępując zgodnie z resztą tej procedury.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="1b7fc-115">W oknie **Właściwości** kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="1b7fc-116">Wyświetlany jest Edytor, który pokazuje krzyżyk.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="1b7fc-117">Aby ustawić kotwicę, kliknij górną, lewą, prawą lub dolną sekcję krzyżyka.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="1b7fc-118">Kontrolki są domyślnie zakotwiczone na górze i w lewo.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="1b7fc-119">Aby wyczyścić stronę kontrolki, która została zakotwiczenie, kliknij tę ramię krzyżowo.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="1b7fc-120">Aby zamknąć <xref:System.Windows.Forms.Control.Anchor%2A> Edytor właściwości, <xref:System.Windows.Forms.Control.Anchor%2A> kliknij ponownie nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="1b7fc-121">Gdy formularz zostanie wyświetlony w czasie wykonywania, zmienia rozmiar kontrolki tak, aby pozostawał w tej samej odległości od krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="1b7fc-122">Odległość od zakotwiczonej krawędzi zawsze pozostaje taka sama jak odległość zdefiniowana, gdy kontrolka jest umieszczona w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="1b7fc-123">Niektóre kontrolki, takie jak <xref:System.Windows.Forms.ComboBox> kontrolka, mają limit wysokości.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="1b7fc-124">Zakotwiczenie kontrolki do dołu jej formularza lub kontenera nie może wymusić przekroczenia limitu wysokości formantu.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="1b7fc-125">Dziedziczone kontrolki muszą `Protected` mieć możliwość zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="1b7fc-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="1b7fc-126">Aby zmienić poziom dostępu kontrolki, ustaw jej `Modifiers` właściwość w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="1b7fc-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b7fc-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b7fc-127">See also</span></span>

- [<span data-ttu-id="1b7fc-128">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b7fc-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="1b7fc-129">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="1b7fc-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="1b7fc-130">Instrukcje: Zadokuj kontrolki na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b7fc-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="1b7fc-131">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1b7fc-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="1b7fc-132">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1b7fc-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="1b7fc-133">Przewodnik: Określanie układu formantów Windows Forms z dopełnieniem, marginesami i właściwością AutoSize</span><span class="sxs-lookup"><span data-stu-id="1b7fc-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
