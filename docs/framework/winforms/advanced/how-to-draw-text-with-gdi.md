---
title: 'Instrukcje: Rysowanie tekstu za pomocą GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3cb67f01f145a55e4e8a68642a37ad287ee94b1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685931"
---
# <a name="how-to-draw-text-with-gdi"></a>Instrukcje: Rysowanie tekstu za pomocą GDI
Za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in Class metoda <xref:System.Windows.Forms.TextRenderer> klasy, możesz uzyskać dostęp [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funkcji Rysowanie tekstu na formularz lub formant. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Renderowanie tekstu zwykle zapewnia lepszą wydajność i bardziej precyzyjne tekstu pomiaru niż [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> klasy nie są obsługiwane w przypadku drukowania. Podczas drukowania, należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak rysować tekst w wielu wierszach, w obrębie prostokąta za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Aby renderować tekstu za pomocą <xref:System.Windows.Forms.TextRenderer> klasy, należy <xref:System.Drawing.IDeviceContext>, takich jak <xref:System.Drawing.Graphics> i <xref:System.Drawing.Font>, lokalizację w której Rysowanie tekstu i kolorów, w którym ma być rysowany. Opcjonalnie można określić za pomocą do formatowania tekstu <xref:System.Windows.Forms.TextFormatFlags> wyliczenia.  
  
 Aby uzyskać więcej informacji na temat uzyskiwania <xref:System.Drawing.Graphics>, zobacz [jak: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Aby uzyskać więcej informacji na temat tworzenia <xref:System.Drawing.Font>, zobacz [jak: Tworzenie rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- <xref:System.Drawing.Color>
- [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
