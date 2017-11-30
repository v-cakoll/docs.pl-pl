---
title: "Porady: zmienianie kolorów"
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
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f89bb5d87ef58c5ecda7be4cb9fb41da08e8a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-shear-colors"></a>Porady: zmienianie kolorów
Pochylanie zwiększa lub zmniejsza składnika kolor przez kwotę proporcjonalny do innego składnika kolorów. Rozważmy na przykład przekształcania, gdzie składnika czerwony zwiększa się o połowę wartość składnika niebieski. W takiej transformacji kolorów (0,2, 0,5, 1) może stać się (0,7, 0,5, 1). Nowy składnik red jest wymagane 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars4.bmp. Następnie kod stosuje transformację Ścinanie opisane w poprzednim akapicie do każdego piksela w obrazie.  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i pochylone obraz po prawej stronie.  
  
 ![Zmienianie kolorów](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po przekształceniu Ścinanie.  
  
|Oryginał|Ścięty|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Zastąp `ColorBars.bmp` nazwę obrazu oraz ścieżki jest prawidłowy w tym systemie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Ponowne kolorowanie obrazów](../../../../docs/framework/winforms/advanced/recoloring-images.md)
