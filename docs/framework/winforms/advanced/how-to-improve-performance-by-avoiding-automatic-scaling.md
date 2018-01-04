---
title: "Porady: poprawianie wydajności dzięki unikaniu automatycznego skalowania"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f49fc4b1e59879b9ecc67295610187fa2e5e80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a><span data-ttu-id="0bc6d-102">Porady: poprawianie wydajności dzięki unikaniu automatycznego skalowania</span><span class="sxs-lookup"><span data-stu-id="0bc6d-102">How to: Improve Performance by Avoiding Automatic Scaling</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="0bc6d-103">może automatycznie skalować obrazu podczas rysowania, które mogłoby obniżyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-103"> may automatically scale an image as you draw it, which would decrease performance.</span></span> <span data-ttu-id="0bc6d-104">Alternatywnie można kontrolować skalowanie obrazu przekazując wymiary prostokąt docelowy <xref:System.Drawing.Graphics.DrawImage%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-104">Alternatively, you can control the scaling of the image by passing the dimensions of the destination rectangle to the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
 <span data-ttu-id="0bc6d-105">Na przykład następujące wywołanie do <xref:System.Drawing.Graphics.DrawImage%2A> metody określa lewym górnym rogu (50, 30), ale nie określa prostokątne docelowego.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-105">For example, the following call to the <xref:System.Drawing.Graphics.DrawImage%2A> method specifies an upper-left corner of (50, 30) but does not specify a destination rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 <span data-ttu-id="0bc6d-106">Chociaż jest to wersja najprostszym <xref:System.Drawing.Graphics.DrawImage%2A> metody pod względem liczby wymaganych argumentów nie jest zawsze najbardziej efektywny.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-106">Although this is the easiest version of the <xref:System.Drawing.Graphics.DrawImage%2A> method in terms of the number of required arguments, it is not necessarily the most efficient.</span></span> <span data-ttu-id="0bc6d-107">Jeśli rozwiązanie używany przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (zazwyczaj 96 punktów na cal) różni się od rozdzielczości, przechowywane w <xref:System.Drawing.Image> obiektu, a następnie <xref:System.Drawing.Graphics.DrawImage%2A> metody mogą być skalowane obrazu.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-107">If the resolution used by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (usually 96 dots per inch) is different from the resolution stored in the <xref:System.Drawing.Image> object, then the <xref:System.Drawing.Graphics.DrawImage%2A> method will scale the image.</span></span> <span data-ttu-id="0bc6d-108">Załóżmy na przykład, <xref:System.Drawing.Image> obiekt ma szerokość 216 pikseli i wartości przechowywanej rozdzielczość pozioma 72 dpi.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-108">For example, suppose an <xref:System.Drawing.Image> object has a width of 216 pixels and a stored horizontal resolution value of 72 dots per inch.</span></span> <span data-ttu-id="0bc6d-109">Ponieważ 216/72 to 3, <xref:System.Drawing.Graphics.DrawImage%2A> skaluje obraz, aby miała ona szerokość 3 cale przy rozdzielczości 96 dpi.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-109">Because 216/72 is 3, <xref:System.Drawing.Graphics.DrawImage%2A> will scale the image so that it has a width of 3 inches at a resolution of 96 dots per inch.</span></span> <span data-ttu-id="0bc6d-110">Oznacza to, że <xref:System.Drawing.Graphics.DrawImage%2A> wyświetli obraz, który ma szerokość 96 x 3 = 288 pikseli.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-110">That is, <xref:System.Drawing.Graphics.DrawImage%2A> will display an image that has a width of 96x3 = 288 pixels.</span></span>  
  
 <span data-ttu-id="0bc6d-111">Nawet jeśli rozdzielczość ekranu jest inny niż 96 punktów na cal, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] będzie prawdopodobnie skali obrazu tak, jakby 96 punktów na cal był rozdzielczość ekranu.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-111">Even if your screen resolution is different from 96 dots per inch, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] will probably scale the image as if the screen resolution were 96 dots per inch.</span></span> <span data-ttu-id="0bc6d-112">Jest to spowodowane tym [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> obiekt jest skojarzony z kontekstu urządzenia i kiedy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zapytania kontekst urządzenia dla rozdzielczość ekranu, wynik jest zwykle 96, niezależnie od rzeczywistej rozdzielczości.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-112">That is because a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> object is associated with a device context, and when [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] queries the device context for the screen resolution, the result is usually 96, regardless of the actual screen resolution.</span></span> <span data-ttu-id="0bc6d-113">Można uniknąć, automatyczne skalowanie, określając docelowy prostokąt w <xref:System.Drawing.Graphics.DrawImage%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-113">You can avoid automatic scaling by specifying the destination rectangle in the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bc6d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bc6d-114">Example</span></span>  
 <span data-ttu-id="0bc6d-115">Poniższy przykład rysuje dwa razy ten sam obraz.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-115">The following example draws the same image twice.</span></span> <span data-ttu-id="0bc6d-116">W pierwszym przypadku szerokość i wysokość prostokąta docelowego nie są określone, a obraz jest automatycznie skalowany.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-116">In the first case, the width and height of the destination rectangle are not specified, and the image is automatically scaled.</span></span> <span data-ttu-id="0bc6d-117">W drugim przypadku szerokość i wysokość (podawana w pikselach) prostokąta docelowej są określone na taki sam jak szerokość i wysokość oryginalnego obrazu.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-117">In the second case, the width and height (measured in pixels) of the destination rectangle are specified to be the same as the width and height of the original image.</span></span> <span data-ttu-id="0bc6d-118">Na poniższej ilustracji przedstawiono obrazu renderowania dwa razy.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-118">The following illustration shows the image rendered twice.</span></span>  
  
 <span data-ttu-id="0bc6d-119">![Skalować tekstury](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span><span class="sxs-lookup"><span data-stu-id="0bc6d-119">![Scaled Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0bc6d-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0bc6d-120">Compiling the Code</span></span>  
 <span data-ttu-id="0bc6d-121">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-121">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="0bc6d-122">Zamień na Texture.jpg obrazu nazwę i ścieżkę, które są prawidłowe w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="0bc6d-122">Replace Texture.jpg with an image name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc6d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bc6d-123">See Also</span></span>  
 [<span data-ttu-id="0bc6d-124">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="0bc6d-124">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="0bc6d-125">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="0bc6d-125">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
