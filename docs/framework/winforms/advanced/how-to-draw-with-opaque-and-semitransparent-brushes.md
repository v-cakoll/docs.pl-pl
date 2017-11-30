---
title: "Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4af2664851ed0903a362a4b88edf1db9bb042dfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli
Podczas wypełnienia kształtu, należy przekazać <xref:System.Drawing.Brush> obiektu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy. Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu. Aby wypełnić kształt nieprzezroczyste, należy ustawić składnika alfa koloru do 255. Aby wypełnić półprzezroczystych kształtu, należy ustawić składnika alfa na wartość od 1 do 254.  
  
 Po wypełnieniu półprzezroczystych kształtu kolor kształtu mieszania kolorów tła. Składnik alfa określa, jak kolory tła i kształtu mieszane; wartości alfa niemal 0 umieść ważniejsze na kolory tła i wartości alfa niemal 255 umieść ważniejsze na kolor kształtu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie map bitowych rysuje i następnie wypełnia wielokropek trzech, które nakładają się na mapy bitowej. Pierwszy elipsy używa składnika alfa 255, tak aby zawierała nieprzezroczyste. Wielokropek drugiego i trzeciego Użyj składnika alfa 128, dzięki czemu są one półprzezroczystych; obraz tła za pośrednictwem wielokropek jest widoczny. Wywołanie, która ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwość powodująca usunięcie mieszania trzeci elipsy w połączeniu z korekcja gamma.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poniższy kod.  
  
 ![Nieprzezroczystych i półprzezroczystych](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Przenikanie alfa linii i wypełnień](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Porady: zapewniają przezroczystego tła formantu](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Porady: Rysowanie nieprzezroczystych i półprzezroczystych linii](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
