---
title: Wymiary tablic w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053720"
---
# <a name="array-dimensions-in-visual-basic"></a>Wymiary tablic w Visual Basic
A *wymiaru* jest kierunek, w którym mogą się różnić specyfikację elementów tablicy. Tablica, która przechowuje Sprzedaż całkowita za każdy dzień miesiąca ma jeden wymiar (dzień miesiąca). Tablica, która przechowuje Sprzedaż całkowita przez dział za każdy dzień miesiąca, ma dwa wymiary (numer działu i dzień miesiąca). Nosi nazwę liczbę wymiarów tablicy zawierającej jej *ranga*.  
  
> [!NOTE]
>  Możesz użyć <xref:System.Array.Rank%2A> właściwości w celu określenia, ile wymiary tablicy zawierającej.  
  
## <a name="working-with-dimensions"></a>Praca z wymiarami  
 Określenie elementu tablicy, podając *indeksu* lub *indeks dolny* dla wszystkich jej wymiarów. Elementy są ciągłe wzdłuż każdego wymiaru z indeksu od 0 do najwyższego indeksu dla tego wymiaru.  
  
 Na poniższych ilustracjach przedstawiono koncepcyjny struktury tablic o różnym stopniu. Każdy element na ilustracjach przedstawiono wartości indeksu, mających do niej dostęp. Na przykład, możesz uzyskać dostęp pierwszego elementu w drugim wierszu dwuwymiarowej tablicy, określając indeksów `(1, 0)`.  
  
 ![Diagram przedstawiający Jednowymiarowa tablica.](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![Diagram przedstawia dwuwymiarową tablicę.](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![Diagram przedstawiający tablicę trójwymiarową.](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a>Jeden wymiar  
 Wiele macierzy mają tylko jeden wymiar, takie jak liczba osób w każdym wieku. Jedynym wymaganiem, aby określić element jest okres ważności, dla którego ten element zawiera liczbę. W związku z tym takiej tablicy używa tylko jednego indeksu. Poniższy przykład deklaruje zmienną do przechowywania *jednowymiarową* wieku liczba w wieku od 0 do 120.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>Dwa wymiary  
 Niektórych tablic ma dwa wymiary, takie jak liczba urzędy każdego piętra każdego tworzenia na uczelniach. Specyfikacja elementu wymaga numeru budynku i piętra, a każdy element przechowuje liczbę dla tej kombinacji budynku i piętra. W związku z tym takiej tablicy wykorzystuje dwa indeksy. Poniższy przykład deklaruje zmienną do przechowywania *dwuwymiarową tablicę* liczby office budynkach 0 za pomocą 40 i podłogi od 0 do 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Tablicy dwuwymiarowej jest również nazywany *prostokątny tablicy*.  
  
### <a name="three-dimensions"></a>Trzy wymiary  
 Kilka tablic ma trzy wymiary, takie jak wartości w przestrzeni trójwymiarowej. Takie tablicy używa trzech indeksów, w tym przypadku reprezentujących x, y i z współrzędne przestrzeni fizycznej. Poniższy przykład deklaruje zmienną do przechowywania *tablicy trójwymiarowej* air temperatur w różnych punktach trójwymiarowej woluminu.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Więcej niż trzech wymiarów  
 Mimo że tablica może mieć maksymalnie 32 wymiarów, to rzadkość, aby mieć więcej niż trzy.  
  
> [!NOTE]
>  Po dodaniu wymiary tablicy, całkowita ilość miejsca, które są wymagane przez tablicę zwiększa znacznie, więc tablic wielowymiarowych użycie z rozwagą.  
  
## <a name="using-different-dimensions"></a>Przy użyciu różnych wymiarach  
 Załóżmy, że chcesz śledzić kwot sprzedaży dla każdego dnia miesiąca obecne. Jednowymiarowa tablica elementów 31 może deklarować jeden na każdy dzień miesiąca, w poniższym przykładzie pokazano.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Teraz załóżmy, że chcesz śledzić te same informacje, nie tylko dla każdego dnia, miesiąca, ale także do każdego miesiąca w roku. Może deklarować dwuwymiarową tablicę z 12 wierszy (w przypadku miesięcy) i 31 kolumn (dni), co ilustruje poniższy przykład.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Teraz załóżmy, że możesz zdecydować, że macierz przechowywać informacje o więcej niż jeden rok. Jeśli chcesz śledzić kwot sprzedaży na 5 lat, można zadeklarować tablicy trójwymiarowej z warstwy 5, 12 wierszy i kolumn 31, jak w poniższym przykładzie pokazano.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Należy zauważyć, że ponieważ każdy indeks różni się od 0 do jego maksymalnej każdego wymiaru `salesAmounts` jest zadeklarowany jako jeden mniejsza niż wymagana długość danego wymiaru. Należy zauważyć, że rozmiar tablicy zwiększa się wraz z każdego nowego wymiaru. Trzy rozmiary w powyższych przykładach są odpowiednio 31, 372 i 1,860 elementów.  
  
> [!NOTE]
>  Można utworzyć tablicę, bez używania `Dim` instrukcji lub `New` klauzuli. Na przykład, można wywołać <xref:System.Array.CreateInstance%2A> metody lub innego składnika można przekazać swój kod tablica utworzona w ten sposób. Takie tablica ma dolną granicę niż 0. Można zawsze sprawdzić, dolna granica wymiaru przy użyciu <xref:System.Array.GetLowerBound%2A> metody lub `LBound` funkcji.  
  
## <a name="see-also"></a>Zobacz także

- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
