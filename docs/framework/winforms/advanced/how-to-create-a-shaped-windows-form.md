---
title: 'Instrukcje: Tworzenie formularza Windows o określonych kształtach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
ms.openlocfilehash: a130614b0977aab6191f195c93454c527e6be9b8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710072"
---
# <a name="how-to-create-a-shaped-windows-form"></a><span data-ttu-id="7226b-102">Instrukcje: Tworzenie formularza Windows o określonych kształtach</span><span class="sxs-lookup"><span data-stu-id="7226b-102">How to: Create a Shaped Windows Form</span></span>
<span data-ttu-id="7226b-103">W tym przykładzie daje formularza kształcie elipsy, który zmienia rozmiar za pomocą formularza.</span><span class="sxs-lookup"><span data-stu-id="7226b-103">This example gives a form an elliptical shape that resizes with the form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7226b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7226b-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7226b-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7226b-105">Compiling the Code</span></span>  
 <span data-ttu-id="7226b-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7226b-106">This example requires:</span></span>  
  
-   <span data-ttu-id="7226b-107">Odwołuje się do <xref:System.Windows.Forms> i <xref:System.Drawing> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7226b-107">References to the <xref:System.Windows.Forms> and <xref:System.Drawing> namespaces.</span></span>  
  
 <span data-ttu-id="7226b-108">Ten przykład przedstawia przesłonięcie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, aby zmienić kształt formularza.</span><span class="sxs-lookup"><span data-stu-id="7226b-108">This example overrides the <xref:System.Windows.Forms.Control.OnPaint%2A> method to change the shape of the form.</span></span> <span data-ttu-id="7226b-109">Aby użyć tego kodu, skopiuj deklaracji metody, a także kod rysowania wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="7226b-109">To use this code, copy the method declaration as well as the drawing code inside the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7226b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7226b-110">See also</span></span>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Region>
- <xref:System.Drawing>
- <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>
- <xref:System.Windows.Forms.Control.Region%2A>
- [<span data-ttu-id="7226b-111">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="7226b-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
