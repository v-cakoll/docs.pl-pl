---
title: 'Instrukcje: Tworzenie pionowego tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 8398b3f18b764743bac19022b69e7f6fac0f7d57
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625995"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="8dfe6-102">Instrukcje: Tworzenie pionowego tekstu</span><span class="sxs-lookup"><span data-stu-id="8dfe6-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="8dfe6-103">Możesz użyć <xref:System.Drawing.StringFormat> obiektu w celu określenia, czy tekst być rysowany pionowo, a nie w poziomie.</span><span class="sxs-lookup"><span data-stu-id="8dfe6-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dfe6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dfe6-104">Example</span></span>  
 <span data-ttu-id="8dfe6-105">Poniższy przykład przypisuje wartość <xref:System.Drawing.StringFormatFlags.DirectionVertical> do <xref:System.Drawing.StringFormat.FormatFlags%2A> właściwość <xref:System.Drawing.StringFormat> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8dfe6-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="8dfe6-106">Czy <xref:System.Drawing.StringFormat> obiekt jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="8dfe6-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="8dfe6-107">Wartość <xref:System.Drawing.StringFormatFlags.DirectionVertical> jest elementem członkowskim <xref:System.Drawing.StringFormatFlags> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8dfe6-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="8dfe6-108">Poniższa ilustracja przedstawia pionowego tekstu:</span><span class="sxs-lookup"><span data-stu-id="8dfe6-108">The following illustration shows the vertical text:</span></span> 
  
 ![Grafika przedstawiająca tekst pionowy czcionki.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8dfe6-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8dfe6-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="8dfe6-111">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e` , czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="8dfe6-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dfe6-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8dfe6-112">See also</span></span>

- [<span data-ttu-id="8dfe6-113">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="8dfe6-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
