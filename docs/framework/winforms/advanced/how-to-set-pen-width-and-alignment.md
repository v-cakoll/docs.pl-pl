---
title: "Porady: ustawianie szerokości i wyrównania pióra"
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
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ed2a28c49554c686abb5e2635ab35b746b83465
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="1849b-102">Porady: ustawianie szerokości i wyrównania pióra</span><span class="sxs-lookup"><span data-stu-id="1849b-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="1849b-103">Po utworzeniu <xref:System.Drawing.Pen>, możesz podać szerokość pióra jako jeden z argumentów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1849b-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="1849b-104">Możesz również zmienić szerokość z <xref:System.Drawing.Pen.Width%2A> właściwość <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="1849b-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="1849b-105">Teoretyczna ma szerokość 0.</span><span class="sxs-lookup"><span data-stu-id="1849b-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="1849b-106">Podczas rysowania linii, o szerokości 1 piksela pikseli jest wyśrodkowywana w wierszu teoretycznego.</span><span class="sxs-lookup"><span data-stu-id="1849b-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="1849b-107">Jeśli rysowania więcej niż jeden piksel szerokości linii pikseli albo skupia się na teoretycznego wiersza lub są wyświetlane obok teoretycznego wiersza.</span><span class="sxs-lookup"><span data-stu-id="1849b-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="1849b-108">Można ustawić właściwości wyrównania pióra <xref:System.Drawing.Pen> ustalenie położenie pikseli z tym pióra względem teoretycznego wierszy.</span><span class="sxs-lookup"><span data-stu-id="1849b-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="1849b-109">Wartości <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, i <xref:System.Drawing.Drawing2D.PenAlignment.Inset> znajdujących się na następujące przykłady kodu są elementami członkowskimi <xref:System.Drawing.Drawing2D.PenAlignment> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1849b-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="1849b-110">Poniższy przykładowy kod rysuje dwa razy: raz piórem czarny o szerokości 1 i drugi raz z zielonym pióra szerokości 10.</span><span class="sxs-lookup"><span data-stu-id="1849b-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="1849b-111">Aby zróżnicować szerokość pióra</span><span class="sxs-lookup"><span data-stu-id="1849b-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="1849b-112">Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwości <xref:System.Drawing.Drawing2D.PenAlignment.Center> (ustawienie domyślne) do określenia, że pikseli z zielonym pióro zostanie wyśrodkowany teoretycznego wiersza.</span><span class="sxs-lookup"><span data-stu-id="1849b-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="1849b-113">Na poniższej ilustracji przedstawiono wynikowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="1849b-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="1849b-114">![Pióra](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="1849b-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="1849b-115">Poniższy przykładowy kod rysuje prostokąt dwa razy: raz piórem czarny o szerokości 1 i drugi raz z zielonym pióra szerokości 10.</span><span class="sxs-lookup"><span data-stu-id="1849b-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="1849b-116">Aby zmienić wyrównania pióra</span><span class="sxs-lookup"><span data-stu-id="1849b-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="1849b-117">Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwości <xref:System.Drawing.Drawing2D.PenAlignment.Center> do określenia, że pikseli z zielonym pióra zostaną wyśrodkowane na krawędzi prostokąta.</span><span class="sxs-lookup"><span data-stu-id="1849b-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="1849b-118">Na poniższej ilustracji przedstawiono wynikowy prostokąta.</span><span class="sxs-lookup"><span data-stu-id="1849b-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="1849b-119">![Pióra](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="1849b-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="1849b-120">Aby utworzyć wstawki pióra</span><span class="sxs-lookup"><span data-stu-id="1849b-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="1849b-121">Zmienić wyrównania pióra zielony, modyfikując trzeci instrukcji w poprzednim przykładzie kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1849b-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="1849b-122">Teraz pikseli szerokości zielony wiersza pojawiają się wewnątrz prostokąta, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="1849b-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="1849b-123">![Pióra](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="1849b-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1849b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1849b-124">See Also</span></span>  
 [<span data-ttu-id="1849b-125">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="1849b-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="1849b-126">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1849b-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
