---
title: Tablice w Visual Basic
ms.date: 12/06/2017
f1_keywords:
  - vb.Array
helpviewer_keywords:
  - 'arrays [Visual Basic]'
  - 'Visual Basic, arrays'
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
---

# <a name="arrays-in-visual-basic"></a>Tablice w Visual Basic

Tablica to zbiór wartości, które są określane jako *elementy*, które są logicznie powiązane ze sobą. Na przykład tablicy może składać się z liczby studentów każdej grupy zaszeregowania w liceum; Każdy element tablicy jest liczba uczniów w jednej klasy korporacyjnej. Podobnie Tablica może składać się z ocen studenta dla klasy; Każdy element tablicy jest jednej klasy korporacyjnej.

Jest możliwe poszczególnych zmiennych do przechowywania wszystkich naszych elementów danych. Na przykład, jeśli nasza aplikacja analizuje ocen studentów, możemy użyć osobnej zmiennej dla każdego ucznia klasy korporacyjnej, takich jak `englishGrade1`, `englishGrade2`itp. Takie podejście ma trzy główne ograniczenia:

- Musimy znać w czasie projektowania, dokładnie ile ocen mamy do obsługi.
- Obsługę dużej liczby klas szybko staje się niewydolna. To z kolei sprawia, że aplikacja będzie mieć poważne błędy.
- Jest trudne w utrzymaniu. Każdego nowe klasy korporacyjnej, które możemy dodać wymaga aplikacji można modyfikować, ponownie skompilowana i ponownego wdrażania.

Za pomocą tablicowego, możesz odwoływać się do tych powiązanych wartości o tej samej nazwie i użyć numeru, który jest nazywany *indeksu* lub *indeks dolny* do identyfikacji pojedynczego elementu na podstawie jego położenia w tablicy. Indeksy tablicy z zakresu od 0 do jednego mniejsza niż całkowita liczba elementów w tablicy. Gdy używasz składni języka Visual Basic można zdefiniować rozmiar tablicy, należy określić jego najwyższy indeks nie całkowitą liczbę elementów w tablicy. Możesz pracować z tablicy jako jednostki, a możliwość iterować jej elementy zwalnia musi wiedzieć dokładnie tak jak wiele elementów zawiera się on w czasie projektowania.

Przykłady szybkich przed wyjaśnienie:

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

'Declare a single-dimension array and set its 4 values.
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

Utwórz tablicę o nazwie `students` do przechowywania liczby studentów każdej grupy zaszeregowania w liceum. Indeksy zakres elementów z zakresu od 0 do 6. Za pomocą tej tablicy jest prostsze niż zadeklarowanie siedmiu zmiennych.

Poniższa ilustracja przedstawia `students` tablicy. Dla każdego elementu tablicy:

- Indeks elementu reprezentuje grupę zaszeregowania (indeks 0 reprezentuje przedszkole).

- Wartość, która jest zawarta w elemencie reprezentuje liczbę studentów w tej klasie.

![Obraz przedstawiający liczby studentów tablicy](../../language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool") elementów tablicy "studenci"

Poniższy przykład zawiera kod języka Visual Basic, który tworzy i używa tablicy:

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

Przykład wykonuje trzy rzeczy:

- Deklaruje `students` tablicy przy użyciu siedem elementów. Liczba `6` w tablicy deklaracja wskazuje, której ostatni indeks w tablicy; jest to jeden mniejsza niż liczba elementów w tablicy.
- Przypisuje wartości do każdego elementu w tablicy. Elementy tablicy są dostępne przy użyciu nazwy tablicy i tym indeks pojedynczego elementu w nawiasach.
- Wyświetla listę każdej wartości w tablicy. W przykładzie użyto [ `For` ](../../../language-reference/statements/for-next-statement.md) instrukcji, które umożliwiają dostęp do każdego elementu tablicy za pomocą numeru indeksu.

`students` Tablica w poprzednim przykładzie to Jednowymiarowa tablica, ponieważ używa jednego indeksu. Nosi nazwę tablicy, która używa więcej niż jednego indeksu lub indeksu dolnego *wielowymiarowe*. Aby uzyskać więcej informacji, zobacz pozostałej części tego artykułu i [wymiary tablicy w języku Visual Basic](../../language-features/arrays/array-dimensions.md).

## <a name="creating-an-array"></a>Tworzenie tablicy

Można zdefiniować rozmiar tablicy na kilka sposobów:

- Można określić rozmiar, gdy tablica jest zadeklarowana:

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- Możesz użyć `New` klauzuli, aby dostarczyć rozmiaru tablicy podczas jej tworzenia:

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

W przypadku istniejącej tablicy można ponownie zdefiniować jej rozmiar za pomocą [ `ReDim` ](../../../language-reference/statements/redim-statement.md) instrukcji. Można określić, że `ReDim` instrukcji przechowywać wartości, które znajdują się w tablicy, lub można określić, że utworzona pusta tablica. W poniższym przykładzie pokazano różne sposoby zastosowania `ReDim` instrukcję, aby zmienić rozmiar istniejącej tablicy.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

Aby uzyskać więcej informacji, zobacz [instrukcji ReDim](../../../language-reference/statements/redim-statement.md).

## <a name="storing-values-in-an-array"></a>Przechowywanie wartości w tablicy

Dostęp do każdej lokalizacji tablicy przy użyciu indeksu typu `Integer`. Można przechowywać i pobierać wartości w tablicy, odwołując się do każdej lokalizacji tablicy przy użyciu jej indeksu w nawiasach. Indeksy dla wielowymiarowych tablic są oddzielone przecinkami (,). Potrzebujesz jednego indeksu dla każdego wymiaru tablicy.

Poniższy przykład ukazuje niektóre instrukcje, które przechowywać i pobierać wartości w tablicach.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Wypełnianie tablicy przy użyciu literałów tablicy

Za pomocą literału tablicowego, możesz wypełnić tablicy o liczbie początkowy zestaw wartości w tym samym czasie, które możesz utworzyć. Literał tablicowy składa się z listy wartości rozdzielanych przecinkami, które są ujęte w nawiasy klamrowe (`{}`).

Tworząc tablicę przy użyciu literału tablicowego, możesz podać typ tablicy lub użyć wnioskowania typu, aby określić typ tablicy. Poniższy kod przedstawia obie opcje.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

Gdy używasz wnioskowania, typ tablicy zależy od *Typ dominujący* na liście wartości literału. Typ dominujący jest typem, do którego można rozszerzyć wszystkie inne typy w tablicy. Jeśli nie można ustalić tego typu unikatowego, Typ dominujący to unikatowy typ, do którego można zawęzić wszystkie inny typy w tablicy. Jeśli żadna z tych typów unikatowych nie można ustalić, typem dominującym jest `Object`. Na przykład, jeśli lista wartości, które jest dostarczane do literału tablicowego zawiera wartości typu `Integer`, `Long`, i `Double`, tablica wynikowa jest typu `Double`. Ponieważ `Integer` i `Long` rozszerzone tylko do `Double`, `Double` jest typem dominującym. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../language-features/data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> Wnioskowanie o typie można użyć tylko dla tablic, które są zdefiniowane jako zmiennych lokalnych w przypadku składowej typu. Jeśli definicja jawnego typu jest nieobecne, tablice zdefiniowane przy użyciu literałów tablicy na poziomie klasy mają wartości typu `Object[]`. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../variables/local-type-inference.md).

Należy zauważyć, że w poprzednim przykładzie zdefiniowano `values` jako tablicę typu `Double` , mimo że literały tablicowe są typu `Integer`. Można utworzyć tej tablicy, ponieważ wartości w literale tablicy można mogą zostać poszerzone do `Double` wartości.

Można również utworzyć i wypełnić tablicę wielowymiarową przy użyciu *zagnieżdżone literały tablicowe*. Zagnieżdżone literały tablicowe muszą mieć liczbę wymiarów, który jest zgodny z tablicą wynikową. Poniższy przykład tworzy tablicę dwuwymiarową liczb całkowitych przy użyciu zagnieżdżonych literałów tablicy.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

Przy użyciu zagnieżdżonych literałów tablicy, aby utworzyć i wypełnić tablicę, błąd występuje, jeśli liczba elementów w zagnieżdżonych literałach tablicowych nie są zgodne. Jeśli jawnie deklarować zmienną tablicy mają różną liczbę wymiarów niż literały tablicowe również wystąpi błąd.

Podobnie jak w przypadku tablic jednowymiarowych, tworząc tablicę wielowymiarową przy użyciu zagnieżdżonych literałów tablicy może polegać na wnioskowanie o typie. Wnioskowany typ to typ dominujący dla wszystkich wartości w literałach tablicowych dla wszystkich poziomów zagnieżdżenia. Poniższy przykład tworzy tablicę dwuwymiarową typu `Double[,]` z wartości typu `Integer` i `Double`.

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Aby uzyskać więcej przykładów, zobacz [jak: Inicjowanie zmiennej tablicy w języku Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Iterowanie przez tablicę

Podczas iteracji przez tablicę dostęp każdy element w tablicy, od najniższego indeksu do najwyższego lub od najwyższego do najniższego. Zwykle, użyj jednej [dla... Następna instrukcja](../../../language-reference/statements/for-next-statement.md) lub [For Each... Następna instrukcja](../../../language-reference/statements/for-each-next-statement.md) do iterowania po elementach tablicy. Jeśli nie znasz górne granice tablicy, możesz wywołać <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> metodę, aby uzyskać najwyższą wartość indeksu. Mimo że najniższa wartość indeksu jest prawie zawsze 0, możesz wywołać <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> metodę, aby uzyskać najniższa wartość indeksu.

Poniższy przykład wykonuje iterację przez tablicę jednowymiarową za pomocą [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) instrukcji.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

Poniższy przykład wykonuje iterację przez tablicę wielowymiarową przy użyciu [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) instrukcji. <xref:System.Array.GetUpperBound%2A> Metoda ma parametr, który określa wymiar. `GetUpperBound(0)` Zwraca najwyższy indeks pierwszego wymiaru i `GetUpperBound(1)` zwraca najwyższy indeks drugiego wymiaru.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

W poniższym przykładzie użyto [For Each... Następna instrukcja](../../../language-reference/statements/for-each-next-statement.md)do iteracji przez tablicę jednowymiarową i dwuwymiarową tablicę.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Rozmiar tablicy

Rozmiar tablicy jest produktem długości wszystkich jej wymiarów. Reprezentuje całkowitą liczbę elementów aktualnie znajdujących się w tablicy.  Na przykład poniższy przykład deklaruje 2-wymiarowej tablicy z czterema elementami w każdym wymiarze. Dane wyjściowe z przykładu pokazują, rozmiar tablicy to 16 (lub (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> Tablice nieregularne nie obejmuje tej dyskusji rozmiar tablicy. Aby uzyskać informacje na temat Tablice nieregularne i określenie rozmiaru tablicy nieregularnej, zobacz [nierówne tablic](#jagged-arrays) sekcji.

Możesz znaleźć rozmiar tablicy za pomocą <xref:System.Array.Length%2A?displayProperty=nameWithType> właściwości. Możesz znaleźć długość każdego wymiaru tablicy wielowymiarowej za pomocą <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.

Możesz zmienić rozmiar zmiennej tablicy, przypisując do niej nowy obiekt tablicy lub za pomocą [ `ReDim` instrukcji](../../../language-reference/statements/redim-statement.md) instrukcji. W poniższym przykładzie użyto `ReDim` instrukcję, aby zmienić 100-elementowej tablicy 51-elementowej tablicy.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Istnieje kilka kwestii, które należy pamiętać podczas zajmowania się rozmiarem tablicy.

|||
|---|---|
|Długość wymiaru|Indeks każdego wymiaru jest oparty na 0, co oznacza, że waha się od 0 do jego górnej granicy. W związku z tym długość danego wymiaru jest większa o jeden od deklarowanej górnej granicy tego wymiaru.|
|Limity długości|Długość każdego wymiaru tablicy jest ograniczona do maksymalnej wartości `Integer` typ danych, który jest <xref:System.Int32.MaxValue?displayProperty=nameWithType> lub (2 ^ 31) - 1. Jednakże całkowity rozmiar tablicy również jest ograniczony przez ilość pamięci dostępnej w systemie. Jeśli użytkownik podejmie próbę zainicjowania tablicy przekraczającej ilość dostępnej pamięci, środowisko wykonawcze zgłasza <xref:System.OutOfMemoryException>.|
|Rozmiar i rozmiar elementu|Rozmiar tablicy nie zależy od typu danych jej elementów. Rozmiar zawsze odzwierciedla całkowitą liczbę elementów, nie liczbę bajtów, które zajmują w pamięci.|
|Użycie pamięci|Nie jest bezpieczne robić założenia dotyczące, jak tablica jest przechowywana w pamięci. Magazyn różni się na platformach o różnych szerokościach danych, aby sama tablica może zużywać więcej pamięci w systemie 64-bitowym niż w przypadku 32-bitowego systemu. W zależności od konfiguracji systemu podczas inicjowania tablicy, środowisko uruchomieniowe języka wspólnego (CLR) można przypisać pamięci masowej do spakowania elementów tak blisko siebie jak to możliwe lub dostosować je wszystkie naturalnych ograniczeń sprzętowych. Również tablica wymaga magazynowania obciążenie dla informacji o kontroli i zwiększa to obciążenie z każdym dodanym wymiarem.|

## <a name="the-array-type"></a>Typ tablicy

Każda tablica ma typ danych, która różni się od typu danych jej elementów. Nie ma żadnych single — typ danych dla wszystkich tablic. Zamiast tego typ danych tablicy zależy od liczby wymiarów, lub *ranga*, tablicy i typ danych elementów w tablicy. Dwie tablice zmiennych są te same dane typu, tylko gdy mają tę samą rangę, a ich elementy mają ten sam typ danych. Długości wymiarów tablicy nie wpływają na typ danych tablicy.

Każda tablica dziedziczy z <xref:System.Array?displayProperty=nameWithType> klasy, a użytkownik może zadeklarować zmienną typu `Array`, ale nie można utworzyć tablicy typu `Array`. Na przykład mimo że poniższy kod deklaruje `arr` zmienną typu `Array` i wywołuje <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie tablicy typu tablicy okaże się, że obiekt [].

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

Ponadto [instrukcji ReDim](../../../language-reference/statements/redim-statement.md) nie może działać na zmiennej zadeklarowanej jako typ `Array`. Z tych powodów i dla zabezpieczeń typów zaleca się deklarować każdą tablicę jako określonego typu.

Można sprawdzić typ danych tablicy lub jej elementów na kilka sposobów.

- Możesz wywołać <xref:System.Object.GetType%2A> metody w zmiennej, aby pobrać <xref:System.Type> obiekt, który reprezentuje typu run-time w zmiennej. <xref:System.Type> Obiektu zawiera wyczerpujące informacje we właściwościach i metodach.
- Możesz przekazać zmienną do <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkcję w celu uzyskania `String` nazwę typu run-time.

Poniższy przykład wywołuje zarówno `GetType` metody i `TypeName` funkcję, aby określić typ tablicy. Typ tablicy to `Byte(,)`. Należy pamiętać, że <xref:System.Type.BaseType%2A?displayProperty=nameWithType> właściwość wskazuje, że typ podstawowy tej tablicy bajtowej jest <xref:System.Array> klasy.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Tablice jako wartości zwracane i parametry

Aby zwrócić tablicę z `Function` procedury, określ typ danych tablicy i liczbę wymiarów jako typ zwracany [Function — instrukcja](../../../language-reference/statements/function-statement.md). Wewnątrz funkcji Zadeklaruj zmienną lokalnej tablicy przy użyciu tego samego typu danych i liczbie wymiarów. W [instrukcji Return](../../../language-reference/statements/return-statement.md), obejmują zmienną lokalnej tablicy bez nawiasów.

Aby określić tablicę jako parametr do `Sub` lub `Function` procedury, zdefiniuj parametr jako tablicę przy użyciu określonego typu danych i liczbie wymiarów. W wywołaniu procedury należy przekazać zmienną tablicową o takim samym typie danych i liczbie wymiarów.

W poniższym przykładzie `GetNumbers` funkcja zwraca `Integer()`, Jednowymiarowa tablica typu `Integer`. `ShowNumbers` Akceptuje procedury `Integer()` argumentu.

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

W poniższym przykładzie `GetNumbersMultiDim` funkcja zwraca `Integer(,)`, tablicę dwuwymiarową typu `Integer`.  `ShowNumbersMultiDim` Akceptuje procedury `Integer(,)` argumentu.

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Tablice nieregularne

Czasami struktury danych w aplikacji są dwuwymiarowe, ale nie prostokątny. Może na przykład, skorzystaj z tablicy, do przechowywania danych dotyczących temperatura każdego dnia miesiąca. Pierwszego wymiaru tablicy reprezentuje miesiąca, ale drugiego wymiaru reprezentuje liczbę dni, a liczba dni w miesiącu nie jest jednolite. A *tablicy nieregularnej*, który jest również nazywany *tablicy tablic*, zaprojektowano pod kątem takich scenariuszy. Nieregularna tablica jest tablicą, której elementy są również tablic. Tablica nieregularna i każdy element w tablicy nieregularnej może mieć jeden lub więcej wymiarów.

W poniższym przykładzie użyto tablicę miesięcy, której każdy element jest tablicą dni. W przykładzie użyto tablicy nieregularnej, ponieważ różne miesiące mają różną liczbę dni.  W przykładzie pokazano sposób tworzenia tablicy nieregularnej, przypisać wartości do niego i pobrać i wyświetlić jego wartości.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

Poprzedni przykład przypisuje wartości do tablicy nieregularnej, na podstawie element po elemencie przy użyciu `For...Next` pętli. Można także przypisać wartości do elementów tablicy nieregularnej, przy użyciu zagnieżdżonych literałów tablicy. Jednak próbę użycia zagnieżdżonych literałów tablicy (na przykład `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) generuje błąd kompilatora [BC30568](../../../,,/../misc/bc30568.md). Aby poprawić ten błąd, należy umieścić wewnętrzne literały tablicowe w nawiasach. Nawiasy wymuszają wyrażeniu literalnym tablicy, mogło zostać ocenione, a wyniki są używane z zewnętrznym literałem tablicy, jak pokazano w poniższym przykładzie.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

Nieregularna Tablica to Jednowymiarowa tablica, której elementy zawierają tablic. W związku z tym <xref:System.Array.Length%2A?displayProperty=nameWithType> właściwości i `Array.GetLength(0)` metoda zwraca liczbę elementów w tablicy jednowymiarowej, i `Array.GetLength(1)` zgłasza <xref:System.IndexOutOfRangeException> ponieważ nie jest wielowymiarowej tablicy nieregularnej. Należy określić liczbę elementów w każdy element członkowski podtablicy poprzez pobranie wartości każdy element członkowski podtablicy <xref:System.Array.Length%2A?displayProperty=nameWithType> właściwości. Poniższy przykład ilustruje sposób określić liczbę elementów w tablicy nieregularnej.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Tablice o zerowej długości

Visual Basic rozróżnia między tablicą niezainicjowanej (tablicę, której wartość jest `Nothing`) i *tablicę o zerowej długości* lub pusta tablica (tablicę, która nie ma żadnych elementów.) Tablica niezainicjowanej jest taki, który nie został wymiary lub miał wszystkie wartości przypisane do niego. Na przykład:

```vb
Dim arr() As String
```

Tablicę o zerowej długości jest zadeklarowana za pomocą wymiaru-1. Na przykład:

```vb
Dim arrZ(-1) As String
```

Może być konieczne utworzyć tablicę o zerowej długości w następujących okolicznościach:

- Bez ryzyka <xref:System.NullReferenceException> wyjątek, kod musi mieć dostęp członkowie <xref:System.Array> klasy, takie jak <xref:System.Array.Length%2A> lub <xref:System.Array.Rank%2A>, lub wywołać funkcję języka Visual Basic, taką jak <xref:Microsoft.VisualBasic.Information.UBound%2A>.

- Chcesz uprościć kod, nie ma pod kątem `Nothing` w szczególnych przypadkach.

- Twój kod współdziała z interfejs programowania aplikacji (API), który wymaga przekazania tablicę o zerowej długości do jednej lub kilku procedur albo zwraca tablicę o zerowej długości z jedną lub kilkoma procedurami.

## <a name="splitting-an-array"></a>Podział tablicy

W niektórych przypadkach może być konieczne podzielić pojedynczą tablicę wiele tablic. Obejmuje to identyfikowanie punkt lub punkty, w których tablica jest rozliczany, a następnie plucie tablicy do co najmniej dwóch oddzielnych tablic.

> [!NOTE]
> W tej sekcji omówiono w nim dzielenie pojedynczego ciągu na tablicę ciągów, w oparciu o ogranicznika. Aby uzyskać informacji na temat dzielenia ciągu, zobacz <xref:System.String.Split%2A?displayProperty=nameWithType> metody.

Najbardziej typowe kryteria podział tablicy są:

- Liczba elementów w tablicy. Na przykład można podzielić tablicę więcej niż określoną liczbę elementów w przybliżeniu równe części. W tym celu można użyć wartości zwrócone przez <xref:System.Array.Length%2A?displayProperty=nameWithType> lub <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.

- Wartość elementu, który służy jako ogranicznika, która wskazuje, gdzie można podzielić tablicy. Można wyszukać określoną wartość, przez wywołanie metody <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> i <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> metody.

Po określeniu indeksu lub indeksów, w których można podzielić tablicy, będzie można utworzyć poszczególnych tablic, wywołując <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody.

Poniższy przykład dzieli tablicę na dwóch tablicach w przybliżeniu taki sam rozmiar. (Jeśli łączna liczba elementów tablicy jest nieparzysta, pierwsza tablica ma jeden element więcej od drugiego).

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

Poniższy przykład dzieli tablicę ciągów na dwóch tablicach, na podstawie obecności elementu, którego wartością jest "zzz", która służy jako ogranicznika tablicy. Nowe tablice nie dołączaj elementu, który zawiera ogranicznik.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Dołączenie do tablic

Liczba macierzy można także połączyć w jedną większe. Aby to zrobić, należy również użyć <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody.

> [!NOTE]
> W tej sekcji omówiono w nim dołączenie do tablicy ciągów w jeden ciąg. Aby uzyskać informacji na temat dołączania tablicę ciągów, zobacz <xref:System.String.Join%2A?displayProperty=nameWithType> metody.

Przed skopiowaniem elementów tablic do nowej tablicy, należy się najpierw upewnić już zainicjować tablicy, aby był wystarczająco dużą do obsługi nowej tablicy. Można to zrobić na jeden z dwóch sposobów:

- Użyj [ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md) instrukcję, aby dynamicznie rozwiń tablicy przed dodaniem nowych elementów. Jest to najprostszy technika, ale może powodować spadek wydajności i zużycia zbyt dużej ilości pamięci, kopiując duże tablice.
- Oblicz sumę elementów potrzebnych do nowej tablicy dużych, a następnie dodaj elementy tablicy każdego źródła do niego.

W poniższym przykładzie użyto drugiej metody, aby dodać czterech tablic dziesięć elementów do pojedynczej macierzy.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Ponieważ w tym przypadku tablic źródła są wszystkie małe, firma Microsoft jest również dynamicznie rozwiń tablicy dodanie do niej elementy każdej nowej tablicy. Poniższy przykład robi to.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Kolekcje jako alternatywa dla tablic

Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą jednoznacznie silnych obiektów. Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W odróżnieniu od tablic, które wymagają jawnie zmienić rozmiar tablicy o liczbie [ `ReDim` instrukcji](../../../language-reference/statements/redim-statement.md), kolekcje rosnąć i maleć dynamicznie, wraz z aplikacji zmienia się zapotrzebowanie.

Kiedy używasz `ReDim` do redimension tablicę, Visual Basic tworzy nową tablicę i zwalnia poprzednią. Spowoduje to przejście czasu wykonywania. W związku z tym jeśli liczba elementów, który aktualnie pracuje ulega częstym zmianom, lub nie można przewidzieć maksymalną liczbę elementów, których potrzebujesz, zazwyczaj będzie uzyskać lepszą wydajność, używając kolekcji.

W niektórych kolekcjach można przypisać klawisz do dowolnych obiektów umieszczonych do kolekcji, tak aby pozwala na szybkie pobranie obiektu przy użyciu klucza.

Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólna kolekcja wymusza typ bezpieczeństwa tak, aby żaden typ danych można dodać do niego.

Aby uzyskać więcej informacji na temat kolekcji, zobacz [kolekcje](../../concepts/collections.md).

## <a name="related-topics"></a>Tematy pokrewne

|Termin|Definicja|
|----------|----------------|
|[Wymiary tablic w języku Visual Basic](../../language-features/arrays/array-dimensions.md)|Wyjaśnia rangę i wymiary w tablicach.|
|[Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md)|Zawiera opis sposobu wypełniania tablic z wartościami początkowymi.|
|[Instrukcje: Sortowanie tablicy w języku Visual Basic](../../language-features/arrays/how-to-sort-an-array.md)|Pokazuje jak alfabetycznie sortować elementy tablicy.|
|[Instrukcje: Przypisywanie tablicy do innej tablicy](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|W tym artykule opisano zasady i czynności podczas przypisywania tablicy do innej zmiennej tablicy.|
|[Rozwiązywanie problemów związanych z tablicami](../../language-features/arrays/troubleshooting-arrays.md)|W tym artykule omówiono niektóre typowe problemy, które występują podczas pracy z tablicami.|

## <a name="see-also"></a>Zobacz także

- <xref:System.Array?displayProperty=nameWithType>
- [Dim, instrukcja](../../../language-reference/statements/dim-statement.md)
- [ReDim, instrukcja](../../../language-reference/statements/redim-statement.md)
