---
title: 'Instrukcje: Wypełnianie kafelków w obrębie kształtu obrazem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: ad7b8737a63028e533cadfa6db56b063eb943f22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954929"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="bd833-102">Instrukcje: Wypełnianie kafelków w obrębie kształtu obrazem</span><span class="sxs-lookup"><span data-stu-id="bd833-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="bd833-103">Zgodnie z kafelków mogą być umieszczane obok siebie na pokrycie piętra, prostokątne obrazy mogą być umieszczone obok siebie do wypełnienia kształtu (fragment).</span><span class="sxs-lookup"><span data-stu-id="bd833-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="bd833-104">Na kafelku wewnątrz kształtu, użyj pędzla tekstury.</span><span class="sxs-lookup"><span data-stu-id="bd833-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="bd833-105">Podczas konstruowania <xref:System.Drawing.TextureBrush> obiektu w Argumenty przekazane do konstruktora jest <xref:System.Drawing.Image> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bd833-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="bd833-106">Malowanie wnętrza kształtu przy użyciu pędzli tekstury, kształt zostanie wypełniony powtarzających się kopii tego obrazu.</span><span class="sxs-lookup"><span data-stu-id="bd833-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="bd833-107">Właściwość tryb zawijania <xref:System.Drawing.TextureBrush> obiektu określa, jak obraz, który jest ustawiony jako jest powtarzany w siatce kartezjańskiej.</span><span class="sxs-lookup"><span data-stu-id="bd833-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="bd833-108">Można tworzyć Kafelki w siatce, że ten sam orientacji, czy też mają być obrazu przerzucić od położenia na siatce co do następnego.</span><span class="sxs-lookup"><span data-stu-id="bd833-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="bd833-109">Przerzucanie może być poziome, pionowe lub obu.</span><span class="sxs-lookup"><span data-stu-id="bd833-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="bd833-110">W poniższych przykładach pokazano fragmentacji z różnymi typami Przerzucanie.</span><span class="sxs-lookup"><span data-stu-id="bd833-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="bd833-111">Na kafelku obrazu</span><span class="sxs-lookup"><span data-stu-id="bd833-111">To tile an image</span></span>  
  
- <span data-ttu-id="bd833-112">W tym przykładzie używa na poniższej ilustracji 75 x 75 do kafelka prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="bd833-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="bd833-113">![Tile 1](./media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="bd833-113">![Tile 1](./media/tile1.gif "tile1")</span></span>  
  
- <span data-ttu-id="bd833-114">Poniższa ilustracja przedstawia, jak prostokąta jest rozmieszczany przy użyciu obrazu.</span><span class="sxs-lookup"><span data-stu-id="bd833-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="bd833-115">Należy pamiętać, że wszystkie Kafelki mają tę samą orientację; nie ma żadnych Przerzucanie.</span><span class="sxs-lookup"><span data-stu-id="bd833-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="bd833-116">![Tile 2](./media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="bd833-116">![Tile 2](./media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="bd833-117">Aby przerzucić obraz w poziomie podczas fragmentacji</span><span class="sxs-lookup"><span data-stu-id="bd833-117">To flip an image horizontally while tiling</span></span>  
  
- <span data-ttu-id="bd833-118">W tym przykładzie używa tego samego obrazu 75 x 75 do wypełnienia prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="bd833-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="bd833-119">Tryb zawijania jest ustawiony na przerzucić obraz w poziomie.</span><span class="sxs-lookup"><span data-stu-id="bd833-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="bd833-120">Poniższa ilustracja przedstawia, jak prostokąta jest rozmieszczany przy użyciu obrazu.</span><span class="sxs-lookup"><span data-stu-id="bd833-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="bd833-121">Należy pamiętać, że po przeniesieniu z jednym kafelkiem dalej w danym wierszu obrazu jest odwrócony poziomo.</span><span class="sxs-lookup"><span data-stu-id="bd833-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="bd833-122">![Tile 3](./media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="bd833-122">![Tile 3](./media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="bd833-123">Aby przerzucić obraz w pionie podczas fragmentacji</span><span class="sxs-lookup"><span data-stu-id="bd833-123">To flip an image vertically while tiling</span></span>  
  
- <span data-ttu-id="bd833-124">W tym przykładzie używa tego samego obrazu 75 x 75 do wypełnienia prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="bd833-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="bd833-125">Tryb zawijania jest ustawiony na Przerzuć obraz w pionie.</span><span class="sxs-lookup"><span data-stu-id="bd833-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="bd833-126">Aby przerzucić obraz w pionie i poziomie podczas fragmentacji</span><span class="sxs-lookup"><span data-stu-id="bd833-126">To flip an image horizontally and vertically while tiling</span></span>  
  
- <span data-ttu-id="bd833-127">W tym przykładzie używa tego samego obrazu 75 x 75 do kafelka prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="bd833-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="bd833-128">Tryb zawijania jest ustawiony na przerzucić obraz w poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="bd833-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="bd833-129">Poniższa ilustracja przedstawia, jak prostokąta jest rozmieszczany przez obraz.</span><span class="sxs-lookup"><span data-stu-id="bd833-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="bd833-130">Należy pamiętać, że po przeniesieniu z jednym kafelkiem dalej w danym wierszu obrazu jest odwrócony poziomo i jak przenieść z jednym kafelkiem dalej w danej kolumnie, obraz, który jest odwrócony w pionie.</span><span class="sxs-lookup"><span data-stu-id="bd833-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="bd833-131">![Tile 5](./media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="bd833-131">![Tile 5](./media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="bd833-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd833-132">See also</span></span>

- [<span data-ttu-id="bd833-133">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="bd833-133">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
