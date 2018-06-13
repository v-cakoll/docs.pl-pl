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
ms.openlocfilehash: 7d66bf147a220bdcdfd32a703d3407817a184a54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521475"
---
# <a name="how-to-create-vertical-text"></a>Porady: tworzenie pionowego tekstu
Można użyć <xref:System.Drawing.StringFormat> obiektu w celu określenia, czy tekst być rysowany pionowo, a nie w poziomie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przypisuje wartość <xref:System.Drawing.StringFormatFlags.DirectionVertical> do <xref:System.Drawing.StringFormat.FormatFlags%2A> właściwość <xref:System.Drawing.StringFormat> obiektu. Czy <xref:System.Drawing.StringFormat> obiekt jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy. Wartość <xref:System.Drawing.StringFormatFlags.DirectionVertical> jest elementem członkowskim <xref:System.Drawing.StringFormatFlags> wyliczenia.  
  
 Na poniższej ilustracji przedstawiono pionowego tekstu.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e` , który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: rysowanie tekstu za pomocą GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
