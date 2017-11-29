---
title: Konstruowanie i rysowanie krzywych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 801af10f7b9e5e7998fc061537977c5bced6bdb3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="constructing-and-drawing-curves"></a>Konstruowanie i rysowanie krzywych
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]obsługuje kilka typów krzywych: wielokropek, łuki kardynalne i krzywych Beziera. Elipsy jest definiowana za pomocą prostokątem; Łuk jest częścią elipsy zdefiniowany przez kąt początkowy i kąta odchylenia. Kardynalnej krzywej składanej jest definiowana za pomocą tablicy punktów i parametr naprężenia — krzywej sprawnie przechodzi przez każdego punktu w macierzy, a parametr naprężenia wpływa na sposób załamania krzywej. Krzywej Beziera jest zdefiniowany przez dwa punkty końcowe i dwa punkty kontrolne, które krzywej nie przechodzi przez punkty kontrolne, ale punktów kontrolnych wpływ kierunek i zakrzywia, ponieważ krzywej przechodzi od jeden punkt końcowy do drugiego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Rysowanie krzywych kardynalnych](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 Opisuje kardynalne oraz rysowania.  
  
 [Porady: Rysowanie pojedynczej krzywej Beziera](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 Opisuje krzywej Beziera oraz jedną rysowania.  
  
 [Porady: Rysowanie sekwencji krzywych Beziera](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 Wyjaśniono, jak rysowanie krzywych Beziera kilka w sekwencji.
