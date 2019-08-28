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
ms.openlocfilehash: 24da407de24a924a68466e4301cc3f4a74cb2e94
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044253"
---
# <a name="matrix-representation-of-transformations"></a>Macierzowe przedstawienie transformacji
Macierz m × n to zbiór liczb uporządkowanych w wierszach m i n kolumnach. Na poniższej ilustracji przedstawiono kilka macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Można dodać dwie macierze o tym samym rozmiarze, dodając poszczególne elementy. Na poniższej ilustracji przedstawiono dwa przykłady dodawania macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Macierz m × n można pomnożyć przez macierz n × p, a wynikiem jest macierz m × p. Liczba kolumn w pierwszej macierzy musi być taka sama jak liczba wierszy w drugiej macierzy. Na przykład macierz 4 × 2 można mnożyć przez macierz 2 × 3, aby utworzyć macierz 4 × 3.  
  
 Punkty w płaszczyźnie i wierszach oraz kolumny macierzy można traktować jako wektory. Na przykład (2, 5) to wektor z dwoma składnikami, a (3, 7, 1) jest wektorem z trzema składnikami. Iloczyn kropki dwóch wektorów jest zdefiniowany w następujący sposób:  
  
 (a, b) • (c, d) = AC + BD  
  
 (a, b, c) • (d, e, f) = AD + być + CF  
  
 Na przykład iloczyn kropki (2, 3) i (5, 4) ma wartość (2) (5) + (3) (4) = 22. Iloczyn kropki (2, 5, 1) i (4, 3, 1) ma wartość (2) (4) + (5) (3) + (1) (1) = 24. Należy zauważyć, że iloczyn kropki dwóch wektorów jest liczbą, a nie innym wektorem. Należy również zauważyć, że można obliczyć iloczyn kropki tylko wtedy, gdy dwa wektory mają tę samą liczbę składników.  
  
 Niech A (i, j) to wpis w macierzy A w wierszu i kolumnie jth. Na przykład (3, 2) to wpis w macierzy A w wierszu trzeci i w drugiej kolumnie. Załóżmy, że A, B i C są macierzami i AB = C. Wpisy C są obliczane w następujący sposób:  
  
 C (i, j) = (wiersz i A) • (kolumna j z B)  
  
 Na poniższej ilustracji przedstawiono kilka przykładów mnożenia macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Jeśli uważasz, że punkt w płaszczyźnie jest tablicą 1 × 2, możesz przekształcić ten punkt przez pomnożenie go przez macierz 2 × 2. Na poniższej ilustracji przedstawiono kilka transformacji zastosowanych do punktu (2, 1).  
  
 ![Przekształcenia](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Wszystkie przekształcenia pokazane na powyższym rysunku to przekształcenia liniowe. Niektóre inne przekształcenia, takie jak translation, nie są liniowe i nie mogą być wyrażone jako mnożenie przez macierz 2 × 2. Załóżmy, że chcesz zacząć od punktu (2, 1), obrócić go o 90 stopni, przetłumaczyć jednostki IT w kierunku x i przetłumaczyć jednostki na 4 w kierunku y. Można to osiągnąć za pomocą mnożenia macierzy, po którym następuje dodanie macierzy.  
  
 ![Przekształcenia](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Transformacja liniowa (iloczyn mnożenia przez macierz 2 × 2), po której następuje tłumaczenie (dodanie macierzy 1 × 2) jest nazywane przekształcaniem afinicznym. Alternatywą do przechowywania transformacji afinicznym w parze macierzy (jednej dla części liniowej i jednej dla tłumaczenia) jest przechowywanie całego przekształcenia w macierzy 3 × 3. Aby to zrobić, punkt w płaszczyźnie musi być przechowywany w macierzy 1 × 3 z manekinem trzeciej współrzędnej. Typową techniką jest, że wszystkie trzecie współrzędne są równe 1. Na przykład punkt (2, 1) jest reprezentowany przez macierz [2 1 1]. Na poniższej ilustracji przedstawiono transformację afinicznym (obrót 90 stopni; translacja 3 jednostek w kierunku x, 4 jednostki w kierunku y) wyrażona jako iloczyn jednej macierzy 3 × 3.  
  
 ![Przekształcenia](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 W poprzednim przykładzie punkt (2, 1) jest mapowany na punkt (2, 6). Zwróć uwagę, że trzecia kolumna macierzy 3 x 3 zawiera liczby 0, 0, 1. Zawsze będzie to miało zastosowanie w przypadku macierzy 3 x 3 afinicznym transformacji. Ważne liczby to sześć cyfr w kolumnach 1 i 2. Górna lewa część 2 × 2 macierzy reprezentuje część liniową przekształcenia, a pierwsze dwa wpisy w trzecim wierszu reprezentują tłumaczenie.  
  
 ![Przekształcenia](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 W programie GDI+ można przechowywać transformację afinicznym w <xref:System.Drawing.Drawing2D.Matrix> obiekcie. Ponieważ trzecia kolumna macierzy, która reprezentuje transformację afinicznym, jest zawsze (0, 0, 1), podczas konstruowania <xref:System.Drawing.Drawing2D.Matrix> obiektu należy określić tylko sześć cyfr w pierwszych dwóch kolumnach. Instrukcja `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` konstruuje matrycę pokazaną na powyższym rysunku.  
  
## <a name="composite-transformations"></a>Przekształcenia złożone  
 Transformacja złożona to sekwencja przekształceń, po której następują inne. Rozważ macierze i przekształcenia na poniższej liście:  
  
|||  
|-|-|  
|Macierz A|Obróć o 90 stopni|  
|Macierz B|Skalowanie według współczynnika 2 w kierunku x|  
|Matrix C|Translacja 3 jednostek w kierunku y|  
  
 Jeśli zaczynamy od punktu (2, 1), reprezentowanego przez macierz [2 1 1] — i pomnóż przez, a następnie B, a następnie C, punkt (2, 1) przejdzie trzy przekształcenia w podanej kolejności.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Zamiast przechowywać trzy części transformacji złożonej w trzech oddzielnych macierzach, można pomnożyć A, B i C, aby uzyskać jedną macierz 3 × 3, w której jest przechowywana cała transformacja złożona. Załóżmy, że ABC = D. Następnie punkt pomnożony przez D daje ten sam wynik jako punkt pomnożony przez, a następnie B, C.  
  
 [2 1 1]D = [-2 5 1]  
  
 Na poniższej ilustracji przedstawiono macierze A, B, C i D.  
  
 ![Przekształcenia](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Fakt, że macierz transformacji złożonej można utworzyć przez pomnożenie pojedynczych macierzy transformacji oznacza, że każda sekwencja transformacji afinicznym może być przechowywana w pojedynczym <xref:System.Drawing.Drawing2D.Matrix> obiekcie.  
  
> [!CAUTION]
> Kolejność transformacji złożonej jest ważna. Ogólnie rzecz biorąc, Obróć, a następnie Skaluj, a następnie Przekształć nie jest taki sam jak skala, a następnie Obróć, a następnie Przekształć. Podobnie kolejność mnożenia macierzy jest ważna. Ogólnie rzecz biorąc, ABC nie jest taka sama jak BK.  
  
 <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A> <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A> <xref:System.Drawing.Drawing2D.Matrix.Scale%2A> <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>Klasa zawiera kilka metod tworzenia transformacji złożonej: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>,, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>,, i. <xref:System.Drawing.Drawing2D.Matrix> Poniższy przykład tworzy macierz transformacji złożonej, która najpierw obraca 30 stopni, a następnie skaluje współczynnik 2 w kierunku y, a następnie tłumaczy 5 jednostek w kierunku x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Na poniższej ilustracji przedstawiono macierz.  
  
 ![Przekształcenia](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Zobacz także

- [Systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md)
- [Używanie przekształceń w zarządzanym GDI+](using-transformations-in-managed-gdi.md)
