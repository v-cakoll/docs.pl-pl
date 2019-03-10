---
title: Przenikanie alfa linii i wypełnień
ms.date: 03/30/2017
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
ms.openlocfilehash: 7a8286fb741effaf668b87e90da04f79d1490de2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716000"
---
# <a name="alpha-blending-lines-and-fills"></a>Przenikanie alfa linii i wypełnień
W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], kolor, który jest wartością 32-bitowych 8 bitów dla alpha, czerwony, zielony i niebieski. Wartość alfa odpowiadającą wskazuje Przezroczystość koloru — zakres, do których kolor jest zmieszana kolorem tła. Wartości alfa z zakresu od 0 do 255, gdzie 0 reprezentuje w pełni przezroczyste kolor, a 255 reprezentuje kolor, który całkowicie nieprzezroczyste.  
  
 Przenikanie alfa jest poszczególne piksele mieszania danych koloru źródłowego i tła. Każdy z trzech składników koloru danego źródła (czerwony, zielony, niebieski) jest zmieszana przy użyciu odpowiadającego składnika koloru tła, zgodnie z następującą formułę:  
  
 displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255  
  
 Na przykład załóżmy, że składnik czerwony kolor źródłowy jest 150 i czerwony składnik kolor tła to 100. Jeśli wartość alfa odpowiadającą jest równy 200, składnik czerwony kolor wynikowy jest obliczana w następujący sposób:  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii](how-to-draw-opaque-and-semitransparent-lines.md)  
 Pokazuje, jak rysowanie linii mieszane alfa.  
  
 [Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Wyjaśnia, jak mieszania alfa, przy użyciu pędzli.  
  
 [Instrukcje: Stosowanie trybu składania do sterowania przenikaniem alfa](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 W tym artykule opisano sposób sterowania przenikaniem alfa, za pomocą <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Instrukcje: Stosowanie macierzy kolorów ustawiania wartości alfa na obrazach](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Opis sposobu użycia <xref:System.Drawing.Imaging.ColorMatrix> obiektu do sterowania przenikaniem alfa.
