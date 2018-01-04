---
title: "Współrzędne formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a><span data-ttu-id="abbeb-102">Współrzędne formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="abbeb-102">Windows Forms Coordinates</span></span>
<span data-ttu-id="abbeb-103">System współrzędnych dla formularza systemu Windows jest oparta na współrzędnych urządzenia i jednostkę urządzenie (zazwyczaj pikseli) jest podstawową jednostką miary Rysowanie w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="abbeb-103">The coordinate system for a Windows Form is based on device coordinates, and the basic unit of measure when drawing in Windows Forms is the device unit (typically, the pixel).</span></span> <span data-ttu-id="abbeb-104">Punkty na ekranie są opisane przez pary współrzędną x i y, z współrzędne x zwiększenie w prawo i współrzędną y zwiększenie od góry do dołu.</span><span class="sxs-lookup"><span data-stu-id="abbeb-104">Points on the screen are described by x- and y-coordinate pairs, with the x-coordinates increasing to the right and the y-coordinates increasing from top to bottom.</span></span> <span data-ttu-id="abbeb-105">Miejsce pochodzenia względem ekranu, będą się różnić w zależności od tego, czy są określający współrzędne ekranu lub klienta.</span><span class="sxs-lookup"><span data-stu-id="abbeb-105">The location of the origin, relative to the screen, will vary depending on whether you are specifying screen or client coordinates.</span></span>  
  
## <a name="screen-coordinates"></a><span data-ttu-id="abbeb-106">Współrzędne ekranu</span><span class="sxs-lookup"><span data-stu-id="abbeb-106">Screen Coordinates</span></span>  
 <span data-ttu-id="abbeb-107">Aplikacji formularzy systemu Windows określa położenie okna na ekranie we współrzędnych ekranu.</span><span class="sxs-lookup"><span data-stu-id="abbeb-107">A Windows Forms application specifies the position of a window on the screen in screen coordinates.</span></span> <span data-ttu-id="abbeb-108">Współrzędne ekranu źródła jest lewym górnym rogu ekranu.</span><span class="sxs-lookup"><span data-stu-id="abbeb-108">For screen coordinates, the origin is the upper-left corner of the screen.</span></span> <span data-ttu-id="abbeb-109">Pełna położenie okna jest często opisanego przez <xref:System.Drawing.Rectangle> struktury zawierającej współrzędne ekranu dwa punkty, które definiują górnym rogu i prawym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="abbeb-109">The full position of a window is often described by a <xref:System.Drawing.Rectangle> structure containing the screen coordinates of two points that define the upper-left and lower-right corners of the window.</span></span>  
  
## <a name="client-coordinates"></a><span data-ttu-id="abbeb-110">Współrzędne klienta</span><span class="sxs-lookup"><span data-stu-id="abbeb-110">Client Coordinates</span></span>  
 <span data-ttu-id="abbeb-111">Aplikacji formularzy systemu Windows określa pozycję punktów w formularzu lub formantu przy użyciu współrzędnych klienta.</span><span class="sxs-lookup"><span data-stu-id="abbeb-111">A Windows Forms application specifies the position of points in a form or control using client coordinates.</span></span> <span data-ttu-id="abbeb-112">Punkt początkowy współrzędne klienta jest lewego górnego rogu obszaru klienta formularza lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="abbeb-112">The origin for client coordinates is the upper-left corner of the client area of the control or form.</span></span> <span data-ttu-id="abbeb-113">Współrzędne klienta upewnij się, czy aplikacja może użyć spójne wartości współrzędnych podczas rysowania formularza lub kontrolki, niezależnie od położenia formularza lub kontrolki, na ekranie.</span><span class="sxs-lookup"><span data-stu-id="abbeb-113">Client coordinates ensure that an application can use consistent coordinate values while drawing in a form or control, regardless of the position of the form or control on the screen.</span></span>  
  
 <span data-ttu-id="abbeb-114">Wymiary obszaru klienckiego są także opisane przez <xref:System.Drawing.Rectangle> struktury, która zawiera współrzędne klienta dla obszaru.</span><span class="sxs-lookup"><span data-stu-id="abbeb-114">The dimensions of the client area are also described by a <xref:System.Drawing.Rectangle> structure that contains client coordinates for the area.</span></span> <span data-ttu-id="abbeb-115">We wszystkich przypadkach Współrzędna lewej górnej krawędzi prostokąta znajduje się w obszarze klienta podczas prawą dolną współrzędną jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="abbeb-115">In all cases, the upper-left coordinate of the rectangle is included in the client area, while the lower-right coordinate is excluded.</span></span> <span data-ttu-id="abbeb-116">Operacje graficzne nie dołączaj dolnej i prawej krawędzi obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="abbeb-116">Graphics operations do not include the right and lower edges of a client area.</span></span> <span data-ttu-id="abbeb-117">Na przykład <xref:System.Drawing.Graphics.FillRectangle%2A> metoda będzie zapełnić do prawej i w dolnej krawędzi prostokąt określony, ale nie będzie zawierał te krawędzi.</span><span class="sxs-lookup"><span data-stu-id="abbeb-117">For example the <xref:System.Drawing.Graphics.FillRectangle%2A> method will fill up to the right and lower edge of the specified rectangle, but will not include these edges.</span></span>  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a><span data-ttu-id="abbeb-118">Mapowanie typu współrzędnych</span><span class="sxs-lookup"><span data-stu-id="abbeb-118">Mapping From One Type of Coordinate to Another</span></span>  
 <span data-ttu-id="abbeb-119">Czasami może być konieczne mapowania współrzędne ekranu na współrzędne klienta.</span><span class="sxs-lookup"><span data-stu-id="abbeb-119">Occasionally, you may need to map from screen coordinates to client coordinates.</span></span> <span data-ttu-id="abbeb-120">Możesz to łatwo zrobić przy użyciu <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod w <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="abbeb-120">You can easily accomplish this by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available in the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="abbeb-121">Na przykład <xref:System.Windows.Forms.Control.MousePosition%2A> właściwość <xref:System.Windows.Forms.Control> jest zgłaszany we współrzędnych ekranu, ale chcesz przekonwertować je na współrzędne klienta.</span><span class="sxs-lookup"><span data-stu-id="abbeb-121">For example, the <xref:System.Windows.Forms.Control.MousePosition%2A> property of <xref:System.Windows.Forms.Control> is reported in screen coordinates, but you may want to convert these to client coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abbeb-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abbeb-122">See Also</span></span>  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
