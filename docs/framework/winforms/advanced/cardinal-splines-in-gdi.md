---
title: Krzywe kardynalne w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
ms.openlocfilehash: 4588f6f606f0f479aeae1d143f23175ec4be32a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200418"
---
# <a name="cardinal-splines-in-gdi"></a>Krzywe kardynalne w GDI+
Krzywa kardynalna jest sekwencją poszczególnych krzywych przyłączone do formularza większych krzywej. Krzywej składanej jest określona przez tablicę punktów i parametrem napięcie. Krzywa kardynalna płynnie przechodzi przez każdy punkt w tablicy; istnieją nie ostre rogi i nie nagłych zmian w szczelność krzywej. Poniższa ilustracja przedstawia zestaw punktów i kardynalna, który przechodzi przez każdy punkt w zestawie.  
  
 ![Cardinal Spline](./media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Krzywe fizycznych i matematyczne  
 Fizyczne z krzywymi składanymi jest to cienka drewna lub innych materiałów elastyczne. Przed nadejściem krzywe matematycznych projektanci użyli krzywe fizycznej do rysowania. Projektant będzie umieścić krzywej składanej na papierze i zakotwiczyć go do danego zestawu punktów. Projektant następnie utworzyć krzywą rysowania wzdłuż krzywej składanej piórem lub ołówka. Określony zestaw punktów może przynieść szereg krzywych, w zależności od właściwości fizyczne z krzywymi składanymi. Na przykład krzywej składanej o wysokiej odporności na zginania wywołałoby krzywą innego niż z krzywymi składanymi niezwykle elastyczny.  
  
 Formuł matematycznych krzywe są uzależnione od właściwości pręty elastyczne, więc krzywych produkowane przez krzywe matematyczne są podobne do krzywych oferowanych raz przez fizyczne krzywe. Tak samo, jak krzywe fizycznego z inną napięcie dadzą różne krzywych za pośrednictwem danego zestawu punktów, matematyczne krzywe z różnymi wartościami dla parametru napięcie dadzą różne krzywych za pośrednictwem danego zestawu punktów. Poniższa ilustracja przedstawia cztery krzywe kardynalne przechodzi przez ten sam zestaw punktów. Naciągnięcie jest wyświetlane dla każdego z krzywymi składanymi. Napięcie 0 odpowiada nieskończonej napięcie fizycznych, wymuszając krzywej do wykonania w sposób możliwie najkrótszym (proste) między punktami. Napięcie 1 odpowiada nie napięcie fizycznych, dzięki czemu krzywej składanej na przepływał ścieżką najmniej całkowita odcinek łącznika. Za pomocą wartości napięcia jest większa niż 1 krzywej zachowuje się jak skompresowany platformy spring wypchnięte do używają dłuższej ścieżki.  
  
 ![Krzywe Kardynalne](./media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Cztery krzywe na powyższej ilustracji korzystają z tej samej linii stycznej z punktu początkowego. Tangens jest linią od punktu początkowego na następny punkt krzywej. Podobnie udostępniony tangens na punkt końcowy jest linią z punktu końcowego do wcześniejszego punktu krzywej.  
  
 Rysowanie krzywej kardynalnej, potrzebne jest wystąpienie <xref:System.Drawing.Graphics> klasy <xref:System.Drawing.Pen>oraz tablicę <xref:System.Drawing.Point> obiekty wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawCurve%2A> metody, która pobiera krzywej składanej, i <xref:System.Drawing.Pen> Przechowuje atrybuty z krzywymi składanymi, takich jak szerokości linii i kolorze. Tablica <xref:System.Drawing.Point> obiektów przechowuje punkty, które będzie przekazywał krzywej. Poniższy przykład kodu pokazuje sposób rysowania kardynalna, który przechodzi przez punkty w `myPointArray`. Trzeci parametr jest naciągnięcie.  
  
 [!code-csharp[LinesCurvesAndShapes#31](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także

- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Konstruowanie i rysowanie krzywych](constructing-and-drawing-curves.md)
