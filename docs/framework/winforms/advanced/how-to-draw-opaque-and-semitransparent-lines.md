---
title: "Porady: rysowanie nieprzezroczystych i półprzezroczystych linii"
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
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea65fd836a6e6fc00472f6139a0700ea859545cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Porady: rysowanie nieprzezroczystych i półprzezroczystych linii
W przypadku rysowania linii, należy podać <xref:System.Drawing.Pen> do obiektu <xref:System.Drawing.Graphics.DrawLine%2A> metody <xref:System.Drawing.Graphics> klasy. Jeden z parametrów <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu. Rysowanie linii nieprzezroczyste, należy ustawić składnika alfa koloru do 255. Aby narysować półprzezroczystych linii, należy ustawić składnika alfa na wartość od 1 do 254.  
  
 Po narysowaniu półprzezroczystych linii w tle kolor linii mieszania kolorów tła. Składnik alfa określa, jak mieszane kolory tła i linii; wartości alfa niemal 0 umieść ważniejsze na kolory tła i wartości alfa niemal 255 umieść ważniejsze na kolor linii.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład map bitowych rysuje, a następnie trzy wiersze, korzystających z mapy bitowej jako tło jest rysowane. Pierwszy wiersz używa składnika alfa 255, tak aby zawierała przezroczystości. Drugi i trzeci linii używają alfa składnika 128, dzięki czemu są one półprzezroczystych; obraz tła do wierszy jest widoczny. Instrukcja, która ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwość powodująca usunięcie mieszania dla trzeciego wiersza w połączeniu z korekcja gamma.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poniższy kod.  
  
 ![Nieprzezroczystych i półprzezroczystych](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Przenikanie alfa linii i wypełnień](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Porady: zapewniają przezroczystego tła formantu](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Porady: Rysowanie nieprzezroczystych i półprzezroczystych pędzli](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
