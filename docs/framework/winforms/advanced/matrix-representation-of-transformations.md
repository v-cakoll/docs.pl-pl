---
title: "Macierzowe przedstawienie przekształcenia"
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
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10babac22fd94bd00b14b7f861fe99469d3ecbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="matrix-representation-of-transformations"></a>Macierzowe przedstawienie przekształcenia
M x n macierzy jest zbioru liczb ułożone w mln wierszy i kolumn n. Na poniższej ilustracji przedstawiono kilka macierzy.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Macierzy dwa o tym samym rozmiarze można dodać, dodając poszczególne elementy. Na poniższej ilustracji przedstawiono dwa przykłady dodanie macierzy.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 M x n macierzy można pomnożona przez macierz p x n, a wynik jest m x p macierzy. Liczba kolumn w macierzy pierwszy musi być taka sama jak liczba wierszy w drugiej macierzy. Na przykład macierzy 4 x 2 można pomnożona przez 2 x 3 macierzy do utworzenia macierzy 4 x 3.  
  
 Punkty w płaszczyźnie i wiersze i kolumny macierzy można traktować jako wektory. Na przykład (2, 5) jest wektorem o dwa składniki i (3, 7, 1) jest wektorem z trzech składników. Iloczyn dwóch wektorów jest zdefiniowane w następujący sposób:  
  
 (, b) • (c, d) = ac + bd  
  
 (, b, c) • (d, e, f) = ad + być + cf  
  
 Na przykład kropki iloczyn (2, 3) i (5, 4) jest (2)(5) + (3)(4) = 22. ILOCZYN (2, 5, 1) i (4, 3, 1) jest (2)(4) + (5)(3) + (1)(1) = 24. Należy pamiętać, że iloczyn dwóch wektorów liczbą nie inny sposób. Należy również zauważyć, można obliczyć iloczyn dwóch wektorów mieć taką samą liczbę elementów.  
  
 Let A(i, j) być wpisem w macierzy A wskazującego wiersza i kolumny jth. Na przykład A (3, 2) wpisu w macierzy A w wierszu 3 i 2 kolumny. Załóżmy, że A, B i C to macierze i AB = C. Wpisy C są obliczane w następujący sposób:  
  
 C (i, j) = (wiersz i A), • (kolumna j B)  
  
 Na poniższej ilustracji przedstawiono kilka przykładów mnożenie macierzy.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Jeśli uważasz punktu płaszczyźnie jako macierz 1 x 2, można przekształcać mnożąc przez macierz 2 x 2 tego punktu. Na poniższej ilustracji przedstawiono kilka przekształceń w punkcie (2 i 1).  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Na powyższej ilustracji przekształceń są linear — przekształcenia. Niektóre inne przekształcenia, takie jak tłumaczenia, nie są liniowej i nie może być wyrażona jako mnożenia przez macierz 2 x 2. Załóżmy, że chcesz rozpocząć punktu (2 i 1), jego obrót o 90 stopni, przekształca ją 3 jednostki w kierunku x i przekształca ją 4 jednostki w kierunku y. Można to zrobić za pomocą mnożenie macierzy, a następnie dodanie macierzy.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Przekształcenie liniową (mnożenia przez macierz 2 x 2) następuje translacja (Dodawanie 1 macierzy x 2) jest nazywany affine — przekształcenia. Zamiast przechowywania affine — przekształcenia w parze macierzy (jeden dla części liniowej) i jeden do tłumaczenia jest do przechowywania całej transformacji w macierzy 3 x 3. Aby działało, punkt w płaszczyźnie musi być przechowywany w macierzy z fikcyjnymi współrzędnych 3 x 1, 3. Zwykle technika jest zapewnienie wszystkie współrzędne 3 równa 1. Na przykład punkt (2 i 1) jest reprezentowana przez macierzy [2 1 1]. Na poniższej ilustracji przedstawiono affine — przekształcenia (obrót o 90 stopni; tłumaczenie 3 jednostki w kierunku x, 4 jednostki w kierunku y) wyrażonej w postaci mnożenia przez macierz pojedynczego 3 x 3.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 W powyższym przykładzie punktu (2 i 1) jest mapowana na punkt (2, 6). Należy pamiętać, że trzeciej kolumny macierzy 3 x 3 zawiera cyfry 0, 0, 1. Zawsze będzie wielkość liter w macierzy 3 x 3 affine — przekształcenia. Numery ważne są sześć liczb w kolumnie 1 i 2. Lewej górnej części x 2 2 macierzy odpowiada liniowej część transformacja, a pierwsze dwa wpisy w wierszu 3 tłumaczenia.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] może przechowywać affine — przekształcenia w <xref:System.Drawing.Drawing2D.Matrix> obiektu. Ponieważ trzecia kolumna reprezentujący affine — przekształcenia macierzy jest zawsze (0, 0, 1), określ tylko sześć liczb w dwóch pierwszych kolumn utworzenia <xref:System.Drawing.Drawing2D.Matrix> obiektu. Instrukcja `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` tworzy macierzy na powyższej ilustracji.  
  
## <a name="composite-transformations"></a>Composite — przekształcenia  
 Złożone przekształcenia jest sekwencją przekształcenia, co następuje innych. Należy wziąć pod uwagę macierzy i przekształcenia na poniższej liście:  
  
|||  
|-|-|  
|Macierz A|Obrót o 90 stopni|  
|Macierz B|Skalowanie przez współczynnik 2 w kierunku x|  
|Macierz C|Tłumaczenie 3 jednostki w kierunku y|  
  
 Jeśli Rozpoczniemy z punktem (2 i 1) — reprezentowany przez macierzy [2 1 1] — i pomnożyć przez, następnie B, a następnie C, (2 i 1) punktu zostaną poddane trzy przekształcenia w podanej kolejności.  
  
 [2 1 1] ABC = [1 5-2]  
  
 Zamiast niż trzy części złożone przekształcenia są przechowywane w trzech oddzielnych macierzy, należy pomnożyć A, B i C razem uzyskanie pojedynczego macierzy 3 x 3, która przechowuje całego złożone przekształcenia. Załóżmy, że ABC = D. Następnie punkt pomnożona przez D zapewnia takiego samego wyniku jako punkt pomnożona przez A, następnie B, następnie C.  
  
 [2 1 1] D = [1 5-2]  
  
 Na poniższej ilustracji przedstawiono macierzy A, B, C i D.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Fakt, że macierzy transformacji złożonego mogą powstawać przez pomnożenie macierzy transformacji poszczególnych oznacza, że wszelkie sekwencji affine — przekształcenia mogą być przechowywane w pojedynczym <xref:System.Drawing.Drawing2D.Matrix> obiektu.  
  
> [!CAUTION]
>  Kolejność złożonych transformacji jest ważna. Ogólnie rzecz biorąc, obracanie, skalowanie, a następnie wykonuje nie jest równocześnie jako skali, obracanie, następnie tłumaczenia. Podobnie ważne jest kolejnością mnożenie macierzy. Ogólnie rzecz biorąc ABC nie jest taka sama jak wykonaj KOPIĘ.  
  
 <xref:System.Drawing.Drawing2D.Matrix> Klasa udostępnia kilka metod tworzenia złożone przekształcenia: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, i <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. Poniższy przykład tworzy macierzy transformacji złożonego, najpierw obraca 30 stopni, a następnie skaluje przez współczynnik 2 w kierunku y, która przetwarza 5 jednostek w kierunku x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Na poniższej ilustracji przedstawiono macierzy.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Zobacz też  
 [Systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Używanie przekształceń w zarządzanym GDI +](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
