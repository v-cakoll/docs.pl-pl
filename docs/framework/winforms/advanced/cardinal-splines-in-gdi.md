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
ms.openlocfilehash: 93ae09c72415fa489e62f753e51e5a3ffcfb2425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cardinal-splines-in-gdi"></a>Krzywe kardynalne w GDI+
Kardynalnej krzywej składanej jest sekwencją poszczególnych krzywych przyłączone do formularza krzywej większy. Krzywej składanej jest określona przez tablicę punktów i parametr naprężenia. Kardynalnej krzywej składanej sprawnie przechodzi przez każdego punktu w tablicy; Brak nie ostre narożniki i brak niespodziewane zmian w szczelność krzywej. Na poniższej ilustracji przedstawiono zestaw punktów i kardynalnej krzywej składanej, który przechodzi przez każdego punktu w zestawie.  
  
 ![Kardynalnej krzywej składanej](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Krzywe fizycznych i matematyczne  
 Fizyczny krzywej składanej jest to alokowania drewna lub innych materiałów elastyczne. Przed zastosowaniem pojawienie matematyczne krzywe projektantów użycie krzywe fizycznych do rysowania. Projektant będzie umieścić krzywej składanej na arkuszu papieru i zakotwiczyć go do danego zestawu punktów. Projektant następnie utworzyć krzywą rysunku wzdłuż krzywej składanej piórem lub ołówka. Określony zestaw punktów wygeneruje różnych krzywych, w zależności od właściwości fizyczne krzywej składanej. Na przykład krzywej składanej o wysokiej odporności na zginania dałby w efekcie innego krzywą niż bardzo elastyczne krzywej składanej.  
  
 Formuł matematycznych krzywe są oparte na właściwości elastyczne pręty tak krzywych utworzonego przez matematyczne krzywe są podobne do krzywych raz opracowane przez krzywe fizycznych. Tak samo jak fizyczny krzywe z różnych naprężenia utworzy różnych krzywych przez podany zestaw punktów, krzywe matematyczne z różnymi wartościami dla parametru naprężenia utworzy różnych krzywych przez podany zestaw punktów. Na poniższej ilustracji przedstawiono cztery kardynalne przechodzącej przez ten sam zestaw punktów. Naciągnięcie jest wyświetlany dla każdej krzywej składanej. Naciągnięciu równym 0 odpowiada nieskończone naprężenia fizycznych, wymuszanie krzywej podjęcie sposób najmniejszej (proste) między punktami. Naprężenia 1 odpowiada nie naprężenia fizycznych, umożliwiając krzywej składanej podjęcie ścieżka najmniej całkowita odcinek łącznika. O wartościach naprężenia jest większa niż 1 krzywej zachowuje się jak spring skompresowany, przypisany do zająć dłuższą ścieżkę.  
  
 ![Krzywe Kardynalne](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Cztery krzywe na powyższej ilustracji korzystają z tej samej linii stycznej z punktu początkowego. Tangens jest linią od punktu początkowego do następnego punktu krzywej. Podobnie udostępnionych tangens na punkt końcowy jest linią pobierane z punktu końcowego do poprzedniego punktu krzywej.  
  
 Aby narysować kardynalnej krzywej składanej, należy wystąpienie <xref:System.Drawing.Graphics> klasy, <xref:System.Drawing.Pen>i tablica <xref:System.Drawing.Point> obiekty wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawCurve%2A> metodę, która pobiera krzywej składanej, i <xref:System.Drawing.Pen> Przechowuje atrybuty krzywej składanej, takie jak szerokość linii i kolor. Tablica <xref:System.Drawing.Point> obiektów przechowuje punkty, które będzie przekazywał krzywej. Poniższy przykład kodu pokazuje sposób rysowania kardynalnej krzywej składanej, który przechodzi przez punkty w `myPointArray`. Trzeci parametr jest naciągnięcie.  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz też  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Konstruowanie i rysowanie krzywych](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
