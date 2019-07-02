---
title: 'Instrukcje: Stosowanie macierzy kolorów do transformacji pojedynczego koloru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 2df74e022b842f7e5c9ff80f6aeddfce51af5eab
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505815"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="183a4-102">Instrukcje: Stosowanie macierzy kolorów do transformacji pojedynczego koloru</span><span class="sxs-lookup"><span data-stu-id="183a4-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
<span data-ttu-id="183a4-103">GDI + zapewnia <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> klasy do przechowywania i manipulowania obrazami.</span><span class="sxs-lookup"><span data-stu-id="183a4-103">GDI+ provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="183a4-104"><xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> obiektów przechowywać kolor każdego piksela jako wartość liczby 32-bitowej: 8 bitów na każdy czerwony, zielony, niebieski i alfa.</span><span class="sxs-lookup"><span data-stu-id="183a4-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="183a4-105">Każdy z czterech składników jest liczba z przedziału od 0 do 255, od 0, reprezentujących natężenie i 255 reprezentujący pełnej intensywności.</span><span class="sxs-lookup"><span data-stu-id="183a4-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="183a4-106">Składnik alfa określa Przezroczystość koloru: 0 jest w pełni przezroczyste, a 255 jest całkowicie nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="183a4-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="183a4-107">Wektor kolorów jest 4-krotka formularza (czerwony, zielony, niebieski, alfa).</span><span class="sxs-lookup"><span data-stu-id="183a4-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="183a4-108">Na przykład wektor kolorów (0, 255, 0, 255) reprezentuje nieprzezroczyste kolor, który nie ma czerwony lub niebieski, ale ma kolor zielony w pełnej intensywności.</span><span class="sxs-lookup"><span data-stu-id="183a4-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="183a4-109">Inną konwencję reprezentująca kolorów używa numer 1 do pełnej intensywności.</span><span class="sxs-lookup"><span data-stu-id="183a4-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="183a4-110">Przy użyciu Konwencji, kolor, który został opisany w poprzednim akapicie jest przedstawiany przez vector (0, 1, 0, 1).</span><span class="sxs-lookup"><span data-stu-id="183a4-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> <span data-ttu-id="183a4-111">GDI + jest używana konwencja 1 jako pełnej intensywności, gdy wykonuje transformacji kolorów.</span><span class="sxs-lookup"><span data-stu-id="183a4-111">GDI+ uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="183a4-112">Linear — przekształcenia (obrotu, skalowanie i podobne) można stosować do wektorów kolorów, poprzez pomnożenie wektorów kolorów w macierzy 4 x 4.</span><span class="sxs-lookup"><span data-stu-id="183a4-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="183a4-113">Jednak nie można używać macierzy 4 x 4, aby wykonać tłumaczenie (nieliniowych).</span><span class="sxs-lookup"><span data-stu-id="183a4-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="183a4-114">Jeśli dodasz fikcyjnego współrzędnych piąty (na przykład numer 1) do każdego wektorów kolor, można użyć macierzy 5 × 5 można zastosować dowolną kombinację linear — przekształcenia i tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="183a4-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="183a4-115">Przekształcenie składający się z liniowego transformacji, następuje tłumaczenia jest wywoływana affine — przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="183a4-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="183a4-116">Na przykład załóżmy, że chcesz rozpocząć z kolorem (0.2 0.0, 0,4, 1.0) i stosuje się następujące przekształcenia:</span><span class="sxs-lookup"><span data-stu-id="183a4-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1. <span data-ttu-id="183a4-117">Double składnik czerwony</span><span class="sxs-lookup"><span data-stu-id="183a4-117">Double the red component</span></span>  
  
2. <span data-ttu-id="183a4-118">Dodaj wymagane 0,2 dla składników czerwonego, zielonego i niebieskiego</span><span class="sxs-lookup"><span data-stu-id="183a4-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="183a4-119">Następujące mnożenie macierzy wykona pary przekształcenia w podanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="183a4-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 ![Zrzut ekranu przedstawiający mnożenie macierzy transformacji.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/multiplication-color-matrix.gif)
  
 <span data-ttu-id="183a4-121">Elementów macierzy kolorów są indeksowane (liczony od zera), wiersz, a następnie kolumny.</span><span class="sxs-lookup"><span data-stu-id="183a4-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="183a4-122">Na przykład wpis w piątym wierszu, a trzecia kolumna macierzy M jest oznaczona M [4] [2].</span><span class="sxs-lookup"><span data-stu-id="183a4-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="183a4-123">5 x 5 macierzą (pokazane na poniższej ilustracji) ma 1s na przekątnej i 0s wszędzie, gdzie else.</span><span class="sxs-lookup"><span data-stu-id="183a4-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="183a4-124">Jeśli wektor kolor mnożenia macierz tożsamości, vector kolorów nie zmienia się.</span><span class="sxs-lookup"><span data-stu-id="183a4-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="183a4-125">Wygodny sposób do utworzenia macierzy transformacji kolorów jest rozpoczynać macierz tożsamości i wprowadź niewielką zmianę, który produkuje żądane transformacje.</span><span class="sxs-lookup"><span data-stu-id="183a4-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 ![Zrzut ekranu przedstawiający macierz tożsamości 5 x 5 dla transformacji kolorów.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/5x5-identity-matrix-color-transformation.gif)  
  
 <span data-ttu-id="183a4-127">Bardziej szczegółowe omówienie macierzy, a przekształcenia zobacz [systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="183a4-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="183a4-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="183a4-128">Example</span></span>  
 <span data-ttu-id="183a4-129">Poniższy przykład pobiera obraz, który jest w jednym kolorze (0.2 0.0, 0,4, 1.0) i stosuje przekształcenia opisanych w poprzednich akapitach.</span><span class="sxs-lookup"><span data-stu-id="183a4-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="183a4-130">Poniższa ilustracja pokazuje oryginalny obraz po lewej stronie i przekształcone obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="183a4-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 ![Purpurowa kwadratowy po lewej i kwadrat fuksja po prawej stronie.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/color-transformation.png)  
  
 <span data-ttu-id="183a4-132">Kod w poniższym przykładzie używa następujące kroki, aby wykonać ponowne kolorowanie:</span><span class="sxs-lookup"><span data-stu-id="183a4-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1. <span data-ttu-id="183a4-133">Inicjowanie <xref:System.Drawing.Imaging.ColorMatrix> obiektu.</span><span class="sxs-lookup"><span data-stu-id="183a4-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2. <span data-ttu-id="183a4-134">Tworzenie <xref:System.Drawing.Imaging.ImageAttributes> i przekazać <xref:System.Drawing.Imaging.ColorMatrix> obiekt <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu.</span><span class="sxs-lookup"><span data-stu-id="183a4-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3. <span data-ttu-id="183a4-135">Przekaż <xref:System.Drawing.Imaging.ImageAttributes> obiekt <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="183a4-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="183a4-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="183a4-136">Compiling the Code</span></span>  
 <span data-ttu-id="183a4-137">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="183a4-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183a4-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="183a4-138">See also</span></span>

- [<span data-ttu-id="183a4-139">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="183a4-139">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="183a4-140">Systemy i przekształcenia współrzędnych</span><span class="sxs-lookup"><span data-stu-id="183a4-140">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
