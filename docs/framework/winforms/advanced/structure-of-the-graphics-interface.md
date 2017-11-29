---
title: Struktura interfejsu grafiki
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd1da930df151869ea3e891da7057f44ed0a4603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="structure-of-the-graphics-interface"></a><span data-ttu-id="5e53f-102">Struktura interfejsu grafiki</span><span class="sxs-lookup"><span data-stu-id="5e53f-102">Structure of the Graphics Interface</span></span>
<span data-ttu-id="5e53f-103">Interfejs zarządzanej klasy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zawiera około 60 klas, 50 wyliczenia i struktury 8.</span><span class="sxs-lookup"><span data-stu-id="5e53f-103">The managed class interface to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contains about 60 classes, 50 enumerations, and 8 structures.</span></span> <span data-ttu-id="5e53f-104"><xref:System.Drawing.Graphics> Klasy jest stanowiącej podstawę [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcji; jest klasa, która faktycznie rysuje linii, krzywych rysunki, obrazy i tekst.</span><span class="sxs-lookup"><span data-stu-id="5e53f-104">The <xref:System.Drawing.Graphics> class is at the core of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] functionality; it is the class that actually draws lines, curves, figures, images, and text.</span></span>  
  
## <a name="important-classes"></a><span data-ttu-id="5e53f-105">Ważne klas</span><span class="sxs-lookup"><span data-stu-id="5e53f-105">Important Classes</span></span>  
 <span data-ttu-id="5e53f-106">Wiele klas działają razem z <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="5e53f-106">Many classes work together with the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="5e53f-107">Na przykład <xref:System.Drawing.Graphics.DrawLine%2A> metoda <xref:System.Drawing.Pen> obiektu, który przechowuje atrybuty (kolor, szerokość, Styl kreskowany i podobnych) wiersz, który ma być rysowany.</span><span class="sxs-lookup"><span data-stu-id="5e53f-107">For example, the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object, which holds attributes (color, width, dash style, and the like) of the line to be drawn.</span></span> <span data-ttu-id="5e53f-108"><xref:System.Drawing.Graphics.FillRectangle%2A> Metody może otrzymywać wskaźnik do <xref:System.Drawing.Drawing2D.LinearGradientBrush> obiektu, który współpracuje z <xref:System.Drawing.Graphics> obiekt, aby wypełnić prostokąt stopniowo zmiana kolorów.</span><span class="sxs-lookup"><span data-stu-id="5e53f-108">The <xref:System.Drawing.Graphics.FillRectangle%2A> method can receive a pointer to a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object, which works with the <xref:System.Drawing.Graphics> object to fill a rectangle with a gradually changing color.</span></span> <span data-ttu-id="5e53f-109"><xref:System.Drawing.Font>i <xref:System.Drawing.StringFormat> obiektów określić sposób <xref:System.Drawing.Graphics> obiektu rysuje tekst.</span><span class="sxs-lookup"><span data-stu-id="5e53f-109"><xref:System.Drawing.Font> and <xref:System.Drawing.StringFormat> objects influence the way a <xref:System.Drawing.Graphics> object draws text.</span></span> <span data-ttu-id="5e53f-110">A <xref:System.Drawing.Drawing2D.Matrix> obiekt przechowuje i manipuluje transformacji świata <xref:System.Drawing.Graphics> obiektu, który służy do obracania, skalowanie i przerzucanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="5e53f-110">A <xref:System.Drawing.Drawing2D.Matrix> object stores and manipulates the world transformation of a <xref:System.Drawing.Graphics> object, which is used to rotate, scale, and flip images.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="5e53f-111">udostępnia kilka struktur (na przykład <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, i <xref:System.Drawing.Size>) służący do organizowania danych grafiki.</span><span class="sxs-lookup"><span data-stu-id="5e53f-111"> provides several structures (for example, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, and <xref:System.Drawing.Size>) for organizing graphics data.</span></span> <span data-ttu-id="5e53f-112">Ponadto niektórych klas służą głównie w strukturze typów danych.</span><span class="sxs-lookup"><span data-stu-id="5e53f-112">Also, certain classes serve primarily as structured data types.</span></span> <span data-ttu-id="5e53f-113">Na przykład <xref:System.Drawing.Imaging.BitmapData> klasy jest pomocnika dla <xref:System.Drawing.Bitmap> klasy i <xref:System.Drawing.Drawing2D.PathData> klasy jest pomocnika dla <xref:System.Drawing.Drawing2D.GraphicsPath> klasy.</span><span class="sxs-lookup"><span data-stu-id="5e53f-113">For example, the <xref:System.Drawing.Imaging.BitmapData> class is a helper for the <xref:System.Drawing.Bitmap> class, and the <xref:System.Drawing.Drawing2D.PathData> class is a helper for the <xref:System.Drawing.Drawing2D.GraphicsPath> class.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="5e53f-114">definiuje kilka wyliczenia, które są kolekcjami elementów pokrewnych stałe.</span><span class="sxs-lookup"><span data-stu-id="5e53f-114"> defines several enumerations, which are collections of related constants.</span></span> <span data-ttu-id="5e53f-115">Na przykład <xref:System.Drawing.Drawing2D.LineJoin> wyliczenie zawiera elementy <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, i <xref:System.Drawing.Drawing2D.LineJoin.Round>, które określą, style, które mogą służyć do przyłączenia dwa wiersze.</span><span class="sxs-lookup"><span data-stu-id="5e53f-115">For example, the <xref:System.Drawing.Drawing2D.LineJoin> enumeration contains the elements <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, and <xref:System.Drawing.Drawing2D.LineJoin.Round>, which specify styles that can be used to join two lines.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e53f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e53f-116">See Also</span></span>  
 [<span data-ttu-id="5e53f-117">Przegląd grafiki</span><span class="sxs-lookup"><span data-stu-id="5e53f-117">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="5e53f-118">Kodzie zarządzanym GDI + — informacje</span><span class="sxs-lookup"><span data-stu-id="5e53f-118">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="5e53f-119">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="5e53f-119">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
