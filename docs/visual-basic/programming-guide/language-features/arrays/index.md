---
title: Tablice
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 5093f28f05c5b72294dce9a4e69723acafb31a9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413094"
---
# <a name="arrays-in-visual-basic"></a>Tablice w Visual Basic

Tablica jest zestawem wartości, które są oznaczanymi *elementami*, które są logicznie powiązane ze sobą. Na przykład tablica może zawierać liczbę studentów w każdej klasie w szkole gramatyki; Każdy element tablicy to liczba studentów w jednej klasie. Podobnie tablica może składać się z kategorii uczniów dla klasy; Każdy element tablicy jest pojedynczą klasy.

Możliwe jest, że poszczególne zmienne przechowują poszczególne elementy danych. Na przykład jeśli nasza aplikacja analizuje klasy uczniów, możemy użyć osobnej zmiennej dla każdej studenta, np `englishGrade1` `englishGrade2` ., itp. Takie podejście ma trzy zasadnicze ograniczenia:

- Musimy znać czas projektowania dokładnie na liczbę potrzebnych do obsłużenia.
- Obsługa dużej liczby ocen szybko zmieni się na nieporęczny. Dzięki temu aplikacja ma znacznie większą liczbę błędów.
- Jest trudno zachować. Każda nowa dodawana Klasa wymaga, aby aplikacja została zmodyfikowana, ponownie skompilowana i wdrożona ponownie.

Korzystając z tablicy, można odwoływać się do tych powiązanych wartości o tej samej nazwie i użyć numeru, który jest nazywany *indeksem* lub *dolnym podindeksem* , aby zidentyfikować pojedynczy element na podstawie jego położenia w tablicy. Indeksy zakresu tablicy od 0 do jeden są mniejsze od całkowitej liczby elementów w tablicy. W przypadku użycia składni Visual Basic w celu zdefiniowania rozmiaru tablicy należy określić jej najwyższy indeks, a nie całkowitą liczbę elementów w tablicy. Możesz współpracować z tablicą jako jednostką, a możliwość iteracji jej elementów uwalnia użytkownika od potrzeb, aby wiedzieć dokładnie, ile elementów zawiera w czasie projektowania.

Kilka szybkich przykładów przed wyjaśnieniem:

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

' Declare a single-dimension array and set its 4 values.
Dim numbers = New Integer() {1, 2, 4, 8}

' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)

' Redefine the size of an existing array and reset the values.
ReDim numbers(15)

' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double

' Declare a 4 x 3 multidimensional array and set array element values.
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}

' Declare a jagged array
Dim sales()() As Double = New Double(11)() {}
```

## <a name="array-elements-in-a-simple-array"></a>Elementy tablicy w prostej tablicy

Utwórzmy tablicę o nazwie `students` , aby przechowywać liczbę studentów w każdej klasie w szkole gramatyki. Indeksy elementów mieszczą się w zakresie od 0 do 6. Użycie tej tablicy jest prostsze niż deklarowanie siedmiu zmiennych.

Na poniższej ilustracji przedstawiono `students` tablicę. Dla każdego elementu tablicy:

- Indeks elementu reprezentuje ocenę (indeks 0 reprezentuje przedszkole).

- Wartość zawarta w elemencie reprezentuje liczbę uczniów w tej klasie.

![Diagram przedstawiający tablicę liczb uczniów](./media/index/students-array-elements.gif)

Poniższy przykład zawiera kod Visual Basic, który tworzy i używa tablicy:

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

Przykład wykonuje trzy czynności:

- Deklaruje `students` tablicę z siedmiu elementami. Liczba `6` w deklaracji tablicy wskazuje ostatni indeks w tablicy; jest ona mniejsza niż liczba elementów w tablicy.
- Przypisuje wartości do każdego elementu w tablicy. Do elementów tablicy uzyskuje się dostęp przy użyciu nazwy tablicy i w tym indeks poszczególnych elementów w nawiasach.
- Wyświetla listę każdej wartości tablicy. W przykładzie używa się [`For`](../../../language-reference/statements/for-next-statement.md) instrukcji w celu uzyskania dostępu do każdego elementu tablicy według numeru indeksu.

`students`Tablica w poprzednim przykładzie jest tablicą jednowymiarową, ponieważ używa jednego indeksu. Tablica, która używa więcej niż jednego indeksu lub indeks dolny, jest nazywana *wielowymiarowych*. Aby uzyskać więcej informacji, zobacz pozostała część tego artykułu i [Wymiary tablicy w Visual Basic](array-dimensions.md).

## <a name="creating-an-array"></a>Tworzenie tablicy

Rozmiar tablicy można zdefiniować na kilka sposobów:

- Możesz określić rozmiar, gdy tablica jest zadeklarowana:

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- Można użyć klauzuli, `New` Aby podać rozmiar tablicy podczas jej tworzenia:

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

Jeśli masz istniejącą tablicę, możesz zmienić jej rozmiar przy użyciu [`ReDim`](../../../language-reference/statements/redim-statement.md) instrukcji. Można określić, że `ReDim` instrukcja ma przechowywać wartości, które znajdują się w tablicy, lub można określić, że ma ona tworzyć pustą tablicę. W poniższym przykładzie pokazano różne zastosowania `ReDim` instrukcji w celu zmodyfikowania rozmiaru istniejącej tablicy.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

Aby uzyskać więcej informacji, zobacz [Instrukcja ReDim](../../../language-reference/statements/redim-statement.md).

## <a name="storing-values-in-an-array"></a>Przechowywanie wartości w tablicy

Możesz uzyskać dostęp do każdej lokalizacji w tablicy przy użyciu indeksu typu `Integer` . Możesz przechowywać i pobierać wartości w tablicy, odwołując się do każdej lokalizacji tablicy przy użyciu indeksu ujętego w nawiasy. Indeksy dla tablic wielowymiarowych są oddzielone przecinkami (,). Wymagany jest jeden indeks dla każdego wymiaru tablicy.

Poniższy przykład ukazuje niektóre instrukcje, które przechowują i pobierają wartości w tablicach.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Wypełnianie tablicy przy użyciu literałów tablicowych

Za pomocą literału tablicowego można wypełnić tablicę początkowym zestawem wartości w tym samym czasie, w którym została utworzona. Literał tablicowy składa się z listy wartości rozdzielonych przecinkami, które są ujęte w nawiasy klamrowe ( `{}` ).

Podczas tworzenia tablicy przy użyciu literału tablicowego można dostarczyć typ tablicy lub użyć wnioskowania o typie, aby określić typ tablicy. W poniższym przykładzie przedstawiono obie opcje.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

Gdy używasz wnioskowania o typie, typ tablicy jest określany przez *Typ dominujący* na liście wartości literału. Typ dominujący jest typem, do którego można rozszerzyć wszystkie inne typy w tablicy. Jeśli nie można określić tego unikatowego typu, typ dominujący jest unikatowym typem, do którego można zawęzić wszystkie inne typy w tablicy. Jeśli nie można określić żadnego z tych unikatowych typów, typ dominujący to `Object` . Na przykład, jeśli lista wartości, które są dostarczone do literału tablicowego zawiera wartości typu `Integer` , `Long` , i `Double` , Tablica wyników jest typu `Double` . Ponieważ `Integer` i `Long` rozszerza tylko do `Double` , `Double` jest typem dominującym. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> Wnioskowanie o typie można użyć tylko dla tablic, które są zdefiniowane jako zmienne lokalne w składowej typu. Jeśli nie istnieje jawna definicja typu, tablice zdefiniowane za pomocą literałów tablicowych na poziomie klasy są typu `Object[]` . Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../variables/local-type-inference.md).

Należy zauważyć, że poprzedni przykład definiuje `values` jako tablicę typu, `Double` mimo że wszystkie literały tablicowe są typu `Integer` . Można utworzyć tę tablicę, ponieważ wartości w literale Array można rozszerzyć na `Double` wartości.

Możesz również utworzyć i wypełnić tablicę wielowymiarową przy użyciu *zagnieżdżonych literałów tablicowych*. Zagnieżdżone literały tablicowe muszą mieć różne wymiary zgodne z tablicą wyników. Poniższy przykład tworzy dwuwymiarową tablicę liczb całkowitych przy użyciu zagnieżdżonych literałów tablicowych.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

W przypadku używania zagnieżdżonych literałów tablicowych do tworzenia i wypełniania tablicy, występuje błąd, jeśli liczba elementów w zagnieżdżonych literałach tablicowych nie jest zgodna. Błąd występuje również wtedy, gdy jawnie deklaruje zmienną tablicową tak, aby miała różną liczbę wymiarów niż literały tablicowe.

Podobnie jak w przypadku tablic jednowymiarowych można polegać na wnioskach o typie podczas tworzenia wielowymiarowej tablicy z zagnieżdżonymi literałami tablicowymi. Typ wnioskowany jest typem dominującym dla wszystkich wartości we wszystkich literałach tablicowych dla wszystkich poziomów zagnieżdżenia. Poniższy przykład tworzy dwuwymiarową tablicę typu `Double[,]` z wartości, które są typu `Integer` i `Double` .

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Aby uzyskać więcej przykładów, zobacz [How to: Initialize a Array Variable in Visual Basic](how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Iteracja przez tablicę

Podczas iteracji przez tablicę uzyskuje się dostęp do każdego elementu w tablicy od najniższego indeksu do najwyższej lub od najwyższego do najniższego. Zazwyczaj należy użyć [dla... Next](../../../language-reference/statements/for-next-statement.md) lub [for each... Następna instrukcja](../../../language-reference/statements/for-each-next-statement.md) do iteracji przez elementy tablicy. Gdy nie znasz górnych granic tablicy, możesz wywołać <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> metodę, aby uzyskać najwyższą wartość indeksu. Chociaż najniższa wartość indeksu jest niemal zawsze równa 0, można wywołać <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> metodę, aby uzyskać najniższą wartość indeksu.

Poniższy przykład wykonuje iterację przez tablicę jednowymiarową za pomocą [`For...Next`](../../../language-reference/statements/for-next-statement.md) instrukcji.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

Poniższy przykład wykonuje iterację przez tablicę wielowymiarową za pomocą [`For...Next`](../../../language-reference/statements/for-next-statement.md) instrukcji. <xref:System.Array.GetUpperBound%2A>Metoda ma parametr, który określa wymiar. `GetUpperBound(0)`zwraca najwyższy indeks pierwszego wymiaru i `GetUpperBound(1)` zwraca najwyższy indeks drugiego wymiaru.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

W poniższym przykładzie zastosowano [for each... Następna instrukcja](../../../language-reference/statements/for-each-next-statement.md)do iteracji przez tablicę jednowymiarową i dwuwymiarową tablicę.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Rozmiar tablicy

Rozmiar tablicy jest iloczynem długości wszystkich wymiarów. Reprezentuje łączną liczbę elementów aktualnie znajdujących się w tablicy.  Na przykład poniższy przykład deklaruje tablicę 2-wymiarową z czterema elementami w każdym wymiarze. Jak widać dane wyjściowe z przykładu, rozmiar tablicy wynosi 16 (lub (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> Ta dyskusja rozmiaru tablicy nie ma zastosowania do tablic nieregularnych. Aby uzyskać informacje na temat tablic nieregularnych i określania rozmiaru tablicy nieregularnej, zobacz sekcję [tablice nieregularne](#jagged-arrays) .

Rozmiar tablicy można znaleźć za pomocą <xref:System.Array.Length%2A?displayProperty=nameWithType> właściwości. Długość każdego wymiaru tablicy wielowymiarowej można znaleźć za pomocą <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.

Można zmienić rozmiar zmiennej tablicowej, przypisując do niej nowy obiekt array lub używając instrukcji [ `ReDim` instrukcji](../../../language-reference/statements/redim-statement.md) . Poniższy przykład używa instrukcji, `ReDim` Aby zmienić tablicę elementów 100 do 51-elementowej tablicy.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Należy pamiętać o kilku kwestiach związanych z rozmiarem tablicy.

|||
|---|---|
|Długość wymiaru|Indeks każdego wymiaru jest oparty na 0, co oznacza, że zakres od 0 do jego górnej granicy. W związku z tym długość danego wymiaru jest większa niż zadeklarowana Górna granica tego wymiaru.|
|Limity długości|Długość każdego wymiaru tablicy jest ograniczona do maksymalnej wartości `Integer` typu danych, czyli <xref:System.Int32.MaxValue?displayProperty=nameWithType> lub (2 ^ 31)-1. Jednak łączny rozmiar tablicy jest również ograniczony przez pamięć dostępną w systemie. Jeśli spróbujesz zainicjować tablicę, która przekracza ilość dostępnej pamięci, środowisko uruchomieniowe wygeneruje <xref:System.OutOfMemoryException> .|
|Rozmiar i rozmiar elementu|Rozmiar tablicy jest niezależny od typu danych jego elementów. Rozmiar zawsze reprezentuje całkowitą liczbę elementów, a nie liczbę bajtów, które zużywają w pamięci.|
|Zużycie pamięci|Nie można bezpiecznie wprowadzać żadnych założeń dotyczących sposobu przechowywania tablicy w pamięci. Magazyn różni się w zależności od platformy różnych szerokości danych, dlatego ta sama tablica może zużywać więcej pamięci w systemie 64-bitowym niż w systemie 32-bitowym. W zależności od konfiguracji systemu po zainicjowaniu tablicy środowisko uruchomieniowe języka wspólnego (CLR) może przypisywać magazyn do spakowania elementów jako blisko siebie, jak to możliwe, lub aby wyrównać je wszystkie do naturalnych granic sprzętu. Ponadto tablica wymaga nakładu pracy związanego z magazynowaniem danych sterujących, a narzuty zwiększają się przy każdym dodanym wymiarze.|

## <a name="the-array-type"></a>Typ tablicy

Każda tablica ma typ danych, który różni się od typu danych jego elementów. Brak pojedynczego typu danych dla wszystkich tablic. Zamiast tego typ danych tablicy jest określany przez liczbę wymiarów lub *rangę*tablicy oraz typ danych elementów w tablicy. Dwie zmienne tablic są tego samego typu danych tylko wtedy, gdy mają tę samą rangę, a ich elementy mają ten sam typ danych. Długość wymiarów tablicy nie ma wpływu na typ danych tablicy.

Każda tablica dziedziczy z <xref:System.Array?displayProperty=nameWithType> klasy i można zadeklarować zmienną jako typu `Array` , ale nie można utworzyć tablicy typu `Array` . Na przykład, chociaż Poniższy kod deklaruje `arr` zmienną jako typ `Array` i wywołuje <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metodę w celu utworzenia wystąpienia tablicy, typ tablicy udowadnia się obiektem [].

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

Ponadto [Instrukcja ReDim](../../../language-reference/statements/redim-statement.md) nie może działać na zmiennej zadeklarowanej jako typ `Array` . Z tych powodów i dla bezpieczeństwa typów zaleca się zadeklarowanie każdej tablicy jako określonego typu.

Możesz sprawdzić typ danych tablicy lub jej elementów na kilka sposobów.

- Można wywołać <xref:System.Object.GetType%2A> metodę na zmiennej, aby uzyskać <xref:System.Type> obiekt, który reprezentuje typ czasu wykonywania zmiennej. <xref:System.Type>Obiekt zawiera rozbudowane informacje we właściwościach i metodach.
- Możesz przekazać zmienną do <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkcji, aby uzyskać `String` nazwę typu czasu wykonywania.

Poniższy przykład wywołuje `GetType` metodę i `TypeName` funkcję, aby określić typ tablicy. Typ tablicy to `Byte(,)` . Należy zauważyć, że <xref:System.Type.BaseType%2A?displayProperty=nameWithType> Właściwość wskazuje również, że typ podstawowy tablicy bajtowej jest <xref:System.Array> klasą.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Tablice jako wartości zwracane i parametry

Aby zwrócić tablicę z `Function` procedury, określ typ danych Array i liczbę wymiarów jako zwracany typ [instrukcji Function](../../../language-reference/statements/function-statement.md). W ramach funkcji deklaruj lokalną zmienną tablicową o tym samym typie danych i liczbie wymiarów. W [instrukcji return](../../../language-reference/statements/return-statement.md)Uwzględnij lokalną zmienną tablicową bez nawiasów.

Aby określić tablicę jako parametr do `Sub` `Function` procedury lub, zdefiniuj parametr jako tablicę o określonym typie danych i liczbie wymiarów. W wywołaniu procedury należy przekazać zmienną tablicową o tym samym typie danych i liczbie wymiarów.

W poniższym przykładzie `GetNumbers` Funkcja zwraca `Integer()` tablicę jednowymiarową typu `Integer` . `ShowNumbers`Procedura akceptuje `Integer()` argument.

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

W poniższym przykładzie `GetNumbersMultiDim` Funkcja zwraca `Integer(,)` tablicę dwuwymiarową typu `Integer` .  `ShowNumbersMultiDim`Procedura akceptuje `Integer(,)` argument.

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Tablice nieregularne

Czasami struktura danych w aplikacji jest dwuwymiarowa, ale nie prostokątna. Na przykład można użyć tablicy do przechowywania danych o wysokiej temperatury każdego dnia miesiąca. Pierwszy wymiar tablicy reprezentuje miesiąc, ale drugi wymiar reprezentuje liczbę dni, a liczba dni w miesiącu nie jest jednolita. *Tablica nieregularna*, nazywana również *tablicą*tablic, została zaprojektowana dla takich scenariuszy. Tablica nieregularna jest tablicą, której elementy są również tablicami. Tablica nieregularna i każdy element w tablicy nieregularnej może mieć co najmniej jeden wymiar.

W poniższym przykładzie zastosowano tablicę miesięcy, każdy element jest tablicą dni. W przykładzie zastosowano tablicę nieregularną, ponieważ różne miesiące mają różną liczbę dni.  W przykładzie pokazano, jak utworzyć tablicę nieregularną, przypisać do niej wartości, a następnie pobrać i wyświetlić jej wartości.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

W poprzednim przykładzie wartości są przypisywane do tablicy nieregularnej przy użyciu `For...Next` pętli. Można również przypisać wartości do elementów tablicy nieregularnej przy użyciu zagnieżdżonych literałów tablicowych. Jednak próba użycia zagnieżdżonych literałów tablicowych (na przykład) powoduje `Dim valuesjagged = {{1, 2}, {2, 3, 4}}` wygenerowanie błędu kompilatora [BC30568](../../../misc/bc30568.md). Aby poprawić błąd, ujmij wewnętrzne literały tablicowe w nawiasy. Nawiasy wymuszają obliczenie wyrażenia literału tablicy, a wyniki są używane z zewnętrznym literałem tablicy, jak pokazano w poniższym przykładzie.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

Tablica nieregularna jest tablicą jednowymiarową, której elementy zawierają tablice. W związku z tym <xref:System.Array.Length%2A?displayProperty=nameWithType> Właściwość i `Array.GetLength(0)` Metoda zwracają liczbę elementów w tablicy jednowymiarowej i `Array.GetLength(1)` zgłasza, <xref:System.IndexOutOfRangeException> że nieregularna tablica nie jest wielowymiarowa. Należy określić liczbę elementów w każdej podtablicy, pobierając wartość każdej właściwości podtablicy <xref:System.Array.Length%2A?displayProperty=nameWithType> . Poniższy przykład ilustruje, jak określić liczbę elementów w tablicy nieregularnej.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Tablice o zerowej długości

Visual Basic odróżnia między niezainicjowaną tablicą (tablicę, której wartością `Nothing` ) i *tablicą o zerowej długości* lub tablicę pustą (tablicę, która nie ma elementów). Niezainicjowana tablica jest taka, która nie została zwymiarowana ani nie ma przypisanych żadnych wartości. Przykład:

```vb
Dim arr() As String
```

Tablica o zerowej długości jest zadeklarowana z wymiarem-1. Przykład:

```vb
Dim arrZ(-1) As String
```

Może być konieczne utworzenie tablicy o zerowej długości w następujących okolicznościach:

- Bez ryzyka <xref:System.NullReferenceException> wyjątku, kod musi uzyskać dostęp do elementów członkowskich <xref:System.Array> klasy, takich jak <xref:System.Array.Length%2A> lub <xref:System.Array.Rank%2A> , lub wywołać funkcję Visual Basic taką jak <xref:Microsoft.VisualBasic.Information.UBound%2A> .

- Chcesz zachować prosty kod, nie trzeba sprawdzać się `Nothing` jako przypadek specjalny.

- Twój kod współdziała z interfejsem programowania aplikacji (API), który wymaga przekazania tablicy o zerowej długości do jednej lub kilku procedur lub zwraca tablicę o zerowej długości z jednej lub kilku procedur.

## <a name="splitting-an-array"></a>Dzielenie tablicy

W niektórych przypadkach może być konieczne wyodrębnienie pojedynczej tablicy do wielu tablic. Obejmuje to zidentyfikowanie punktu lub punktów, w których tablica ma zostać podzielona, a następnie Spitting tablicę do dwóch lub więcej oddzielnych tablic.

> [!NOTE]
> W tej sekcji nie jest omawiany podział pojedynczego ciągu na tablicę ciągów na podstawie pewnego ogranicznika. Aby uzyskać informacje na temat dzielenia ciągu, zobacz <xref:System.String.Split%2A?displayProperty=nameWithType> metodę.

Najczęstszymi kryteriami dzielenia tablicy są:

- Liczba elementów w tablicy. Na przykład możesz chcieć podzielić tablicę o więcej niż określoną liczbę elementów na liczbę w przybliżeniu równej części. W tym celu można użyć wartości zwracanej przez <xref:System.Array.Length%2A?displayProperty=nameWithType> <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metodę lub.

- Wartość elementu, który służy jako ogranicznik, który wskazuje, gdzie należy podzielić tablicę. Konkretną wartość można wyszukać, wywołując <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> metody i <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> .

Po ustaleniu indeksu lub indeksów, w których Tablica powinna być podzielona, można utworzyć poszczególne tablice, wywołując <xref:System.Array.Copy%2A?displayProperty=nameWithType> metodę.

Poniższy przykład dzieli tablicę na dwie tablice o rozmiarze zbliżonym do równe. (Jeśli łączna liczba elementów tablicy jest nieparzysta, pierwsza tablica ma jeden element niż drugi).

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

Poniższy przykład dzieli tablicę ciągów na dwie tablice na podstawie obecności elementu, którego wartością jest "ZZZ", który służy jako ogranicznik tablicy. Nowe tablice nie zawierają elementu zawierającego ogranicznik.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Sprzęganie tablic

Istnieje również możliwość łączenia wielu tablic w jedną większą tablicę. W tym celu należy również użyć <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody.

> [!NOTE]
> Ta sekcja nie omawia sprzężenia tablicy ciągów w jeden ciąg. Aby uzyskać informacje na temat dołączania tablicy ciągów, zobacz <xref:System.String.Join%2A?displayProperty=nameWithType> metodę.

Przed skopiowaniem elementów każdej tablicy do nowej tablicy, najpierw należy się upewnić, że zainicjowano tablicę, tak aby była wystarczająco duża, aby pomieścić nową tablicę. Można to zrobić na jeden z dwóch sposobów:

- Użyj [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) instrukcji, aby dynamicznie rozwijać tablicę przed dodaniem do niej nowych elementów. Jest to najprostsza technika, ale może to spowodować spadek wydajności i nadmierne użycie pamięci podczas kopiowania dużych tablic.
- Oblicz łączną liczbę elementów wymaganą przez nową dużą tablicę, a następnie Dodaj do niej elementy każdej tablicy źródłowej.

Poniższy przykład używa drugiego podejścia do dodawania czterech tablic zawierających dziesięć elementów każdego do jednej tablicy.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Ponieważ w tym przypadku tablice źródłowe są bardzo małe, możemy również dynamicznie rozwijać tablicę, dodając do niej elementy każdej nowej tablicy. W poniższym przykładzie jest to.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Kolekcje jako alternatywę dla tablic

Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą obiektów silnie wpisanych. Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W przeciwieństwie do tablic, które wymagają jawnie zmiany rozmiaru tablicy z [ `ReDim` instrukcją](../../../language-reference/statements/redim-statement.md), kolekcje są zwiększane i zmniejszane dynamicznie w miarę potrzeby zmiany aplikacji.

W przypadku użycia `ReDim` do przewymiarowania tablicy Visual Basic tworzy nową tablicę i zwalnia poprzednią. Trwa to czas wykonywania. W związku z tym, jeśli liczba elementów, które często pracujesz ze zmianami lub nie można przewidzieć maksymalnej wymaganej liczby elementów, zwykle uzyskuje się lepszą wydajność przy użyciu kolekcji.

W przypadku niektórych kolekcji można przypisać klucz do dowolnego obiektu, który został umieszczony w kolekcji, dzięki czemu można szybko pobrać obiekt przy użyciu klucza.

Jeśli kolekcja zawiera elementy tylko jednego typu danych, można użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólna kolekcja wymusza bezpieczeństwo typu, tak aby nie można było dodać do niego żadnego innego typu danych.

Aby uzyskać więcej informacji na temat kolekcji, zobacz [kolekcje](../../concepts/collections.md).

## <a name="related-topics"></a>Powiązane tematy

|Termin|Definicja|
|----------|----------------|
|[Wymiary tablic w Visual Basic](array-dimensions.md)|Objaśnia rangę i wymiary w tablicach.|
|[Porady: inicjowanie zmiennej tablicy w języku Visual Basic](how-to-initialize-an-array-variable.md)|Opisuje sposób wypełniania tablic wartościami początkowymi.|
|[Porady: sortowanie tablicy w Visual Basic](how-to-sort-an-array.md)|Pokazuje, jak sortować elementy tablicy alfabetycznie.|
|[Instrukcje: przypisywanie tablicy do innej tablicy](how-to-assign-one-array-to-another-array.md)|Opisuje reguły i kroki umożliwiające przypisanie tablicy do innej zmiennej tablicowej.|
|[Rozwiązywanie problemów związanych z tablicami](troubleshooting-arrays.md)|W tym artykule omówiono niektóre typowe problemy, które powstają podczas pracy z tablicami.|

## <a name="see-also"></a>Zobacz też

- <xref:System.Array?displayProperty=nameWithType>
- [Dim, instrukcja](../../../language-reference/statements/dim-statement.md)
- [ReDim, instrukcja](../../../language-reference/statements/redim-statement.md)
