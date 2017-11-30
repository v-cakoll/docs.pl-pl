---
title: "Porady: rysowanie linii wypełnionej teksturą"
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
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33374a16e6fee80dd45227acd4c5860d5bfc4545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Porady: rysowanie linii wypełnionej teksturą
Zamiast rysowania linii jednolitym kolorem, można Rysowanie linii z tekstury. Rysowanie linii i krzywych teksturą, Utwórz <xref:System.Drawing.TextureBrush> obiektu i przekazać który <xref:System.Drawing.TextureBrush> do obiektu <xref:System.Drawing.Pen.%23ctor%2A> konstruktora. Mapa bitowa skojarzone z pędzla tekstury służy do kafelka płaszczyzny (sposób niewidoczny), i gdy Pióro rysuje linię lub krzywą, obrysu pióra odkrywa niektórych pikseli tekstury sąsiadującym.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Bitmap> obiektów z pliku `Texture1.jpg`. Tej mapy bitowej jest używany do tworzenia <xref:System.Drawing.TextureBrush> obiektu, a <xref:System.Drawing.TextureBrush> obiekt jest używany do utworzenia <xref:System.Drawing.Pen> obiektu. Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> rysuje mapy bitowej z jego lewego górnego rogu na (0, 0). Wywołanie <xref:System.Drawing.Graphics.DrawEllipse%2A> używa <xref:System.Drawing.Pen> obiektu do rysowania teksturą elipsy.  
  
 Na poniższej ilustracji przedstawiono mapy bitowej i teksturą elipsy.  
  
 ![Pióra](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie formularza systemu Windows i obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń. Wklej poprzedni kod do <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Zastąp `Texture.jpg` wraz z obrazem, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
