---
title: 'Porady: rysowanie linii w formularzu systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 78ad7d455f1de4b7077288d9575ea4907c3f218d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="5c33f-102">Porady: rysowanie linii w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5c33f-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="5c33f-103">W tym przykładzie rysuje linię w formularzu.</span><span class="sxs-lookup"><span data-stu-id="5c33f-103">This example draws a line on a form.</span></span> <span data-ttu-id="5c33f-104">Zazwyczaj podczas rysowania na formularzu, należy obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń i wykonywać Rysowanie za pomocą <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość <xref:System.Windows.Forms.PaintEventArgs>, jak pokazano w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="5c33f-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c33f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c33f-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c33f-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5c33f-106">Compiling the Code</span></span>  
 <span data-ttu-id="5c33f-107">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c33f-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5c33f-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5c33f-108">Robust Programming</span></span>  
 <span data-ttu-id="5c33f-109">Zawsze należy wywołać <xref:System.IDisposable.Dispose%2A> na wszystkie obiekty używające zasobów systemowych, takich jak <xref:System.Drawing.Pen> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5c33f-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c33f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c33f-110">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawLine%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="5c33f-111">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="5c33f-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="5c33f-112">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="5c33f-112">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="5c33f-113">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c33f-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
