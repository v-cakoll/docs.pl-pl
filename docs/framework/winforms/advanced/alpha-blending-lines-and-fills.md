---
title: "Przenikanie alfa linii i wypełnień"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b3c0ee3ec82d4d8447c43b7dc9b275591ebe890
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="alpha-blending-lines-and-fills"></a>Przenikanie alfa linii i wypełnień
W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], kolor jest 32-bitową wartość z 8 bitów dla alpha, czerwony, zielony i niebieski. Wartości alfa wskazuje Przezroczystość koloru — zakresu, do którego kolor mieszania kolorem tła. Wartości alfa należą do zakresu od 0 do 255, gdzie 0 oznacza całkowicie przezroczysty kolor, a 255 reprezentuje kolor całkowicie nieprzezroczyste.  
  
 Przenikanie alfa jest mieszanie poszczególne piksele dane koloru źródłowego i tła. Wszystkie trzy składniki (czerwony, zielony, niebieski) koloru danego źródła jest mieszane z odpowiadającego składnika kolor tła według następującego wzoru:  
  
 displayColor = sourceColor × alfa / 255 + x backgroundColor (255 — alfa) / 255  
  
 Na przykład załóżmy, że składnik red koloru źródłowego jest 150 i kolor tła składnika czerwony to 100. Jeśli alfa wartość 200, składnika czerwony wynikowe koloru jest obliczana w następujący sposób:  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Rysowanie nieprzezroczystych i półprzezroczystych linii](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 Pokazuje, jak do rysowania linii przenikaniem alfa.  
  
 [Porady: Rysowanie nieprzezroczystych i półprzezroczystych pędzli](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Wyjaśniono, jak program blend alfa pędzli.  
  
 [Porady: stosowanie trybu składania do sterowania przenikaniem alfa](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Zawiera opis sposobu kontrolowania przenikanie alfa przy użyciu <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Wyjaśniono, jak używać <xref:System.Drawing.Imaging.ColorMatrix> obiekt do kontrolowania przenikanie alfa.
