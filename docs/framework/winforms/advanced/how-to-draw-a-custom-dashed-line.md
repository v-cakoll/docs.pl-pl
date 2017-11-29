---
title: 'Porady: rysowanie niestandardowej linii kreskowanej'
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
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90fcc99414e8d5c9542d643677c85d4ff670f50f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Porady: rysowanie niestandardowej linii kreskowanej
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]dostępnych jest kilka typów kreska, które są wymienione w <xref:System.Drawing.Drawing2D.DashStyle> wyliczenia. Jeśli te style standard dash nie własnych potrzeb, można utworzyć niestandardowego wzorze.  
  
## <a name="example"></a>Przykład  
 Rysowanie niestandardowej linii kreskowanej, umieść długości kresek i spacji w tablicy i przypisz tablicy jako wartość <xref:System.Drawing.Pen.DashPattern%2A> właściwość <xref:System.Drawing.Pen> obiektu. Poniższy przykład rysuje niestandardowej linii kreskowanej oparte na tablicy `{5, 2, 15, 4}`. Jeśli elementy tablicy pomnożenia szerokość pióra 5, możesz uzyskać `{25, 10, 75, 20}`. Łączniki wyświetlanych alternatywny długości między 25 i 75 i przestrzeni alternatywny o długości od 10 do 20.  
  
 Na poniższej ilustracji przedstawiono wynikowa linia przerywana. Należy pamiętać, że dash końcowego musi być krótsza niż 25 jednostek tak, aby wiersz może kończyć się przy (405, 5).  
  
 ![Pióra](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie formularza systemu Windows i obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń. Wklej poprzedni kod do <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
