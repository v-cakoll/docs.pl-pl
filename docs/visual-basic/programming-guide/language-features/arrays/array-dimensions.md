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
ms.openlocfilehash: bbc9e523e9b74cf380c65135e7416f1feba01a2e
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512895"
---
# <a name="array-dimensions-in-visual-basic"></a>Wymiary tablic w Visual Basic

*Wymiar* to kierunek, w którym można zmienić specyfikację elementów tablicy. Tablica, która przechowuje sumę sprzedaży dla każdego dnia miesiąca, ma jeden wymiar (dzień miesiąca). Tablica zawierająca sumę sprzedaży według działu dla każdego dnia miesiąca ma dwa wymiary (numer działu i dzień miesiąca). Liczba wymiarów, które tablica ma określać jej *rangę*.

> [!NOTE]
> Możesz użyć <xref:System.Array.Rank%2A> właściwości, aby określić, ile wymiarów ma tablica.

## <a name="working-with-dimensions"></a>Praca z wymiarami

Należy określić element tablicy przez dostarczenie *indeksu lub indeks* dolny dla  każdego z jego wymiarów. Elementy są ciągłe wzdłuż każdego wymiaru od indeksu 0 do najwyższego indeksu dla tego wymiaru.

Na poniższych ilustracjach przedstawiono strukturę koncepcyjną tablic o różnych rangach. Każdy element na ilustracjach przedstawia wartości indeksu, które uzyskują do niego dostęp. Na przykład można uzyskać dostęp do pierwszego elementu drugiego wiersza tablicy dwuwymiarowej przez określenie indeksów `(1, 0)`.

![Diagram przedstawiający tablicę jednowymiarową.](./media/array-dimensions/one-dimensional-array.gif)

![Diagram przedstawiający dwuwymiarową tablicę.](./media/array-dimensions/two-dimensional-array.gif)

![Diagram przedstawiający trójwymiarową tablicę.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a>Jeden wymiar

Wiele tablic ma tylko jeden wymiar, taki jak liczba osób każdego wieku. Jedynym wymaganiem do określenia elementu jest wiek, dla którego ten element przechowuje liczbę. W związku z tym, taka tablica używa tylko jednego indeksu. Poniższy przykład deklaruje zmienną do przechowywania jednowymiarowej *tablicy* liczby lat od 0 do 120.

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a>Dwa wymiary

Niektóre tablice mają dwa wymiary, takie jak liczba biur w poszczególnych piętrach każdego budynku w kampusie. Specyfikacja elementu wymaga zarówno numeru budynku, jak i podłogi, a każdy element przechowuje liczbę dla tej kombinacji budynku i piętra. W związku z tym, taka tablica używa dwóch indeksów. Poniższy przykład deklaruje zmienną do przechowywania dwuwymiarowej *tablicy* liczników pakietu Office dla budynków od 0 do 40 i podłóg 0 – 5.

```vb
Dim officeCounts(40, 5) As Byte
```

Dwuwymiarowa tablica jest również nazywana *tablicą prostokątną*.

### <a name="three-dimensions"></a>Trzy wymiary

Kilka tablic ma trzy wymiary, takie jak wartości w trójwymiarowej przestrzeni. Taka tablica używa trzech indeksów, co w tym przypadku reprezentuje współrzędne x, y i z miejsca fizycznego. Poniższy przykład deklaruje zmienną do przechowywania trójwymiarowej *tablicy* temperatur w różnych punktach na trójwymiarowym woluminie.

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a>Więcej niż trzy wymiary

Chociaż tablica może mieć maksymalnie 32 wymiarów, bardzo rzadko ma więcej niż trzy.

> [!NOTE]
> Po dodaniu wymiarów do tablicy łączny magazyn wymagany przez tablicę jest znacząco zwiększany, więc używaj tablic wielowymiarowych z opieką.

## <a name="using-different-dimensions"></a>Korzystanie z różnych wymiarów

Załóżmy, że chcesz śledzić kwoty sprzedaży dla każdego dnia bieżącego miesiąca. Można zadeklarować tablicę jednowymiarową z 31 elementami, jedną dla każdego dnia miesiąca, jak pokazano w poniższym przykładzie.

```vb
Dim salesAmounts(30) As Double
```

Teraz Załóżmy, że chcesz śledzić te same informacje nie tylko dla każdego dnia miesiąca, ale również dla każdego miesiąca roku. Można zadeklarować dwuwymiarową tablicę z 12 wierszami (przez miesiące) i 31 kolumn (w dniach), jak pokazano w poniższym przykładzie.

```vb
Dim salesAmounts(11, 30) As Double
```

Teraz Załóżmy, że chcesz, aby tablica zawierała informacje przez więcej niż jeden rok. Jeśli chcesz śledzić kwoty sprzedaży przez 5 lat, możesz zadeklarować trójwymiarową tablicę z 5 warstwami, 12 wierszami i 31 kolumnami, jak pokazano w poniższym przykładzie.

```vb
Dim salesAmounts(4, 11, 30) As Double
```

Należy pamiętać, że ponieważ każdy indeks różni się od 0 do maksimum, każdy wymiar `salesAmounts` jest zadeklarowany jako mniejszy niż wymagana długość dla tego wymiaru. Zwróć uwagę na to, że rozmiar tablicy rośnie wraz z każdym nowym wymiarem. Trzy powyższe wielkości w powyższych przykładach mają odpowiednio 31, 372 i 1 860 elementów.

> [!NOTE]
> Można utworzyć tablicę bez użycia `Dim` instrukcji `New` lub klauzuli. Na przykład można wywołać <xref:System.Array.CreateInstance%2A> metodę lub inny składnik może przekazać kod w ten sposób tablicę utworzoną w ten sposób. Taka tablica może mieć dolną granicę inną niż 0. Zawsze możesz testować dolną granicę wymiaru przy użyciu <xref:System.Array.GetLowerBound%2A> metody `LBound` lub funkcji.

## <a name="see-also"></a>Zobacz także

- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
