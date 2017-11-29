---
title: "Używanie pędzla gradientów do wypełniania kształtów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a1c4ab7c2ee6f7164b6158dcb4ca4721be12650
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Używanie pędzla gradientów do wypełniania kształtów
Pędzla gradientów służy do wypełnienia kształtu zmieniających się stopniowo kolorem. Na przykład umożliwia poziome gradientu wypełnienia kształtu kolorem, który zmienia stopniowo podczas przenoszenia od lewej krawędzi kształtu do prawej krawędzi. Wyobraź sobie prostokąt z lewej krawędzi, czarne (reprezentowane przez składniki czerwony, zielonemu i niebieskiemu, 0, 0, 0) i prawej krawędzi czyli czerwony (reprezentowane przez 255, 0, 0). Jeśli prostokąt 256 pikseli szerokości, składnika czerwony danego piksela będzie dłuższą o jeden niż składnika czerwony piksela po lewej stronie. Po lewej stronie piksel w wierszu zawiera składniki kolorów (0, 0, 0), drugi pikseli ma (1, 0, 0), trzeci pikseli ma (2, 0, 0) i tak dalej, aż do piksela po prawej stronie zawiera składniki kolorów (255, 0, 0). Te wartości kolorów interpolowane tworzą kolor gradientu.  
  
 Gradient liniowy zmienia kolor, Przenieś poziomie, w pionie lub równoległe do określonego wiersza pochyłe. Gradientu ścieżki zmienia kolor, jak przenieść o wewnętrznych i granicy ścieżki. Gradienty ścieżki do osiągnięcia szerokiej gamy efekty można dostosować.  
  
 Na poniższej ilustracji przedstawiono wypełniony prostokąt z pędzla gradientu liniowego i elipsy wypełniany pędzla gradientu ścieżki.  
  
 ![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Tworzenie gradientu liniowego](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 Przedstawia sposób tworzenia gradientu liniowego użyciu <xref:System.Drawing.Drawing2D.LinearGradientBrush> klasy.  
  
 [Porady: Tworzenie gradientu ścieżki](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 Opisuje sposób Tworzenie gradientu ścieżki przy użyciu <xref:System.Drawing.Drawing2D.PathGradientBrush> klasy.  
  
 [Porady: stosowanie korekcji Gamma do gradientu](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 Wyjaśniono, jak używać korekcja gamma z pędzla gradientu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.
