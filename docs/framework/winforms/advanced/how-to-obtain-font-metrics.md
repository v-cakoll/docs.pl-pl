---
title: 'Porady: uzyskiwanie miar czcionek'
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
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b45f3f903c02d056fc457b652b01fb7b59413a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-font-metrics"></a>Porady: uzyskiwanie miar czcionek
<xref:System.Drawing.FontFamily> Klasa udostępnia następujące metody pobierające różnych metryk dla określonej rodziny i stylu kombinacji:  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Liczby zwrócone przez te metody znajdują się w jednostki projektu czcionki, dzięki czemu są one niezależnie od rozmiaru i jednostki konkretnej <xref:System.Drawing.Font> obiektu.  
  
 Na poniższej ilustracji przedstawiono różne metryki.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metryki regularne styl rodziny czcionek Arial. Kod tworzy również <xref:System.Drawing.Font> obiektu (w oparciu Arial rodziny) o rozmiarze 16 pikseli i przedstawia metryki (w pikselach) dla tego określonego <xref:System.Drawing.Font> obiektu.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe przykładowy kod.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")  
  
 Należy pamiętać, pierwsze dwa wiersze danych wyjściowych na powyższej ilustracji. <xref:System.Drawing.Font> o rozmiarze 16, podaje obiektu i <xref:System.Drawing.FontFamily> obiektu zwraca wysokość em 2048. Te dwie liczb (16 i 2048) są kluczem do konwersji między jednostkami projektowania czcionki i jednostki (w tym przypadku pikselach) <xref:System.Drawing.Font> obiektu.  
  
 Na przykład można konwertować wzrastająca z projektu jednostki do pikseli w następujący sposób:  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")  
  
 Poniższy kod umieszcza tekst w pionie, ustawiając <xref:System.Drawing.PointF.Y%2A> elementu członkowskiego danych <xref:System.Drawing.PointF> obiektu. Współrzędna y jest zwiększana o `font.Height` dla każdego nowego wiersza tekstu. <xref:System.Drawing.Font.Height%2A> Właściwość <xref:System.Drawing.Font> obiektu zwraca wierszami (w pikselach) dla tego określonego <xref:System.Drawing.Font> obiektu. W tym przykładzie numer zwrócone przez <xref:System.Drawing.Font.Height%2A> jest 19. Należy pamiętać, że jest to ten sam numer (zaokrąglona w górę do liczby całkowitej) uzyskane konwertując Metryka odstępów między wierszami pikseli.  
  
 Należy pamiętać, że wysokość em (nazywanych również rozmiar rozmiar lub em) nie jest sumą wzrastająca i spadku. Suma wzrastająca i spadku jest nazywany wysokość komórki. Wysokość komórki minus wewnętrzny początkowy jest równa wysokość elementu. Wysokość komórki oraz wiodące zewnętrzne jest równa wierszami.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
