---
title: "Porady: łączenie linii"
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
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f02da181d66f7bb26a8414782e42eff2570e6918
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-join-lines"></a><span data-ttu-id="02ae2-102">Porady: łączenie linii</span><span class="sxs-lookup"><span data-stu-id="02ae2-102">How to: Join Lines</span></span>
<span data-ttu-id="02ae2-103">Połączenie linii jest typowe obszar, który jest tworzony przez dwa wiersze, w których zakończenia spełnia lub nakładają się.</span><span class="sxs-lookup"><span data-stu-id="02ae2-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="02ae2-104">udostępnia trzy style sprzężenia linii: ostre, faza i zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="02ae2-104"> provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="02ae2-105">Styl łączenia linii jest właściwością <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="02ae2-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="02ae2-106">Po określeniu styl łączenia linii dla <xref:System.Drawing.Pen> obiektu, czy styl łączenia zostaną zastosowane do wszystkich połączonych wierszy w żadnym <xref:System.Drawing.Drawing2D.GraphicsPath> rysowane przy użyciu pióra tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="02ae2-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="02ae2-107">Na poniższej ilustracji przedstawiono wyniki przykładu sprzężenia ukośne wiersza.</span><span class="sxs-lookup"><span data-stu-id="02ae2-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 <span data-ttu-id="02ae2-108">![Pióra](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span><span class="sxs-lookup"><span data-stu-id="02ae2-108">![Pens](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ae2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="02ae2-109">Example</span></span>  
 <span data-ttu-id="02ae2-110">Styl łączenia linii można określić za pomocą <xref:System.Drawing.Pen.LineJoin%2A> właściwość <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="02ae2-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="02ae2-111">W przykładzie pokazano ukośne wiersza sprzężenie wierszy poziomych linii pionowej.</span><span class="sxs-lookup"><span data-stu-id="02ae2-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="02ae2-112">W poniższym kodzie wartość <xref:System.Drawing.Drawing2D.LineJoin.Bevel> przypisane do <xref:System.Drawing.Pen.LineJoin%2A> właściwości jest elementem członkowskim <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="02ae2-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="02ae2-113">Elementy członkowskie z <xref:System.Drawing.Drawing2D.LineJoin> są wyliczenie <xref:System.Drawing.Drawing2D.LineJoin.Miter> i <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="02ae2-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02ae2-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="02ae2-114">Compiling the Code</span></span>  
 <span data-ttu-id="02ae2-115">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="02ae2-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ae2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02ae2-116">See Also</span></span>  
 [<span data-ttu-id="02ae2-117">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="02ae2-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
