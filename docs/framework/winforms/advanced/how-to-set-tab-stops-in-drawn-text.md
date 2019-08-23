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
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście
Można ustawić tabulatory dla tekstu przez wywołanie <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> obiektu, a następnie <xref:System.Drawing.Graphics.DrawString%2A> przekazanie tego <xref:System.Drawing.StringFormat> obiektu do metody <xref:System.Drawing.Graphics> klasy.  
  
> [!NOTE]
> Nie obsługuje dodawania tabulatora do rysowanego tekstu, chociaż można rozwinąć istniejące tabulatory <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> przy użyciu flagi. <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia tabulatory na 150, 250 i 350. Następnie kod wyświetla listę nazw i wyników testów.  
  
 Na poniższej ilustracji przedstawiono tekst z kartami:  
  
 ![Zrzut ekranu przedstawiający listę nazw i ocen na kartach.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 Poniższy kod przekazuje dwa argumenty do <xref:System.Drawing.StringFormat.SetTabStops%2A> metody. Drugi argument jest tablicą zawierającą przesunięcia tabulacji. Pierwszy argument, który przeszedł do <xref:System.Drawing.StringFormat.SetTabStops%2A> to 0, co oznacza, że pierwsze przesunięcie w tablicy jest mierzone od położenia 0, lewej krawędzi prostokąta granicy.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>który jest parametrem.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie czcionek i tekstu](using-fonts-and-text.md)
- [Instrukcje: Rysuj tekst przy użyciu GDI](how-to-draw-text-with-gdi.md)
