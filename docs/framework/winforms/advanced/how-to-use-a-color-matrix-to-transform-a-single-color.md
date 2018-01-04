---
title: "Porady: stosowanie macierzy kolorów do przekształcenia pojedynczego koloru"
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
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6c9273102dc8e8f0fe6be3e31d0f0b6e570c7af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="7f66f-102">Porady: stosowanie macierzy kolorów do przekształcenia pojedynczego koloru</span><span class="sxs-lookup"><span data-stu-id="7f66f-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="7f66f-103">udostępnia <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> klasy do przechowywania i manipulowanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="7f66f-103"> provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="7f66f-104"><xref:System.Drawing.Image>i <xref:System.Drawing.Bitmap> obiektów przechowywania koloru każdego piksela jako 32-bitową liczbą: 8, usługa bits dla czerwony, zielony, niebieski i alfa.</span><span class="sxs-lookup"><span data-stu-id="7f66f-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="7f66f-105">Każdy z czterech składników jest liczba z przedziału od 0 do 255, gdzie 0 reprezentujący natężenie i 255 reprezentujący intensywność pełna.</span><span class="sxs-lookup"><span data-stu-id="7f66f-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="7f66f-106">Określa przezroczystość koloru, składnika alfa: 0 jest w pełni przezroczyste, i jest całkowicie nieprzezroczyste 255.</span><span class="sxs-lookup"><span data-stu-id="7f66f-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="7f66f-107">Wektor kolor jest 4-krotka formularza (czerwony, zielony, niebieski, alfa).</span><span class="sxs-lookup"><span data-stu-id="7f66f-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="7f66f-108">Na przykład wektor kolor (0, 255, 0, 255) reprezentuje nieprzezroczyste kolor, który nie ma czerwony ani blue, ale ma zielony pełna intensywność.</span><span class="sxs-lookup"><span data-stu-id="7f66f-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="7f66f-109">Inny Konwencji reprezentujący kolorów używa numer 1 intensywność pełna.</span><span class="sxs-lookup"><span data-stu-id="7f66f-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="7f66f-110">Przy użyciu Konwencji, kolor opisane w poprzednim akapicie jest przedstawiany wektor (0, 1, 0, 1).</span><span class="sxs-lookup"><span data-stu-id="7f66f-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="7f66f-111">używa konwencji 1 jako pełna intensywność podczas wykonywania transformacji kolorów.</span><span class="sxs-lookup"><span data-stu-id="7f66f-111"> uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="7f66f-112">Linear — przekształcenia (obrót, skalowanie i podobne) można zastosować do wektorów kolor przez pomnożenie wektory kolor przez macierz 4 x 4.</span><span class="sxs-lookup"><span data-stu-id="7f66f-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="7f66f-113">Jednak macierzy 4 x 4 nie można używać do wykonywania tłumaczenia (rożne).</span><span class="sxs-lookup"><span data-stu-id="7f66f-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="7f66f-114">Jeśli dodasz fikcyjnymi współrzędnych piąty (na przykład numer 1) do każdego z kierunków kolor umożliwia macierzy 5 x 5 zastosować dowolną kombinację linear — przekształcenia i tłumaczeń.</span><span class="sxs-lookup"><span data-stu-id="7f66f-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="7f66f-115">Przekształcenie składające się z transformację liniowej następuje translacja jest nazywany affine — przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="7f66f-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="7f66f-116">Na przykład załóżmy, że chcesz uruchomić z kolorem (0,2, 0.0, 0,4, 1.0) i stosuje się następujące przekształcenia:</span><span class="sxs-lookup"><span data-stu-id="7f66f-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1.  <span data-ttu-id="7f66f-117">Podwójna składnika czerwony</span><span class="sxs-lookup"><span data-stu-id="7f66f-117">Double the red component</span></span>  
  
2.  <span data-ttu-id="7f66f-118">Dodaj 0,2 czerwony, zielonemu i niebieskiemu składników</span><span class="sxs-lookup"><span data-stu-id="7f66f-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="7f66f-119">Następujące mnożenie macierzy wykona pary przekształcenia w podanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="7f66f-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="7f66f-120">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="7f66f-120">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="7f66f-121">Elementy tablicy kolorów są indeksowane (liczony od zera) wiersza i kolumny.</span><span class="sxs-lookup"><span data-stu-id="7f66f-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="7f66f-122">Na przykład wpis w wierszu piątym i trzecia kolumna macierzy M jest oznaczona M [4] [2].</span><span class="sxs-lookup"><span data-stu-id="7f66f-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="7f66f-123">5 x 5 macierzą (pokazano na poniższej ilustracji) ma 1s na przekątnej i 0s wszędzie else.</span><span class="sxs-lookup"><span data-stu-id="7f66f-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="7f66f-124">Jeśli wektor kolor pomnożenia macierzą, vector kolor nie zmienia się.</span><span class="sxs-lookup"><span data-stu-id="7f66f-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="7f66f-125">To wygodny sposób na formularzu macierzy transformacji kolorów jest rozpocząć z macierzą i wprowadzić niewielkie zmiany tworzącego żądaną transformacji.</span><span class="sxs-lookup"><span data-stu-id="7f66f-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="7f66f-126">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="7f66f-126">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="7f66f-127">Bardziej szczegółowe omówienie macierzy i przekształcenia, zobacz [systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="7f66f-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f66f-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f66f-128">Example</span></span>  
 <span data-ttu-id="7f66f-129">Poniższy przykład przyjmuje obrazu, który jest jeden kolor (0,2, 0.0, 0,4, 1.0) i stosuje transformację opisane w poprzednim akapicie.</span><span class="sxs-lookup"><span data-stu-id="7f66f-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="7f66f-130">Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i przekształcony obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="7f66f-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="7f66f-131">![Kolory](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="7f66f-131">![Colors](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="7f66f-132">Kod w poniższym przykładzie przeprowadzić ponowne kolorowanie korzysta z następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7f66f-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1.  <span data-ttu-id="7f66f-133">Inicjowanie <xref:System.Drawing.Imaging.ColorMatrix> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7f66f-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2.  <span data-ttu-id="7f66f-134">Utwórz <xref:System.Drawing.Imaging.ImageAttributes> obiektu i przekazać <xref:System.Drawing.Imaging.ColorMatrix> do obiektu <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7f66f-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3.  <span data-ttu-id="7f66f-135">Przekaż <xref:System.Drawing.Imaging.ImageAttributes> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7f66f-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f66f-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7f66f-136">Compiling the Code</span></span>  
 <span data-ttu-id="7f66f-137">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7f66f-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f66f-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f66f-138">See Also</span></span>  
 [<span data-ttu-id="7f66f-139">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="7f66f-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="7f66f-140">Systemy i przekształcenia współrzędnych</span><span class="sxs-lookup"><span data-stu-id="7f66f-140">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
