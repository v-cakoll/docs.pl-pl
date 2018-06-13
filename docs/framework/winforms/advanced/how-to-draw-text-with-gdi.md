---
title: 'Porady: rysowanie tekstu za pomocą GDI'
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
ms.openlocfilehash: e18ff96ea97eb636de8ab73aaa094c07b10fd456
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522918"
---
# <a name="how-to-draw-text-with-gdi"></a>Porady: rysowanie tekstu za pomocą GDI
Z <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody w <xref:System.Windows.Forms.TextRenderer> klasy, można uzyskać dostęp [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funkcji Rysowanie tekstu na formularz lub formant. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Renderowanie tekstu zwykle zapewnia lepszą wydajność i dokładniejsze tekst pomiaru niż [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> klasy nie są obsługiwane do drukowania. Podczas drukowania, należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak rysowanie tekstu w wielu wierszach w prostokącie przy użyciu <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Do renderowania tekstu w <xref:System.Windows.Forms.TextRenderer> klasy, należy <xref:System.Drawing.IDeviceContext>, takich jak <xref:System.Drawing.Graphics> i <xref:System.Drawing.Font>, lokalizacji do rysowania tekstu i kolor, w którym ma być rysowany. Opcjonalnie można określić formatowanie przy użyciu tekstu <xref:System.Windows.Forms.TextFormatFlags> wyliczenia.  
  
 Aby uzyskać więcej informacji na temat uzyskiwania <xref:System.Drawing.Graphics>, zobacz [porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Aby uzyskać więcej informacji na temat tworzenia <xref:System.Drawing.Font>, zobacz [jak: utworzyć rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
