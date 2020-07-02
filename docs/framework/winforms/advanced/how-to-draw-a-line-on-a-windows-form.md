---
title: 'Porady: rysowanie linii w formularzu systemu Windows'
description: Dowiedz się, jak narysować linię w formularzu przez obsługę zdarzenia Paint, a następnie wykonać rysowanie przy użyciu właściwości Graphics PaintEventArgs.
ms.date: 03/30/2017
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
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621629"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="8a9b9-103">Porady: rysowanie linii w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8a9b9-103">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="8a9b9-104">Ten przykład rysuje linię w formularzu.</span><span class="sxs-lookup"><span data-stu-id="8a9b9-104">This example draws a line on a form.</span></span> <span data-ttu-id="8a9b9-105">Zwykle podczas rysowania na formularzu jest obsługiwane <xref:System.Windows.Forms.Control.Paint> zdarzenie formularza i wykonywanie rysunku przy użyciu <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwości <xref:System.Windows.Forms.PaintEventArgs> , jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8a9b9-105">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a9b9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a9b9-106">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a9b9-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8a9b9-107">Compiling the Code</span></span>  
 <span data-ttu-id="8a9b9-108">Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e` , który jest parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8a9b9-108">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8a9b9-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8a9b9-109">Robust Programming</span></span>  
 <span data-ttu-id="8a9b9-110">Należy zawsze wywoływać <xref:System.IDisposable.Dispose%2A> wszystkie obiekty, które zużywają zasoby systemowe, takie jak <xref:System.Drawing.Pen> obiekty.</span><span class="sxs-lookup"><span data-stu-id="8a9b9-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9b9-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a9b9-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="8a9b9-112">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="8a9b9-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="8a9b9-113">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="8a9b9-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="8a9b9-114">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a9b9-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
