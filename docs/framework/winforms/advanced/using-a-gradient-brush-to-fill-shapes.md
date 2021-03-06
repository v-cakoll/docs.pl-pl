---
title: Używanie pędzla gradientów do wypełniania kształtów
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 7ff555ba4fd81e9123e5f9e9feed38a0ec9d0a08
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063593"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Używanie pędzla gradientów do wypełniania kształtów
Można użyć pędzla gradientów do wypełnienia kształtu przy użyciu stopniowo Zmienianie koloru. Na przykład można użyć poziomy gradientu do wypełnienia kształtu przy użyciu koloru, który stopniowo zmienia się po przeniesieniu od lewej krawędzi kształtu do prawej krawędzi. Wyobraź sobie prostokąt przy lewej krawędzi, czarne (reprezentowane przez składniki czerwony, zielony i niebieski, 0, 0, 0) i prawej krawędzi to znaczy red (reprezentowany przez 255, 0, 0). Jeśli prostokąt 256 pikseli, składnik czerwony piksela podanego będzie większa o jeden od składnik czerwony piksela po lewej stronie. Skrajnie po lewej stronie piksel w wierszu etapy kolorów (0, 0, 0), drugi pikseli posiada (1, 0, 0), trzeci pikseli (2, 0, 0) i tak dalej, aż dojdziesz do piksela po prawej stronie zawiera składniki kolorów (255, 0, 0). Te wartości kolorów interpolowane tworzą kolor gradientu.  
  
 Gradient liniowy zmienia kolor, jak przenieść poziomie, w pionie lub równoległe do określonego wiersza pochyłego. Gradientu ścieżki zmienia kolor po przeniesieniu o wewnętrznych i granicy ścieżki. Można dostosować gradienty ścieżki do osiągnięcia szerokiej gamy efekty.  
  
 Poniższa ilustracja przedstawia, prostokąt wypełnione pędzel gradientów liniowych i elipsy wypełnione pędzla gradientu ścieżki:  
  
 ![Prostokąt wypełniony pędzla gradientów z elipsę.](./media/using-a-gradient-brush-to-fill-shapes/rectangle-ellipse-gradient-brush.png)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie gradientu liniowego](how-to-create-a-linear-gradient.md)  
 Pokazuje, jak tworzenie gradientu liniowego użyciu <xref:System.Drawing.Drawing2D.LinearGradientBrush> klasy.  
  
 [Instrukcje: Tworzenie gradientu ścieżki](how-to-create-a-path-gradient.md)  
 Opisuje sposób Tworzenie gradientu ścieżki przy użyciu <xref:System.Drawing.Drawing2D.PathGradientBrush> klasy.  
  
 [Instrukcje: Stosowanie korekcji Gamma do gradientu](how-to-apply-gamma-correction-to-a-gradient.md)  
 Wyjaśnia, jak za pomocą usług korekcja gamma pędzla gradientu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.
