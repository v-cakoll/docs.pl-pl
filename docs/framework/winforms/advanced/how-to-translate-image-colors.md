---
title: "Porady: przesuwanie kolorów obrazu"
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
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c21d20b631d8e0cf68e370dd43b3f5e92144b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-translate-image-colors"></a>Porady: przesuwanie kolorów obrazu
Tłumaczenie dodaje wartość do przynajmniej jednej z czterech składowych. Wpisów macierzy kolorów, które reprezentują tłumaczenia są podane w poniższej tabeli.  
  
|Składnik do tłumaczenia|Wpis macierzy|  
|--------------------------------|------------------|  
|czerwony|[4][0]|  
|zielony|[4][1]|  
|niebieski|[4][2]|  
|Alpha|[4][3]|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars.bmp. Następnie kod dodaje 0,75 do składnika czerwony każdego piksela obrazu. Oryginalnego obrazu jest rysowane obok przekształcone obrazu.  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i przekształcony obraz po prawej stronie.  
  
 ![Translacja kolorów](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po translacji czerwony. Należy pamiętać, że maksymalna wartość dla składnika kolor jest 1, składnika czerwony w drugim wierszu nie zmienia się. (Podobnie, wartość minimalna dla składnika kolor jest 0).  
  
|Oryginał|Tłumaczenie|  
|--------------|----------------|  
|Czarne (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Czerwony (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Kolor zielony (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Niebieski (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Zastąp `ColorBars.bmp` nazwę pliku obrazu oraz ścieżki, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Ponowne kolorowanie obrazów](../../../../docs/framework/winforms/advanced/recoloring-images.md)
