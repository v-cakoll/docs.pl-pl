---
title: 'Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947816"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="d3e88-102">Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście</span><span class="sxs-lookup"><span data-stu-id="d3e88-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="d3e88-103">Można ustawić tabulatory dla tekstu przez wywołanie <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> obiektu, a następnie <xref:System.Drawing.Graphics.DrawString%2A> przekazanie tego <xref:System.Drawing.StringFormat> obiektu do metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="d3e88-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3e88-104">Nie obsługuje dodawania tabulatora do rysowanego tekstu, chociaż można rozwinąć istniejące tabulatory <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> przy użyciu flagi. <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d3e88-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3e88-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3e88-105">Example</span></span>  
 <span data-ttu-id="d3e88-106">Poniższy przykład ustawia tabulatory na 150, 250 i 350.</span><span class="sxs-lookup"><span data-stu-id="d3e88-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="d3e88-107">Następnie kod wyświetla listę nazw i wyników testów.</span><span class="sxs-lookup"><span data-stu-id="d3e88-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="d3e88-108">Na poniższej ilustracji przedstawiono tekst z kartami:</span><span class="sxs-lookup"><span data-stu-id="d3e88-108">The following illustration shows the tabbed text:</span></span>  
  
 ![Zrzut ekranu przedstawiający listę nazw i ocen na kartach.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 <span data-ttu-id="d3e88-110">Poniższy kod przekazuje dwa argumenty do <xref:System.Drawing.StringFormat.SetTabStops%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d3e88-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="d3e88-111">Drugi argument jest tablicą zawierającą przesunięcia tabulacji.</span><span class="sxs-lookup"><span data-stu-id="d3e88-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="d3e88-112">Pierwszy argument, który przeszedł do <xref:System.Drawing.StringFormat.SetTabStops%2A> to 0, co oznacza, że pierwsze przesunięcie w tablicy jest mierzone od położenia 0, lewej krawędzi prostokąta granicy.</span><span class="sxs-lookup"><span data-stu-id="d3e88-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3e88-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d3e88-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="d3e88-114">Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>który jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="d3e88-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e88-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3e88-115">See also</span></span>

- [<span data-ttu-id="d3e88-116">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="d3e88-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="d3e88-117">Instrukcje: Rysuj tekst przy użyciu GDI</span><span class="sxs-lookup"><span data-stu-id="d3e88-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
