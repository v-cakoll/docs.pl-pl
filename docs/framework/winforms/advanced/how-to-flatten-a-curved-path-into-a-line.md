---
title: 'Instrukcje: Spłaszczanie ścieżki krzywej do linii'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a151b4244e14d3704fd5fa1c55de92211981232f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781364"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Instrukcje: Spłaszczanie ścieżki krzywej do linii
A <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt przechowuje sekwencji linii i krzywych Beziera. Można dodać kilka typów krzywych (wielokropek, łuki kardynalne) do ścieżki, ale każda krzywa jest konwertowany na krzywej Beziera, zanim znajduje się w ścieżce. Spłaszczanie ścieżki składa się z konwersji każdego krzywej Beziera w ścieżce z linii prostych sekwencji. Na poniższej ilustracji przedstawiono ścieżkę przed i po nim spłaszczanie.  
  
 ![Proste linii i krzywych](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Spłaszczanie ścieżki  
  
- Wywołaj <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metody <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metoda otrzymuje argument płaskość, który określa maksymalną odległość między ścieżką spłaszczone i Oryginalna ścieżka.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Konstruowanie i rysowanie ścieżek](constructing-and-drawing-paths.md)
