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
ms.openlocfilehash: 68dbebfc4fab773fe749f9443d0c61883099d2ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197493"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="24cbe-102">Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście</span><span class="sxs-lookup"><span data-stu-id="24cbe-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="24cbe-103">Można ustawienie pozycji tabulatorów tekst, wywołując <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> obiektu, a następnie przekazywanie, <xref:System.Drawing.StringFormat> obiekt <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="24cbe-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24cbe-104"><xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Ma nie jest obsługiwane dodawanie tabulatorów w rysowanym tekście, mimo że można rozwinąć istniejącej karty ta wstrzymuje korzystanie z <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flagi.</span><span class="sxs-lookup"><span data-stu-id="24cbe-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24cbe-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="24cbe-105">Example</span></span>  
 <span data-ttu-id="24cbe-106">W poniższym przykładzie ustawiono tabulatorów, 150, 250 i 350.</span><span class="sxs-lookup"><span data-stu-id="24cbe-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="24cbe-107">Następnie kod wyświetla listę z kartami nazwy i wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="24cbe-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="24cbe-108">Poniższa ilustracja przedstawia tekst z kartami:</span><span class="sxs-lookup"><span data-stu-id="24cbe-108">The following illustration shows the tabbed text:</span></span>  
  
 ![Zrzut ekranu przedstawiający listę z kartami nazwy i wyniki.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 <span data-ttu-id="24cbe-110">Poniższy kod przekazuje dwa argumenty <xref:System.Drawing.StringFormat.SetTabStops%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="24cbe-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="24cbe-111">Drugi argument jest tablicą zawierającą przesunięcia kartę.</span><span class="sxs-lookup"><span data-stu-id="24cbe-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="24cbe-112">Pierwszy argument przekazany do <xref:System.Drawing.StringFormat.SetTabStops%2A> ma wartość 0, co oznacza, że pierwsze przesunięcie w tablicy jest mierzony od pozycji 0, lewą krawędzią prostokąt otaczający.</span><span class="sxs-lookup"><span data-stu-id="24cbe-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24cbe-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="24cbe-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="24cbe-114">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="24cbe-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24cbe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24cbe-115">See also</span></span>

- [<span data-ttu-id="24cbe-116">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="24cbe-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="24cbe-117">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="24cbe-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
