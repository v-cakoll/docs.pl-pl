---
title: "Porady: wypełnianie kafelków w obrębie kształtu obrazem"
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
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f825371d3849e96ace627e660fd7c59bd290185
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="5cf46-102">Porady: wypełnianie kafelków w obrębie kształtu obrazem</span><span class="sxs-lookup"><span data-stu-id="5cf46-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="5cf46-103">Tak samo, jak kafelki mogą być umieszczone obok siebie, aby pokrywał piętra, prostokątne obrazów mogą być umieszczone obok siebie do wypełnienia kształtu (kafelka).</span><span class="sxs-lookup"><span data-stu-id="5cf46-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="5cf46-104">Na kafelku wewnątrz kształtu, użyj pędzla tekstury.</span><span class="sxs-lookup"><span data-stu-id="5cf46-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="5cf46-105">Podczas konstruowania <xref:System.Drawing.TextureBrush> obiektu, jeden z argumentów przekazać do konstruktora jest <xref:System.Drawing.Image> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cf46-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="5cf46-106">Pędzel tekstury umożliwia malowanie wnętrza kształtu, kształt jest wypełniony powtarzane kopii tego obrazu.</span><span class="sxs-lookup"><span data-stu-id="5cf46-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="5cf46-107">Właściwość tryb zawijania <xref:System.Drawing.TextureBrush> obiektu określa, jak obraz jest ustawiony jako jest powtarzany w siatce prostokątny.</span><span class="sxs-lookup"><span data-stu-id="5cf46-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="5cf46-108">Możesz wprowadzić Kafelki w siatce, że tę samą orientację, można też obrazów Przerzucanie od położenia siatki co do następnego.</span><span class="sxs-lookup"><span data-stu-id="5cf46-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="5cf46-109">Przerzucanie może być poziomo, pionowy lub oba.</span><span class="sxs-lookup"><span data-stu-id="5cf46-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="5cf46-110">W poniższych przykładach pokazano kafelków z różnymi typami Przerzucanie.</span><span class="sxs-lookup"><span data-stu-id="5cf46-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="5cf46-111">Na kafelku obrazu</span><span class="sxs-lookup"><span data-stu-id="5cf46-111">To tile an image</span></span>  
  
-   <span data-ttu-id="5cf46-112">W tym przykładzie używane na poniższej ilustracji 75 x 75 na kafelku prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="5cf46-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="5cf46-113">![Kafelek 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="5cf46-113">![Tile 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="5cf46-114">Na poniższej ilustracji przedstawiono sposób wypełniania prostokąt z obrazem.</span><span class="sxs-lookup"><span data-stu-id="5cf46-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="5cf46-115">Należy zauważyć, że wszystkie Kafelki tę samą orientację; nie ma żadnych Przerzucanie.</span><span class="sxs-lookup"><span data-stu-id="5cf46-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="5cf46-116">![Kafelek 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="5cf46-116">![Tile 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="5cf46-117">Aby odwrócić obraz poziomo podczas kafelków</span><span class="sxs-lookup"><span data-stu-id="5cf46-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="5cf46-118">W tym przykładzie ten sam obraz x 75 75 są używane do wypełnienia prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="5cf46-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="5cf46-119">Tryb zawijania jest ustawiony na poziomie Przerzucanie obrazu.</span><span class="sxs-lookup"><span data-stu-id="5cf46-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="5cf46-120">Na poniższej ilustracji przedstawiono sposób wypełniania prostokąt z obrazem.</span><span class="sxs-lookup"><span data-stu-id="5cf46-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="5cf46-121">Należy pamiętać, że podczas przenoszenia z jednego fragmentu do następnego wiersza danego obrazu jest odwrócony poziomo.</span><span class="sxs-lookup"><span data-stu-id="5cf46-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="5cf46-122">![Kafelek 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="5cf46-122">![Tile 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="5cf46-123">Aby odwrócić obraz w pionie podczas kafelków</span><span class="sxs-lookup"><span data-stu-id="5cf46-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="5cf46-124">W tym przykładzie ten sam obraz x 75 75 są używane do wypełnienia prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="5cf46-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="5cf46-125">Tryb zawijania jest ustawiony na Przerzuć obraz w pionie.</span><span class="sxs-lookup"><span data-stu-id="5cf46-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="5cf46-126">Aby odwrócić obraz w poziomie i w pionie podczas kafelków</span><span class="sxs-lookup"><span data-stu-id="5cf46-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="5cf46-127">W tym przykładzie używa tego samego obrazu x 75 75 na kafelku prostokąt 200 x 200.</span><span class="sxs-lookup"><span data-stu-id="5cf46-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="5cf46-128">Tryb zawijania jest ustawiony na Przerzucanie obrazu w poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="5cf46-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="5cf46-129">Na poniższej ilustracji przedstawiono sposób wypełniania prostokąt przez obraz.</span><span class="sxs-lookup"><span data-stu-id="5cf46-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="5cf46-130">Należy pamiętać, że jak przejść z jednego fragmentu do drugiego w danym wierszu, obraz jest odwrócony poziomo i jak przenieść z jednego fragmentu do następnego w danej kolumnie, obraz jest odwrócony pionowo.</span><span class="sxs-lookup"><span data-stu-id="5cf46-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="5cf46-131">![Kafelek 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="5cf46-131">![Tile 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="5cf46-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cf46-132">See Also</span></span>  
 [<span data-ttu-id="5cf46-133">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="5cf46-133">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
