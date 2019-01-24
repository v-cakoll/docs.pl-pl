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
ms.openlocfilehash: 4bf9328b63be88f487995f7b9691683167271c46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635809"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście
Można ustawienie pozycji tabulatorów tekst, wywołując <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> obiektu, a następnie przekazywanie, <xref:System.Drawing.StringFormat> obiekt <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Ma nie jest obsługiwane dodawanie tabulatorów w rysowanym tekście, mimo że można rozwinąć istniejącej karty ta wstrzymuje korzystanie z <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flagi.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie ustawiono tabulatorów, 150, 250 i 350. Następnie kod wyświetla listę z kartami nazwy i wyniki testu.  
  
 Poniższa ilustracja przedstawia okno tekstowe.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 Poniższy kod przekazuje dwa argumenty <xref:System.Drawing.StringFormat.SetTabStops%2A> metody. Drugi argument jest tablicą zawierającą przesunięcia kartę. Pierwszy argument przekazany do <xref:System.Drawing.StringFormat.SetTabStops%2A> ma wartość 0, co oznacza, że pierwsze przesunięcie w tablicy jest mierzony od pozycji 0, lewą krawędzią prostokąt otaczający.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [Instrukcje: Rysowanie tekstu za pomocą GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
