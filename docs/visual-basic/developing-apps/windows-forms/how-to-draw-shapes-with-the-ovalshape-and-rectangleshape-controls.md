---
title: 'Porady: rysowanie kształtów za pomocą formantów OvalShape i RectangleShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: f87865ba3aebe5739b87d6ae6bfeaa957af726d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="6f14a-102">Porady: rysowanie kształtów za pomocą formantów OvalShape i RectangleShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6f14a-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="6f14a-103">Można użyć <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> formantu, aby narysować okręgi lub elipsy w formularzu lub kontenera, zarówno w czasie projektowania, jak i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6f14a-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="6f14a-104">Można użyć <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formantu do rysowania kwadratów, prostokąty lub prostokąty z zaokrąglonymi narożnikami w formularzu lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f14a-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="6f14a-105">Ten formant umożliwia również Rysowanie kształtów zarówno w czasie projektowania, jak i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6f14a-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="6f14a-106">Można dostosować wygląd kształtu, zmieniając szerokości, kolorów i styl obramowania.</span><span class="sxs-lookup"><span data-stu-id="6f14a-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="6f14a-107">Tło kształt jest niewidoczny domyślnie; można dostosować do wyświetlenia pełnego koloru, wzorzec, wypełnienia gradientowego (Przechodzenie z jednego koloru do innego) lub obrazu tła.</span><span class="sxs-lookup"><span data-stu-id="6f14a-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="6f14a-108">Aby narysować kształt proste w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="6f14a-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="6f14a-109">Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> lub <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kontrolować z **Visual Basic PowerPacks** kartę (Aby zainstalować, zobacz [formantów Powerpack Visual Basic](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) w **przybornika** formularz lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6f14a-110">Przeciągnij zmiany rozmiaru i Przenieś dojścia do rozmiaru i pozycji kształtu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="6f14a-111">Możesz również rozmiar i położenie kształtu, zmieniając `Size` i `Position` właściwości w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="6f14a-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="6f14a-112">Aby utworzyć prostokąt z zaokrąglonymi narożnikami, wybierz `CornerRadius` właściwości w **właściwości** okna i ustaw ją na wartość, która jest większa niż 0.</span><span class="sxs-lookup"><span data-stu-id="6f14a-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="6f14a-113">W **właściwości** okna, opcjonalnie zestaw dodatkowe właściwości, aby zmienić wygląd kształtu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="6f14a-114">Aby narysować kształt proste w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="6f14a-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="6f14a-115">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="6f14a-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="6f14a-116">W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Microsoft.VisualBasic.PowerPacks.VS**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f14a-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6f14a-117">W **edytora kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:</span><span class="sxs-lookup"><span data-stu-id="6f14a-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="6f14a-118">Dodaj następujący kod w `Event` procedury:</span><span class="sxs-lookup"><span data-stu-id="6f14a-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="6f14a-119">Dostosowywanie kształtów</span><span class="sxs-lookup"><span data-stu-id="6f14a-119">Customizing Shapes</span></span>  
 <span data-ttu-id="6f14a-120">Korzystając z ustawienia domyślne <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> i <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> formanty są wyświetlane z stałe czarnym obramowaniem jeden piksel szerokości i przezroczyste tło.</span><span class="sxs-lookup"><span data-stu-id="6f14a-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="6f14a-121">Przez ustawienie właściwości można zmienić szerokości, stylu i koloru obramowania.</span><span class="sxs-lookup"><span data-stu-id="6f14a-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="6f14a-122">Dodatkowe właściwości umożliwiają zmianę tła kształtów jednolitym kolorem, wzorzec, wypełnieniem gradientowym lub obrazu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="6f14a-123">Przed wprowadzeniem zmian w tle kształtu, należy poznać kilka właściwości interakcje.</span><span class="sxs-lookup"><span data-stu-id="6f14a-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="6f14a-124"><xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Ustawienie właściwości nie obowiązuje, chyba że <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="6f14a-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="6f14a-125">Jeśli <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> zastępuje <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f14a-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="6f14a-126">Jeśli <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> właściwość ma ustawioną wartość wzorca takich jak <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> lub <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, wzorzec zostanie wyświetlona w <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f14a-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="6f14a-127">Tło będą wyświetlane w <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, pod warunkiem że <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="6f14a-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="6f14a-128">Aby wyświetlić wypełnienia gradientowego <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> musi mieć ustawioną właściwość <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> i <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> właściwość musi mieć ustawioną wartość innych niż <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="6f14a-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="6f14a-129">Ustawienie <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> właściwość do obrazu zastępuje wszystkie inne ustawienia tła.</span><span class="sxs-lookup"><span data-stu-id="6f14a-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="6f14a-130">Aby narysować okrąg, który ma obramowanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6f14a-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="6f14a-131">Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6f14a-132">W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6f14a-133">Ustaw `BorderColor` kolor, który chcesz dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="6f14a-134">Ustaw `BorderStyle` właściwości wartości innych niż `Solid`.</span><span class="sxs-lookup"><span data-stu-id="6f14a-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="6f14a-135">Ustaw `BorderWidth` rozmiar w pikselach.</span><span class="sxs-lookup"><span data-stu-id="6f14a-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="6f14a-136">Aby narysować koło z wypełnieniem</span><span class="sxs-lookup"><span data-stu-id="6f14a-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="6f14a-137">Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6f14a-138">W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6f14a-139">Ustaw `BackColor` kolor, który chcesz dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="6f14a-140">Ustaw `BackStyle` właściwości `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="6f14a-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="6f14a-141">Aby narysować okrąg deseniem wypełnieniem</span><span class="sxs-lookup"><span data-stu-id="6f14a-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="6f14a-142">Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6f14a-143">W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6f14a-144">Ustaw `BackColor` kolor tła dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="6f14a-145">Ustaw `BackStyle` właściwości `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="6f14a-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="6f14a-146">Ustaw `FillColor` kolor, który ma wzorca dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="6f14a-147">Ustaw `FillStyle` właściwości wartości innych niż `Transparent` lub `Solid`.</span><span class="sxs-lookup"><span data-stu-id="6f14a-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="6f14a-148">Aby narysować koło z wypełnieniem gradientowym</span><span class="sxs-lookup"><span data-stu-id="6f14a-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="6f14a-149">Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6f14a-150">W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6f14a-151">Ustaw `FillColor` kolor kolor początkowy dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="6f14a-152">Ustaw `FillGradientColor` kolor końcowy kolor dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="6f14a-153">Ustaw `FillGradientStyle` właściwości na wartość inną niż `None`.</span><span class="sxs-lookup"><span data-stu-id="6f14a-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="6f14a-154">Rysowanie wypełnionej obrazu okręgu</span><span class="sxs-lookup"><span data-stu-id="6f14a-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="6f14a-155">Przeciągnij `OvalShape` kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6f14a-156">W **właściwości** okna w `Size` właściwość, ustaw `Height` i `Width` równe wartości.</span><span class="sxs-lookup"><span data-stu-id="6f14a-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6f14a-157">Wybierz `BackgroundImage` właściwości i kliknij przycisk **wielokropka** przycisk (...).</span><span class="sxs-lookup"><span data-stu-id="6f14a-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="6f14a-158">W **zasobów wybierz** okno dialogowe, wybierz obraz do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="6f14a-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="6f14a-159">Jeśli nie są wyświetlane nie zasoby obrazów, kliknij przycisk **importu** aby przejść do lokalizacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="6f14a-160">Kliknij przycisk **OK** do wstawiania obrazu.</span><span class="sxs-lookup"><span data-stu-id="6f14a-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f14a-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f14a-161">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [<span data-ttu-id="6f14a-162">Linie i kształty — Wprowadzenie do kontrolek</span><span class="sxs-lookup"><span data-stu-id="6f14a-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="6f14a-163">Instrukcje: rysowanie linii za pomocą kontrolki LineShape</span><span class="sxs-lookup"><span data-stu-id="6f14a-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
