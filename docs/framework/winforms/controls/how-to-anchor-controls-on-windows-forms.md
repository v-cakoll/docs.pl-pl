---
title: Kotwiczenie kontrolek
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c307d8c5b3bc32e15e6de048c434854ef1bbc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747181"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="f6324-102">Instrukcje: kontrolki kotwicowe na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6324-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="f6324-103">Jeśli projektujesz formularz, którego użytkownik może zmienić rozmiar w czasie wykonywania, kontrolki w formularzu powinny zmieniać rozmiar i zmienić położenie odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f6324-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="f6324-104">Aby dynamicznie zmieniać rozmiar kontrolek przy użyciu formularza, można użyć właściwości <xref:System.Windows.Forms.Control.Anchor%2A> Windows Forms kontrolek.</span><span class="sxs-lookup"><span data-stu-id="f6324-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="f6324-105">Właściwość <xref:System.Windows.Forms.Control.Anchor%2A> definiuje położenie zakotwiczenia dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f6324-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="f6324-106">Gdy kontrolka jest zakotwiczona do formularza i zmieniany jest rozmiar formularza, formant utrzymuje odległość między kontrolką a położeniami zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="f6324-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="f6324-107">Na przykład jeśli masz formant <xref:System.Windows.Forms.TextBox>, który jest zakotwiczony w lewej, prawej i dolnej części formularza, w miarę zmieniania rozmiaru formularza <xref:System.Windows.Forms.TextBox> kontrolka zmienia rozmiar w poziomie tak, aby zachować taką samą odległość od prawej i lewej strony formularza.</span><span class="sxs-lookup"><span data-stu-id="f6324-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="f6324-108">Ponadto kontrolka sama rozmieszczenie w pionie, tak aby jej lokalizacja była zawsze taka sama jak odległość od dolnej krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="f6324-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="f6324-109">Jeśli kontrolka nie jest zakotwiczona i rozmiar formularza zostanie zmieniony, pozycja kontrolki względem krawędzi formularza zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="f6324-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="f6324-110">Właściwość <xref:System.Windows.Forms.Control.Anchor%2A> współdziała z właściwością <xref:System.Windows.Forms.Control.AutoSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6324-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="f6324-111">Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f6324-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="f6324-112">Zakotwiczenie kontrolki w formularzu</span><span class="sxs-lookup"><span data-stu-id="f6324-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="f6324-113">W programie Visual Studio Wybierz kontrolkę, którą chcesz zakotwiczyć.</span><span class="sxs-lookup"><span data-stu-id="f6324-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f6324-114">Możesz zakotwiczyć wiele kontrolek jednocześnie, naciskając klawisz CTRL, klikając poszczególne kontrolki, aby je zaznaczyć, a następnie postępując zgodnie z resztą tej procedury.</span><span class="sxs-lookup"><span data-stu-id="f6324-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="f6324-115">W oknie **Właściwości** kliknij strzałkę po prawej stronie właściwości <xref:System.Windows.Forms.Control.Anchor%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6324-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="f6324-116">Wyświetlany jest Edytor, który pokazuje krzyżyk.</span><span class="sxs-lookup"><span data-stu-id="f6324-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="f6324-117">Aby ustawić kotwicę, kliknij górną, lewą, prawą lub dolną sekcję krzyżyka.</span><span class="sxs-lookup"><span data-stu-id="f6324-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="f6324-118">Kontrolki są domyślnie zakotwiczone na górze i w lewo.</span><span class="sxs-lookup"><span data-stu-id="f6324-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="f6324-119">Aby wyczyścić stronę kontrolki, która została zakotwiczenie, kliknij tę ramię krzyżowo.</span><span class="sxs-lookup"><span data-stu-id="f6324-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="f6324-120">Aby zamknąć Edytor właściwości <xref:System.Windows.Forms.Control.Anchor%2A>, kliknij ponownie nazwę właściwości <xref:System.Windows.Forms.Control.Anchor%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6324-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="f6324-121">Gdy formularz zostanie wyświetlony w czasie wykonywania, zmienia rozmiar kontrolki tak, aby pozostawał w tej samej odległości od krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="f6324-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="f6324-122">Odległość od zakotwiczonej krawędzi zawsze pozostaje taka sama jak odległość zdefiniowana, gdy kontrolka jest umieszczona w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f6324-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="f6324-123">Niektóre kontrolki, takie jak kontrolka <xref:System.Windows.Forms.ComboBox>, mają limit wysokości.</span><span class="sxs-lookup"><span data-stu-id="f6324-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="f6324-124">Zakotwiczenie kontrolki do dołu jej formularza lub kontenera nie może wymusić przekroczenia limitu wysokości formantu.</span><span class="sxs-lookup"><span data-stu-id="f6324-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="f6324-125">Kontrolki dziedziczone muszą być `Protected`, aby mogły być zakotwiczone.</span><span class="sxs-lookup"><span data-stu-id="f6324-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="f6324-126">Aby zmienić poziom dostępu kontrolki, ustaw jej Właściwość `Modifiers` w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="f6324-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6324-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6324-127">See also</span></span>

- [<span data-ttu-id="f6324-128">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6324-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="f6324-129">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="f6324-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="f6324-130">Instrukcje: dokowanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6324-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="f6324-131">Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f6324-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="f6324-132">Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f6324-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="f6324-133">Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize</span><span class="sxs-lookup"><span data-stu-id="f6324-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
