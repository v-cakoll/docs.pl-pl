---
title: "Porady: obracanie kolorów"
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
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81b022011bd5613b8e956aa83482d2836508a4f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="0354d-102">Porady: obracanie kolorów</span><span class="sxs-lookup"><span data-stu-id="0354d-102">How to: Rotate Colors</span></span>
<span data-ttu-id="0354d-103">Obrót w miejscu color czterowymiarowego jest trudne do wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="0354d-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="0354d-104">Firma Microsoft może ułatwić do wizualizacji obrotu zgadzając się do jednego ze składników kolor stałej zachowania.</span><span class="sxs-lookup"><span data-stu-id="0354d-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="0354d-105">Załóżmy, że firma Microsoft Zgadzam się składnika alfa ustalona na 1 (całkowicie nieprzezroczyste).</span><span class="sxs-lookup"><span data-stu-id="0354d-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="0354d-106">Firma Microsoft następnie wizualizacji przestrzeni trójwymiarowej koloru z czerwonym, zielonemu i niebieskiemu osi, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="0354d-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="0354d-107">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="0354d-107">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="0354d-108">Kolor można traktować jako punktu 3-miejsca.</span><span class="sxs-lookup"><span data-stu-id="0354d-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="0354d-109">Na przykład punkt (1, 0, 0), w miejsce reprezentuje kolor czerwony, a punkt (0, 1, 0), w miejsce reprezentuje kolor zielony.</span><span class="sxs-lookup"><span data-stu-id="0354d-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="0354d-110">Na poniższej ilustracji przedstawiono co obracanie kolorów (1, 0, 0) oznacza się pod kątem 60 stopni na płaszczyźnie czerwony zielony.</span><span class="sxs-lookup"><span data-stu-id="0354d-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="0354d-111">Obracanie równolegle płaszczyzny płaszczyzny czerwony zielony można traktować jako obrót wokół osi niebieski.</span><span class="sxs-lookup"><span data-stu-id="0354d-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="0354d-112">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="0354d-112">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="0354d-113">Na poniższej ilustracji przedstawiono sposób inicjowania macierzy kolorów do wykonania obrotów o poszczególnych trzy osie współrzędnych (czerwony, zielony, niebieski).</span><span class="sxs-lookup"><span data-stu-id="0354d-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="0354d-114">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="0354d-114">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="0354d-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0354d-115">Example</span></span>  
 <span data-ttu-id="0354d-116">Poniższy przykład przyjmuje obrazu, który jest jeden kolor (1, 0, 0,6) i stosuje 60 stopni niebieski osi.</span><span class="sxs-lookup"><span data-stu-id="0354d-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="0354d-117">Kąt obrotu przechwytywana wychodzących na płaszczyźnie jest zbliżony do płaszczyzny czerwony zielony.</span><span class="sxs-lookup"><span data-stu-id="0354d-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="0354d-118">Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej i obracać kolor obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0354d-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="0354d-119">![Obracanie kolorów](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="0354d-119">![Rotate Colors](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="0354d-120">Na poniższej ilustracji przedstawiono wizualizację obracanie kolorów wykonywane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0354d-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="0354d-121">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="0354d-121">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0354d-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0354d-122">Compiling the Code</span></span>  
 <span data-ttu-id="0354d-123">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0354d-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="0354d-124">Zastąp `RotationInput.bmp` z nazwą pliku obrazu i ścieżki jest prawidłowy w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="0354d-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0354d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0354d-125">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="0354d-126">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0354d-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="0354d-127">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="0354d-127">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
