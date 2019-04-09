---
title: 'Instrukcje: Ustawianie szerokości i wyrównania pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: bc2ac2587554215ef3b2c2580413fbbb894aa687
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074979"
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="41045-102">Instrukcje: Ustawianie szerokości i wyrównania pióra</span><span class="sxs-lookup"><span data-stu-id="41045-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="41045-103">Po utworzeniu <xref:System.Drawing.Pen>, szerokość pióra można podać jako jeden z argumentów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="41045-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="41045-104">Możesz również zmienić szerokość z <xref:System.Drawing.Pen.Width%2A> właściwość <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="41045-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="41045-105">Teoretyczna wiersz ma szerokość 0.</span><span class="sxs-lookup"><span data-stu-id="41045-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="41045-106">Po narysowaniu linii, o szerokości 1 piksela, pikseli jest wyśrodkowywana teoretycznych wiersza.</span><span class="sxs-lookup"><span data-stu-id="41045-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="41045-107">Po narysowaniu linii z więcej niż jeden piksel szeroką, piksele albo jest wyśrodkowywana w wierszu teoretycznych lub pojawiają się obok wiersza teoretycznych.</span><span class="sxs-lookup"><span data-stu-id="41045-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="41045-108">Można ustawić właściwości wyrównania pióra <xref:System.Drawing.Pen> Aby ustalić położenie pikseli narysowany przy tym pióra względem teoretycznych wierszy.</span><span class="sxs-lookup"><span data-stu-id="41045-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="41045-109">Wartości <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, i <xref:System.Drawing.Drawing2D.PenAlignment.Inset> są widoczne w następujące przykłady kodu są elementami członkowskimi <xref:System.Drawing.Drawing2D.PenAlignment> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="41045-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="41045-110">Poniższy kod rysuje dwa razy: zielony pióra szerokości 10 raz przy użyciu pióra czarne o szerokości 1 i drugi raz.</span><span class="sxs-lookup"><span data-stu-id="41045-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="41045-111">Aby zmienić jego szerokość pióra</span><span class="sxs-lookup"><span data-stu-id="41045-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="41045-112">Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwość <xref:System.Drawing.Drawing2D.PenAlignment.Center> (ustawienie domyślne) do określenia, czy pikseli z zielonym pióro zostanie tematyka koncentruje się na teoretycznych wiersza.</span><span class="sxs-lookup"><span data-stu-id="41045-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="41045-113">Poniższa ilustracja przedstawia wynikowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="41045-113">The following illustration shows the resulting line.</span></span>  
  
     ![Czarna linia alokowania elastycznego za pomocą Wyróżnij zielony.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-line.gif)  
  
     <span data-ttu-id="41045-115">Poniższy kod rysuje prostokąt dwa razy: zielony pióra szerokości 10 raz przy użyciu pióra czarne o szerokości 1 i drugi raz.</span><span class="sxs-lookup"><span data-stu-id="41045-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="41045-116">Aby zmienić wyrównania pióra</span><span class="sxs-lookup"><span data-stu-id="41045-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="41045-117">Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwości <xref:System.Drawing.Drawing2D.PenAlignment.Center> do określenia, czy pikseli narysować za pomocą pióra zielony będzie wyśrodkowana na krawędzi prostokąta.</span><span class="sxs-lookup"><span data-stu-id="41045-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="41045-118">Na poniższej ilustracji przedstawiono wynikowe prostokąt:</span><span class="sxs-lookup"><span data-stu-id="41045-118">The following illustration shows the resulting rectangle:</span></span>
  
     ![Prostokąt z czarnym alokowania elastycznego wiersze z zielone podświetlenie.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-rectangle.gif)  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="41045-120">Aby utworzyć wstawki pióra</span><span class="sxs-lookup"><span data-stu-id="41045-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="41045-121">Zmienianie wyrównania pióra zielony, modyfikując trzecia instrukcja w powyższym przykładzie kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="41045-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="41045-122">Pikseli szerokości zieloną linią pojawiają się wewnątrz prostokąta jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="41045-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration:</span></span>
  
     ![Prostokąt z czarnym wiersze z szerokiego zieloną linią wewnątrz.](./media/how-to-set-pen-width-and-alignment/green-pixels-inside-rectangle.gif)  
  
## <a name="see-also"></a><span data-ttu-id="41045-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41045-124">See also</span></span>

- [<span data-ttu-id="41045-125">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="41045-125">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="41045-126">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="41045-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
