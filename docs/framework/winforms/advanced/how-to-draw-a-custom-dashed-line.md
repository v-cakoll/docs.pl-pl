---
title: 'Porady: rysowanie niestandardowej linii kreskowanej'
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
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 770ce290b21f7d0094a487c30079063b79a7c08d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="aaa10-102">Porady: rysowanie niestandardowej linii kreskowanej</span><span class="sxs-lookup"><span data-stu-id="aaa10-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="aaa10-103">dostępnych jest kilka typów kreska, które są wymienione w <xref:System.Drawing.Drawing2D.DashStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="aaa10-103"> provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="aaa10-104">Jeśli te style standard dash nie własnych potrzeb, można utworzyć niestandardowego wzorze.</span><span class="sxs-lookup"><span data-stu-id="aaa10-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaa10-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="aaa10-105">Example</span></span>  
 <span data-ttu-id="aaa10-106">Rysowanie niestandardowej linii kreskowanej, umieść długości kresek i spacji w tablicy i przypisz tablicy jako wartość <xref:System.Drawing.Pen.DashPattern%2A> właściwość <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="aaa10-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="aaa10-107">Poniższy przykład rysuje niestandardowej linii kreskowanej oparte na tablicy `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="aaa10-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="aaa10-108">Jeśli elementy tablicy pomnożenia szerokość pióra 5, możesz uzyskać `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="aaa10-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="aaa10-109">Łączniki wyświetlanych alternatywny długości między 25 i 75 i przestrzeni alternatywny o długości od 10 do 20.</span><span class="sxs-lookup"><span data-stu-id="aaa10-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="aaa10-110">Na poniższej ilustracji przedstawiono wynikowa linia przerywana.</span><span class="sxs-lookup"><span data-stu-id="aaa10-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="aaa10-111">Należy pamiętać, że dash końcowego musi być krótsza niż 25 jednostek tak, aby wiersz może kończyć się przy (405, 5).</span><span class="sxs-lookup"><span data-stu-id="aaa10-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="aaa10-112">![Pióra](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="aaa10-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aaa10-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="aaa10-113">Compiling the Code</span></span>  
 <span data-ttu-id="aaa10-114">Tworzenie formularza systemu Windows i obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aaa10-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="aaa10-115">Wklej poprzedni kod do <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aaa10-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa10-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aaa10-116">See Also</span></span>  
 [<span data-ttu-id="aaa10-117">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="aaa10-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
