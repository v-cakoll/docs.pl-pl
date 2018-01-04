---
title: "Porady: rysowanie linii z zakończeniem linii"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4048757e11724aa1e175d8b18c47f48d22d807e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="74c44-102">Porady: rysowanie linii z zakończeniem linii</span><span class="sxs-lookup"><span data-stu-id="74c44-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="74c44-103">Może wykonywać Rysowanie początek lub koniec wiersza w jednym z kilku kształtów o nazwie wielkości graniczne linii.</span><span class="sxs-lookup"><span data-stu-id="74c44-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="74c44-104">obsługuje kilka wielkości graniczne linii, takich jak round, kwadratowe romb i strzałki.</span><span class="sxs-lookup"><span data-stu-id="74c44-104"> supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c44-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="74c44-105">Example</span></span>  
 <span data-ttu-id="74c44-106">Można określić wielkości graniczne linii do początku wiersza (start cap), na koniec wiersza (zakończenie) lub łączniki linii kreskowanej (dash cap).</span><span class="sxs-lookup"><span data-stu-id="74c44-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="74c44-107">Poniższy przykład rysuje linię za pomocą strzałki w jeden element end i okrągłe zakończenie na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="74c44-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="74c44-108">Na ilustracji przedstawiono wynikowego wiersza:</span><span class="sxs-lookup"><span data-stu-id="74c44-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="74c44-109">![Pióra](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="74c44-109">![Pens](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74c44-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="74c44-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="74c44-111">Tworzenie formularza systemu Windows i obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="74c44-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="74c44-112">Wklej przykładowy kod do <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń przekazywanie `e` jako <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="74c44-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c44-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74c44-113">See Also</span></span>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [<span data-ttu-id="74c44-114">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74c44-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="74c44-115">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="74c44-115">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
