---
title: 'Instrukcje: Tworzenie gradientu liniowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: 953a1944073a8cb5b19ef072e2a523baec3a5605
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650005"
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="b2613-102">Instrukcje: Tworzenie gradientu liniowego</span><span class="sxs-lookup"><span data-stu-id="b2613-102">How to: Create a Linear Gradient</span></span>
<span data-ttu-id="b2613-103">GDI + zapewnia poziomej, pionowej i ukośne gradienty liniowe.</span><span class="sxs-lookup"><span data-stu-id="b2613-103">GDI+ provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="b2613-104">Domyślnie w przypadku gradientu liniowego zmienia kolor równomiernie.</span><span class="sxs-lookup"><span data-stu-id="b2613-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="b2613-105">Można jednak dostosować gradientu liniowego, tak, aby zmienia kolor w sposób obsługuje technologię niejednolitego.</span><span class="sxs-lookup"><span data-stu-id="b2613-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  

> [!NOTE]
> <span data-ttu-id="b2613-106">Przykłady w niniejszym artykule są metody, które są wywoływane z poziomu kontroli <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b2613-106">The examples in this article are methods that are called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  

<span data-ttu-id="b2613-107">Poniższy przykład wypełnia linię, elipsę i prostokąt o poziomie pędzel gradientów liniowych.</span><span class="sxs-lookup"><span data-stu-id="b2613-107">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
<span data-ttu-id="b2613-108"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktor odbiera cztery argumenty: dwa punkty i dwóch kolorów.</span><span class="sxs-lookup"><span data-stu-id="b2613-108">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="b2613-109">Pierwszy punkt (0, 10) jest skojarzona z pierwszy kolor (czerwony), a drugi punkt (200, 10) jest skojarzony z drugi kolor (niebieski).</span><span class="sxs-lookup"><span data-stu-id="b2613-109">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="b2613-110">Jak można oczekiwać, wiersz z (0, 10) do (200, 10) stopniowo zmienia się z kolor czerwony, niebieski.</span><span class="sxs-lookup"><span data-stu-id="b2613-110">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="b2613-111">10s w punktach (0, 10) i (200, 10) nie są ważne.</span><span class="sxs-lookup"><span data-stu-id="b2613-111">The 10s in the points (0, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="b2613-112">Co to jest ważne jest, czy dwa punkty mają tę samą współrzędną. drugi — wiersz, łącząc je jest poziomy.</span><span class="sxs-lookup"><span data-stu-id="b2613-112">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="b2613-113">Elipsy i prostokąt również zmienić stopniowo kolor czerwony, niebieski, ponieważ pozioma współrzędne przechodzi z zakresu od 0 do 200.</span><span class="sxs-lookup"><span data-stu-id="b2613-113">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="b2613-114">Na poniższej ilustracji przedstawiono wiersza, elipsy i prostokąt.</span><span class="sxs-lookup"><span data-stu-id="b2613-114">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="b2613-115">Należy pamiętać, że kolor gradientu powtarza się, jak pozioma współrzędne przekroczy 200.</span><span class="sxs-lookup"><span data-stu-id="b2613-115">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="b2613-116">![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="b2613-116">![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="b2613-117">Aby użyć poziomy gradientów liniowych</span><span class="sxs-lookup"><span data-stu-id="b2613-117">To use horizontal linear gradients</span></span>  
  
- <span data-ttu-id="b2613-118">Przekaż nieprzezroczyste niebieski czerwonego i nieprzezroczystości jako argument trzecia i czwarta odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b2613-118">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="b2613-119">W powyższym przykładzie kolor zmiany składników liniowo po przeniesieniu pozioma współrzędne 0 Aby pozioma współrzędne 200.</span><span class="sxs-lookup"><span data-stu-id="b2613-119">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="b2613-120">Na przykład punkt, w której Współrzędna pierwszy jest w połowie zakresu od 0 do 200 mają niebieski składnik, który jest w połowie między 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="b2613-120">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 <span data-ttu-id="b2613-121">GDI + pozwala dostosować sposób, w których kolor, który różni się od jednej krawędzi gradientu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="b2613-121">GDI+ allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="b2613-122">Załóżmy, że chcesz utworzyć pędzla gradientu, który zmienia się pomiędzy czarny na czerwony, zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="b2613-122">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="b2613-123">Pozioma współrzędne</span><span class="sxs-lookup"><span data-stu-id="b2613-123">Horizontal coordinate</span></span>|<span data-ttu-id="b2613-124">Składniki RGB</span><span class="sxs-lookup"><span data-stu-id="b2613-124">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="b2613-125">0</span><span class="sxs-lookup"><span data-stu-id="b2613-125">0</span></span>|<span data-ttu-id="b2613-126">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="b2613-126">(0, 0, 0)</span></span>|  
|<span data-ttu-id="b2613-127">40</span><span class="sxs-lookup"><span data-stu-id="b2613-127">40</span></span>|<span data-ttu-id="b2613-128">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="b2613-128">(128, 0, 0)</span></span>|  
|<span data-ttu-id="b2613-129">200</span><span class="sxs-lookup"><span data-stu-id="b2613-129">200</span></span>|<span data-ttu-id="b2613-130">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="b2613-130">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="b2613-131">Należy pamiętać, że składnik czerwony w wysokości równej połowie intensywność podczas pozioma współrzędne jest tylko 20% sposób z zakresu od 0 do 200.</span><span class="sxs-lookup"><span data-stu-id="b2613-131">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="b2613-132">Poniższy przykład ustawia <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> właściwość do skojarzenia z trzech względne natężenia z trzech położenie względne.</span><span class="sxs-lookup"><span data-stu-id="b2613-132">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> property to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="b2613-133">Tak jak w powyższej tabeli względną intensywność 0,5 jest skojarzony z względne położenie 0.2.</span><span class="sxs-lookup"><span data-stu-id="b2613-133">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="b2613-134">Kod wprowadza elipsę i prostokąt z pędzla gradientu.</span><span class="sxs-lookup"><span data-stu-id="b2613-134">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="b2613-135">Na poniższej ilustracji przedstawiono wynikowe elipsy i prostokąt.</span><span class="sxs-lookup"><span data-stu-id="b2613-135">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="b2613-136">![Gradient liniowy](./media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="b2613-136">![Linear Gradient](./media/cslineargradient2.png "cslineargradient2")</span></span>  

### <a name="to-customize-linear-gradients"></a><span data-ttu-id="b2613-137">Aby dostosować gradienty liniowe</span><span class="sxs-lookup"><span data-stu-id="b2613-137">To customize linear gradients</span></span>  
  
- <span data-ttu-id="b2613-138">Przekaż nieprzezroczyste red czarne i nieprzezroczystości jako argument trzecia i czwarta odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b2613-138">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="b2613-139">Gradienty w powyższych przykładach zostały poziomy; oznacza to zmienia kolor stopniowo po przeniesieniu wzdłuż dowolnej linii poziomej.</span><span class="sxs-lookup"><span data-stu-id="b2613-139">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="b2613-140">Można również zdefiniować gradientów pionowych i gradientów ukośne.</span><span class="sxs-lookup"><span data-stu-id="b2613-140">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="b2613-141">Poniższy przykład przekazuje punkty (0, 0) i (200, 100), aby <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="b2613-141">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="b2613-142">Kolor niebieski jest skojarzony z (0, 0), a kolor zielony jest skojarzony z (200, 100).</span><span class="sxs-lookup"><span data-stu-id="b2613-142">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="b2613-143">Wiersz (przy użyciu szerokości pióro 10) i elipsy są wypełnione pędzel gradientów liniowych.</span><span class="sxs-lookup"><span data-stu-id="b2613-143">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="b2613-144">Na poniższej ilustracji przedstawiono wiersza i elipsy.</span><span class="sxs-lookup"><span data-stu-id="b2613-144">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="b2613-145">Należy pamiętać, kolor zmiany elipsy stopniowo po przeniesieniu wzdłuż żadnego wiersza jest zbliżony do wiersza, przechodzi przez (0, 0) i (200, 100).</span><span class="sxs-lookup"><span data-stu-id="b2613-145">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="b2613-146">![Gradient liniowy](./media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="b2613-146">![Linear Gradient](./media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="b2613-147">Aby utworzyć w użyciu gradientów liniowych</span><span class="sxs-lookup"><span data-stu-id="b2613-147">To create diagonal linear gradients</span></span>  
  
- <span data-ttu-id="b2613-148">Przekaż nieprzezroczyste zielonego nieprzezroczyste i w kolorze niebieskim jako argument trzecia i czwarta, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b2613-148">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="b2613-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2613-149">See also</span></span>

- [<span data-ttu-id="b2613-150">Używanie pędzla gradientów do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="b2613-150">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
- [<span data-ttu-id="b2613-151">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2613-151">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
