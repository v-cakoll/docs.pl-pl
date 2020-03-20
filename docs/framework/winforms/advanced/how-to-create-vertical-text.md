---
title: 'Porady: tworzenie pionowego tekstu'
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
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182561"
---
# <a name="how-to-create-vertical-text"></a>Porady: tworzenie pionowego tekstu
Za pomocą <xref:System.Drawing.StringFormat> obiektu można określić, że tekst jest rysowany pionowo, a nie w poziomie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przypisuje <xref:System.Drawing.StringFormatFlags.DirectionVertical> wartość <xref:System.Drawing.StringFormat.FormatFlags%2A> do właściwości <xref:System.Drawing.StringFormat> obiektu. Ten <xref:System.Drawing.StringFormat> obiekt jest <xref:System.Drawing.Graphics.DrawString%2A> przekazywany <xref:System.Drawing.Graphics> do metody klasy. Wartość <xref:System.Drawing.StringFormatFlags.DirectionVertical> jest członkiem <xref:System.Drawing.StringFormatFlags> wyliczenia.  
  
 Na poniższej ilustracji przedstawiono tekst pionowy:
  
 ![Grafika przedstawiająca tekst czcionki pionowej.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e` formularzami systemu Windows <xref:System.Windows.Forms.PaintEventHandler>i wymaga , który jest parametrem .  
  
## <a name="see-also"></a>Zobacz też

- [Porady: rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md)
