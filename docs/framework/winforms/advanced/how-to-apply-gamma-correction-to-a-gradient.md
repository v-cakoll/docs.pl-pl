---
title: 'Porady: stosowanie korekcji gamma do gradientu'
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
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2721a45381f2d0befe82d6d0db2630f3eae08d51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="d812e-102">Porady: stosowanie korekcji gamma do gradientu</span><span class="sxs-lookup"><span data-stu-id="d812e-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="d812e-103">Można włączyć korekcji gamma pędzla gradientu liniowego, ustawiając pędzla <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="d812e-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="d812e-104">Korekcja gamma można wyłączyć, ustawiając <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="d812e-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="d812e-105">Korekcja gamma jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="d812e-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d812e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d812e-106">Example</span></span>  
 <span data-ttu-id="d812e-107">W przykładzie tworzy pędzla gradientu liniowego i używa tego pędzla do wypełniania dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="d812e-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="d812e-108">Pierwszy prostokąt zostanie wypełnione bez korekcji gamma, a drugi prostokąt jest wypełniony korekcja gamma.</span><span class="sxs-lookup"><span data-stu-id="d812e-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="d812e-109">Na poniższej ilustracji przedstawiono dwa prostokąty wypełnione.</span><span class="sxs-lookup"><span data-stu-id="d812e-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="d812e-110">Górnego prostokąta, która nie ma korekcja gamma, pojawi się ciemny w środku.</span><span class="sxs-lookup"><span data-stu-id="d812e-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="d812e-111">Prostokąt dołu, mającej korekcja gamma pojawia się ma więcej intensywność uniform.</span><span class="sxs-lookup"><span data-stu-id="d812e-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="d812e-112">![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="d812e-112">![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d812e-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d812e-113">Compiling the Code</span></span>  
 <span data-ttu-id="d812e-114">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d812e-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d812e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d812e-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [<span data-ttu-id="d812e-116">Używanie pędzla gradientów do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="d812e-116">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
