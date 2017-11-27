---
title: "Porady: tworzenie pędzla pełnego koloru"
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
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01c07c132a703d6fd9401d9c191f5467667cc156
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="e205e-102">Porady: tworzenie pędzla pełnego koloru</span><span class="sxs-lookup"><span data-stu-id="e205e-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="e205e-103">Ten przykład tworzy <xref:System.Drawing.SolidBrush> obiektu, który może być używany przez <xref:System.Drawing.Graphics> obiektu do wypełniania kształtów.</span><span class="sxs-lookup"><span data-stu-id="e205e-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e205e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e205e-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e205e-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e205e-105">Robust Programming</span></span>  
 <span data-ttu-id="e205e-106">Po zakończeniu korzystania z nich należy wywołać <xref:System.IDisposable.Dispose%2A> w obiektach, które korzystać z zasobów systemowych, takich jak obiekty pędzla.</span><span class="sxs-lookup"><span data-stu-id="e205e-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e205e-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e205e-107">See Also</span></span>  
 <xref:System.Drawing.SolidBrush>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="e205e-108">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="e205e-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="e205e-109">Pędzle i wypełnione kształty w GDI +</span><span class="sxs-lookup"><span data-stu-id="e205e-109">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 [<span data-ttu-id="e205e-110">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="e205e-110">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
