---
title: Macierzowe przedstawienie transformacji
ms.date: 03/30/2017
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
ms.openlocfilehash: c87be8eaf715e373da75dd8f91889b0e396dba0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172786"
---
# <a name="matrix-representation-of-transformations"></a>Macierzowe przedstawienie transformacji
M x n macierzy jest zbioru liczb rozmieszczone w mln wierszy i kolumn n. Poniższa ilustracja przedstawia kilka macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Możesz dodać dwa macierzy o tym samym rozmiarze, dodając poszczególne elementy. Na poniższej ilustracji przedstawiono dwa przykłady dodanie macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 M x n macierzy można pomnożona przez macierz p n x, a wynik jest macierzy p "x" m. Liczba kolumn w pierwszym macierzy musi być taka sama jak liczba wierszy w drugiej macierzy. Na przykład macierzy 4 x 2 można pomnożona przez 2 macierzy x 3, aby wygenerować macierzy 4 x 3.  
  
 Punkty w płaszczyźnie i wierszy i kolumn w macierzy może być uważane za wektorami. Na przykład (2, 5) jest wektora z dwoma składnikami i (3, 7, 1) jest wektorem z trzech składników. Iloczyn dwóch wektorów jest zdefiniowana w następujący sposób:  
  
 (, b) • (c, d) = ac + bd  
  
 (, b, c) • (d, e, f) = ad + być + cf  
  
 Na przykład kropki iloczyn (2, 3) i (5, 4) jest (2)(5) + (3)(4) = 22. ILOCZYN (2, 5, 1) i (4, 3, 1) jest (2)(4) + (5)(3) + (1)(1) = 24. Należy pamiętać, że iloczyn dwóch wektorów jest liczbą, a nie inny sposób. Należy również zauważyć, można obliczyć iloczyn tylko wtedy, gdy dwa wektory mają taką samą liczbę składników.  
  
 Pozwól A(i, j) się wpis w macierzy A ię od wiersza i kolumny jth. Na przykład A (3, 2) wpis w macierzy A w wierszu 3 i 2 kolumny. Załóżmy, że A, B i C są macierzach i AB = C. Wpisy C są obliczane w następujący sposób:  
  
 C (i, "j") = (wiersz i A), • (kolumna "j" B)  
  
 Na poniższej ilustracji przedstawiono kilka przykładów mnożenie macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Jeśli Twoim zdaniem punktu płaszczyźnie jako 1 macierzy x 2, mnożąc przez macierz 2 x 2 można przekształcać tego punktu. Poniższa ilustracja przedstawia kilka przekształcenia w punkcie, (2, 1).  
  
 ![Przekształcenia](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Wszystkie przekształcenia zostało pokazane na poprzedniej ilustracji są linear — przekształcenia. Niektóre inne transformacji, takich jak tłumaczenia, nie są liniowe, a nie może być wyrażona jako mnożenia przez macierz 2 x 2. Załóżmy, że chcesz rozpocząć od punktu, (2, 1), Obróć go o 90 stopni, przekształca ją 3 jednostki w kierunku x i przekształca ją 4 jednostek w kierunku y. Można to zrobić za pomocą mnożenie macierzy, a następnie dodanie macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Liniowy transformacji (mnożenie przez macierz 2 x 2), następuje tłumaczenia (Dodawanie 1 macierzy x 2) jest nazywany affine — przekształcenia. Alternatywa dla przechowywania affine — przekształcenia w parze macierzy (jeden dla części liniowych) i jeden dla tłumaczenie jest do przechowywania cały przekształcenia w macierzy 3 x 3. Aby działało, punkt na płaszczyźnie muszą być przechowywane w macierzy x 1, 3, za pomocą fikcyjnego współrzędnych 3. Zwykle techniką jest zapewnienie wszystkie współrzędne 3rd równa 1. Na przykład punkt, (2, 1) jest reprezentowany przez macierz [2 1 1]. Na poniższej ilustracji przedstawiono affine — przekształcenia (obrót o 90 stopni; tłumaczenie 3 jednostki w kierunku x, 4 jednostek w kierunku y) wyrażonej w postaci mnożenia przez macierz pojedynczego 3 x 3.  
  
 ![Przekształcenia](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 W powyższym przykładzie punktu, (2, 1) jest mapowany do punktu, (2, 6). Należy pamiętać, że trzecia kolumna macierzy 3 x 3 zawiera cyfry od 0, 0, 1. Zawsze będzie w przypadku macierzy 3 x 3 affine — przekształcenia. Numery ważne są sześć cyfr w kolumnach 1 i 2. Lewa górna 2 x 2 część macierzy odpowiada liniowej część przekształcenie, a pierwsze dwie pozycje w wierszu 3 tłumaczenia.  
  
 ![Przekształcenia](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można przechowywać affine — przekształcenia w <xref:System.Drawing.Drawing2D.Matrix> obiektu. Ponieważ trzecia kolumna macierzy, który reprezentuje affine — przekształcenia jest zawsze (0, 0, 1), określ tylko sześć cyfr w pierwszych dwóch kolumn będących jej podczas konstruowania <xref:System.Drawing.Drawing2D.Matrix> obiektu. Wykonywanie instrukcji `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` tworzy macierzy pokazano na poprzednim rysunku.  
  
## <a name="composite-transformations"></a>Composite — przekształcenia  
 Złożone przekształcenia to sekwencja przekształceń, jeden następuje drugiego. Należy wziąć pod uwagę macierzy, a przekształcenia na poniższej liście:  
  
|||  
|-|-|  
|Tabela A|Obrót o 90 stopni|  
|Tabela B|Możesz zmieniać skalę, współczynnik 2 w kierunku x|  
|Matrix C|Tłumaczenie 3 jednostki w kierunku y|  
  
 Gdy Rozpoczniemy pracę punktu, (2, 1) — reprezentowany przez macierz [2 1 1] — i mnożenia, następnie B, a następnie C, punkt, (2, 1), zostaną poddane trzy przekształcenia w podanej kolejności.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Raczej niż trzy części złożone przekształcenia są przechowywane w trzech oddzielnych macierzy, należy pomnożyć A, B i C ze sobą można pobrać jednej macierzy 3 x 3, która przechowuje cały przekształcenia złożonego. Załóżmy, że ABC = D. Następnie punkt pomnożona przez D daje ten sam wynik jako punkt pomnożona przez A, następnie B, następnie C.  
  
 [2 1 1]D = [-2 5 1]  
  
 Na poniższej ilustracji przedstawiono macierzy, A, B, C i D.  
  
 ![Przekształcenia](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Fakt, że macierzy transformacji złożonych mogą powstawać przez mnożenie macierzy transformacji poszczególnych oznacza, że dowolnej sekwencji affine — przekształcenia mogą być przechowywane w jednej <xref:System.Drawing.Drawing2D.Matrix> obiektu.  
  
> [!CAUTION]
>  Kolejność złożonych transformacji jest ważna. Ogólnie rzecz biorąc, obracanie, skalowanie, a następnie tłumaczenie jest nie sam jako skali, obracanie, następnie tłumaczenie. Podobnie ważne jest kolejność mnożenie macierzy. Ogólnie rzecz biorąc ABC nie jest taka sama jak KOPIE.  
  
 <xref:System.Drawing.Drawing2D.Matrix> Klasa udostępnia kilka metod do tworzenia złożonych transformacji: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, i <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. Poniższy przykład tworzy macierzy transformacji złożonego, najpierw obraca się 30 stopni, a następnie skaluje się o 2 w kierunku y, która przetwarza 5 jednostek w kierunku x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Poniższa ilustracja przedstawia macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Zobacz także

- [Systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md)
- [Używanie przekształceń w zarządzanym GDI+](using-transformations-in-managed-gdi.md)
