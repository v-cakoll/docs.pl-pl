---
title: 'Porady: tworzenie gradientu liniowego'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbf3b1657a5a6b91ba88a0968b6b92d4e4bdbf0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="e1e4f-102">Porady: tworzenie gradientu liniowego</span><span class="sxs-lookup"><span data-stu-id="e1e4f-102">How to: Create a Linear Gradient</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e1e4f-103">udostępnia pozioma, pionowych i ukośnych gradienty liniowe.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-103"> provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="e1e4f-104">Domyślnie w przypadku gradientu liniowego zmienia kolor jednakowo.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="e1e4f-105">Można jednak dostosować gradientu liniowego tak, aby w sposób niejednolitego zmienia kolor.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  
  
 <span data-ttu-id="e1e4f-106">Poniższy przykład wypełnia linii, elipsy i prostokąt o poziomie pędzla gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-106">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
 <span data-ttu-id="e1e4f-107"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktor odbiera cztery argumenty: dwa punkty i dwa kolory.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-107">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="e1e4f-108">Pierwszy punkt (0, 10) jest skojarzona z pierwszego koloru (czerwony), a drugi punkt (200, 10) jest skojarzona z drugi kolor (niebieski).</span><span class="sxs-lookup"><span data-stu-id="e1e4f-108">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="e1e4f-109">Jak można oczekiwać, wiersz z (0, 10) do (200, 10) zmieni się stopniowo z kolor czerwony, niebieski.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-109">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="e1e4f-110">10s w punktach (50, 10) i (200, 10) nie są ważne.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-110">The 10s in the points (50, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="e1e4f-111">Co to jest ważne jest, że dwa punkty ma tę samą współrzędną. drugi — wiersz, łącząc je jest poziomy.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-111">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="e1e4f-112">Elipsy i prostokąt również zmienić stopniowo kolor czerwony, niebieski, ponieważ Współrzędna pozioma przechodzi od 0 do 200.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-112">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="e1e4f-113">Na poniższej ilustracji przedstawiono wiersza, elipsy i prostokąta.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-113">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="e1e4f-114">Należy pamiętać, że kolor gradientu powtarza się, jak współrzędnych poziomych przekroczy 200.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-114">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="e1e4f-115">![Gradient liniowy](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="e1e4f-115">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="e1e4f-116">Aby użyć poziome gradienty liniowe</span><span class="sxs-lookup"><span data-stu-id="e1e4f-116">To use horizontal linear gradients</span></span>  
  
-   <span data-ttu-id="e1e4f-117">Przekaż nieprzezroczyste niebiesko czerwona i przezroczystości jako trzeci i czwarty argument odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-117">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="e1e4f-118">W powyższym przykładzie kolor zmiany składników liniowo podczas przenoszenia z poziome współrzędną 0 poziome współrzędną 200.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-118">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="e1e4f-119">Na przykład punkt, w których pierwszy współrzędnych jest w połowie zakresu od 0 do 200 ma niebieski składnik, który jest w połowie pomiędzy 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-119">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e1e4f-120">Pozwala dopasować sposób kolor zależą od jednej krawędzi gradientu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-120"> allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="e1e4f-121">Załóżmy, że chcesz utworzyć pędzla gradientu, który zmienia się z czarnym czerwony zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-121">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="e1e4f-122">Współrzędna pozioma</span><span class="sxs-lookup"><span data-stu-id="e1e4f-122">Horizontal coordinate</span></span>|<span data-ttu-id="e1e4f-123">Składniki RGB</span><span class="sxs-lookup"><span data-stu-id="e1e4f-123">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="e1e4f-124">0</span><span class="sxs-lookup"><span data-stu-id="e1e4f-124">0</span></span>|<span data-ttu-id="e1e4f-125">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="e1e4f-125">(0, 0, 0)</span></span>|  
|<span data-ttu-id="e1e4f-126">40</span><span class="sxs-lookup"><span data-stu-id="e1e4f-126">40</span></span>|<span data-ttu-id="e1e4f-127">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="e1e4f-127">(128, 0, 0)</span></span>|  
|<span data-ttu-id="e1e4f-128">200</span><span class="sxs-lookup"><span data-stu-id="e1e4f-128">200</span></span>|<span data-ttu-id="e1e4f-129">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="e1e4f-129">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="e1e4f-130">Należy pamiętać, że składnik red w połowie intensywność przy poziomie Współrzędna jest tylko 20% sposób z zakresu od 0 do 200.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-130">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="e1e4f-131">W poniższym przykładzie <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> właściwość <xref:System.Drawing.Drawing2D.LinearGradientBrush> obiektu trzy względne natężenia z trzech położenia.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-131">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> property of a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="e1e4f-132">W powyższej tabeli względną intensywność 0,5 jest skojarzony z względne położenie 0,2.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-132">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="e1e4f-133">Kod wypełnia elipsy i prostokąt z pędzla gradientu.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-133">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="e1e4f-134">Na poniższej ilustracji przedstawiono wynikowy elipsy i prostokąta.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-134">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="e1e4f-135">![Gradient liniowy](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="e1e4f-135">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span></span>  
  
### <a name="to-customize-linear-gradients"></a><span data-ttu-id="e1e4f-136">Aby dostosować gradienty liniowe</span><span class="sxs-lookup"><span data-stu-id="e1e4f-136">To customize linear gradients</span></span>  
  
-   <span data-ttu-id="e1e4f-137">Przekaż nieprzezroczyste czerwone czarne i przezroczystości jako trzeci i czwarty argument odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-137">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="e1e4f-138">Gradienty w powyższych przykładach zostały poziome; oznacza to, że zmienia kolor stopniowo podczas wykonywania czynności dowolnej linii poziomej.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-138">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="e1e4f-139">Można również zdefiniować pionowy gradientach i przekątnej gradientu.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-139">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="e1e4f-140">Poniższy przykład przekazuje punktów (0, 0) i (200, 100) do <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-140">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="e1e4f-141">Kolor niebieski jest skojarzony z (0, 0), i jest skojarzony kolor zielony (200, 100).</span><span class="sxs-lookup"><span data-stu-id="e1e4f-141">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="e1e4f-142">Wiersz (szerokość 10) i elipsy są wypełniane pędzla gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-142">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="e1e4f-143">Na poniższej ilustracji przedstawiono elipsy i wiersza.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-143">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="e1e4f-144">Należy zauważyć, że kolor zmian elipsy stopniowo podczas wykonywania czynności żadnego wiersza jest zbliżony do linii przechodzącej przez (0, 0) i (200, 100).</span><span class="sxs-lookup"><span data-stu-id="e1e4f-144">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="e1e4f-145">![Gradient liniowy](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="e1e4f-145">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="e1e4f-146">Aby utworzyć ukośnych gradienty liniowe</span><span class="sxs-lookup"><span data-stu-id="e1e4f-146">To create diagonal linear gradients</span></span>  
  
-   <span data-ttu-id="e1e4f-147">Przekazywane nieprzezroczyste zielony niebieska i przezroczystości jako trzeci i czwarty argument odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-147">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e1e4f-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1e4f-148">See Also</span></span>  
 [<span data-ttu-id="e1e4f-149">Używanie pędzla gradientów do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="e1e4f-149">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [<span data-ttu-id="e1e4f-150">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e1e4f-150">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
