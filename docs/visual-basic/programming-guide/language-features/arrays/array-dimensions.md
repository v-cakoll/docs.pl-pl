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
ms.openlocfilehash: cf295288dd034d744dceb71b5c58278be5cc2a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="array-dimensions-in-visual-basic"></a>Wymiary tablic w Visual Basic
A *wymiaru* jest kierunek, w którym można wybrać różne specyfikacje elementów tablicy. Tablica, która przechowuje sprzedaży całkowitą dla każdego dnia, miesiąca ma jeden wymiar (dzień miesiąca). Tablica, która przechowuje sprzedaży całkowita przez dział dla każdego dnia, miesiąca ma dwóch wymiarów (numer działu i dzień miesiąca). Nazywa się liczby wymiarów tablicy nie ma jej *rangę*.  
  
> [!NOTE]
>  Można użyć <xref:System.Array.Rank%2A> właściwości w celu określenia liczby wymiarów tablicy nie ma.  
  
## <a name="working-with-dimensions"></a>Praca z wymiarami  
 Określ element tablicy podając *indeksu* lub *indeks dolny* dla każdego z jego wymiarów. Elementy są ciągłe wzdłuż każdego wymiaru z indeksem 0 za pomocą najwyższy indeksu dla tego wymiaru.  
  
 Na poniższych ilustracjach przedstawiono koncepcyjnej struktury tablic o różnym stopniu. Każdy element na ilustracjach przedstawiono wartości indeksów, które do niego dostęp. Na przykład można dostępu pierwszym elementem w drugim wierszu tablicą dwuwymiarową określając indeksów `(1, 0)`.  
  
 ![Graficzny diagram jednego&#45;tablicą wielowymiarową](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")  
Jednowymiarowa tablica  
  
 ![Graficzny diagram dwóch&#45;tablicą wielowymiarową](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
tablicą dwuwymiarową  
  
 ![Graficzny diagram trzech&#45;tablicą wielowymiarową](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
tablicą trójwymiarową  
  
### <a name="one-dimension"></a>Jeden wymiar  
 Wiele tablic mieć tylko jeden wymiar, takie jak liczba osób każdego wieku. Jedynym wymaganiem, aby określić elementu jest okres ważności, dla którego ten element zawiera wartość licznika. W związku z tym takie tablicy używa tylko jeden indeks. Poniższy przykład deklaruje zmienną do przechowywania *jednowymiarową* wieku liczba wieku od 0 do 120.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>Dwóch wymiarów  
 Niektóre tablice zawierają dwóch wymiarów, takich jak liczba oddziałów na każde piętro każdego tworzenia w firmy. Specyfikacja elementu wymaga zarówno numeru budynku i piętra, a każdy element zawiera liczbę elementów w tym kombinację budynku i piętra. W związku z tym takie tablicy używa dwóch indeksów. Poniższy przykład deklaruje zmienną do przechowywania *tablicą dwuwymiarową* liczników pakietu office, budynki 0 za pomocą 40 i piętra od 0 do 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Skrót jest tablicą dwuwymiarową *tablicy regularnej*.  
  
### <a name="three-dimensions"></a>Trzy wymiary  
 Tablice kilka ma trzy wymiarów, takich jak wartości w przestrzeni trójwymiarowej. Takie tablicy używa trzech indeksów, które reprezentują w takim przypadku x, y oraz współrzędne z fizycznego miejsca. Poniższy przykład deklaruje zmienną do przechowywania *tablicą trójwymiarową* lotniczego temperatur w różnych miejscach trójwymiarowy woluminu.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Więcej niż trzech wymiarów  
 Mimo że tablica może mieć maksymalnie 32 wymiarów, jest rzadko ma więcej niż trzy.  
  
> [!NOTE]
>  Dodaj wymiary do tablicy, całkowita ilość miejsca, które są wymagane przez tablicę zwiększa znacznie, tak tablice wielowymiarowe Użyj ostrożność.  
  
## <a name="using-different-dimensions"></a>Przy użyciu różnych wymiarach  
 Załóżmy, że chcesz śledzić kwoty sprzedaży dla każdego dnia, miesiąca występuje. Jednowymiarowa tablica elementów 31, mogą zadeklarować po jednej dla każdego dnia, miesiąca, jak w poniższym przykładzie przedstawiono.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Teraz załóżmy, że chcesz śledzić te same informacje, nie tylko dla każdego dnia, miesiąca, ale też co miesiąc w roku. Może zadeklarować jest tablicą dwuwymiarową z 12 wierszy (dla miesięcy) i 31 kolumn (dni), jak przedstawiono na poniższym przykładzie.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Teraz załóżmy, że użytkownik chce mieć macierzy przechowywania informacji przez więcej niż jeden rok. Jeśli chcesz śledzić kwoty sprzedaży 5 lat, można zadeklarować jest tablicą trójwymiarową z warstwy 5, 12 wierszy i kolumn 31, jak przedstawiono na poniższym przykładzie.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Należy zauważyć, że każdy indeks różne od 0 do jego maksymalnej każdego wymiaru `salesAmounts` jest zadeklarowany jako jeden mniejszy niż wymagana długość dla tego wymiaru. Należy pamiętać, że rozmiar tablicy zwiększa się wraz z każdego nowego wymiaru. Trzy rozmiary w powyższych przykładach są odpowiednio 31, 372 i 1,860 elementów.  
  
> [!NOTE]
>  Można utworzyć tablicy bez używania `Dim` instrukcji lub `New` klauzuli. Na przykład można wywołać <xref:System.Array.CreateInstance%2A> metody lub innego składnika można przekazać swój kod tablicy utworzonej w ten sposób. Takie tablicy mogą mieć dolną granicą inną niż 0. Należy zawsze przetestować dla dolna granica wymiaru przy użyciu <xref:System.Array.GetLowerBound%2A> metody lub `LBound` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
