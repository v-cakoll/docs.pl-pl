---
title: "Porady: stosowanie trybu składania do sterowania przenikaniem alfa"
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
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564d46cb2d72ac63962657b39146489aaafd6a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Porady: stosowanie trybu składania do sterowania przenikaniem alfa
Może to być razy, gdy chcesz utworzyć ukrytej mapy bitowej, który ma następującą charakterystykę:  
  
-   Kolory przyjmują wartości alfa, które są mniej niż 255.  
  
-   Kolory nie są alfa mieszane ze sobą, podczas tworzenia mapy bitowej.  
  
-   Podczas wyświetlania mapy bitowej Zakończono kolorów w mapie bitowej są przenikaniem przy użyciu kolorów tła na urządzenia wyświetlającego alfa.  
  
 Aby utworzyć mapę bitową, należy utworzyć pusty <xref:System.Drawing.Bitmap> obiekt, a następnie utworzyć <xref:System.Drawing.Graphics> obiektu oparte na tej mapy bitowej. Ustawianie trybu składania <xref:System.Drawing.Graphics> do obiektu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Graphics> na podstawie obiektu <xref:System.Drawing.Bitmap> obiektu. W kodzie użyto <xref:System.Drawing.Graphics> obiektu wraz z dwóch półprzezroczystych pędzli (alfa = 160) do malowania mapy bitowej. Kod wypełnia red elipsy i elipsy zielony, przy użyciu półprzezroczystych pędzli. Zielony elipsy pokrywa się czerwone elipsy, ale zielonego nie jest przejściowe z czerwonym, ponieważ tryb składania <xref:System.Drawing.Graphics> obiektu ma ustawioną wartość <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 Kod rysuje mapy bitowej na ekranie dwa razy: raz na białe tło i raz w różnych kolorach tła. Pikseli w mapie bitowej będących częścią dwie elipsy ma składnika alfa 160, więc wielokropek są mieszane z kolorów tła na ekranie.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe w przykładzie kodu. Należy pamiętać, że wielokropek są mieszane w tle, ale nie są one mieszane ze sobą.  
  
 ![Źródło kopiowania](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 Przykładowy kod zawiera tej instrukcji:  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Wielokropek na przejściowe, ze sobą, a także w tle, zmienić tej instrukcji do następującego:  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poprawione kodu.  
  
 ![Źródło przez](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Przenikanie alfa linii i wypełnień](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
