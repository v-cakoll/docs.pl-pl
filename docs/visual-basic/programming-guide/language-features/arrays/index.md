---
title: Tablice w Visual Basic
ms.custom: ''
ms.date: 12/06/2017
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: d223ca8b0ff59a13c31fa777e5cb6a97918421c6
ms.sourcegitcommit: 01ea3686e74ff05e4f6de3d8d46dc603d051ec00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2017
---
# <a name="arrays-in-visual-basic"></a>Tablice w Visual Basic
Tablica to zbiór wartości, które są określane jako *elementy*, logicznie powiązanych ze sobą. Na przykład tablicy może składać się z liczby studentów w każdej klasy w szkole gramatyki; Każdy element tablicy jest liczba studentów w jednej kategorii. Podobnie Tablica może składać się z klas Studenta dla klasy; Każdy element tablicy jest jednej klasy.    

Jest możliwe poszczególne zmienne do przechowywania wszystkich naszych elementów danych. Na przykład jeśli naszej aplikacji analizuje ocen studentów, możemy użyć zmiennej osobne dla każdego Studenta, takich jak `englishGrade1`, `englishGrade2`itp. Takie podejście ma trzy główne ograniczenia:
- Musimy wiedzieć w czasie projektowania, dokładnie tak jak wiele klas mamy do obsługi.
- Szybko obsługi dużej liczby klas staje się niewygodna. To z kolei powoduje, że aplikacja będzie mieć poważnych usterek.
- Jest trudne w utrzymaniu. Każdej nowej klasy, które możemy dodać wymaga aplikacji można modyfikować, ponownie skompilowana czy ponownego wdrożenia.  
 
 Korzystając z tablicy, można odwoływać się do tych powiązanych wartości o tej samej nazwie i użyj liczby, która jest wywoływana *indeksu* lub *indeks dolny* do identyfikowania pojedynczego elementu oparte na jej położenie w tablicy. Indeksy tablicy z zakresu od 0 do jednego mniejszy niż liczba elementów w tablicy. Użycie składni języka Visual Basic określenie rozmiaru tablicy, należy określić jego najwyższy indeks nie całkowita liczba elementów w tablicy. Możesz pracować z tablicy jako jednostki, a możliwość przejść elementów zwalnia z znajomości dokładnie tak jak wiele elementów zawiera w czasie projektowania.
  
 Przykłady szybkie przed wyjaśnienie:  
  
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
  
 ## <a name="in-this-article"></a>W tym artykule
  
- [Elementy tablicy w tablicy proste](#array-elements-in-a-simple-array)  
  
- [Tworzenie tablicy](#creating-an-array)  
  
- [Przechowywanie wartości w tablicy](#storing-values-in-an-array)  
  
- [Wypełnianie tablicy o Literały tablicy](#populating-an-array-with-array-literals)  
  
- [Iteracja przez tablicy](#iterating-through-an-array)  
  
- [Rozmiar tablicy](#BKMK_ArraySize)  

- [Typ tablicy](#the-array-type)  
  
- [Użycie tablic jako parametry i wartości zwracane](#arrays-as-return-values-and-parameters)  
- [Tablice nieregularne](#jagged-arrays)  
  
- [Tablice o zerowej długości](#zero-length-arrays)  

- [Podział tablicy](#splitting-an-array)
  
- [Kolekcje alternatywą dla tablic](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a>Elementy tablicy w tablicy proste  

Utwórz tablicy o nazwie `students` do przechowywania liczba studentów w każdej klasy w szkole gramatyki. Indeksy elementy zakresu od 0 do 6. Przy użyciu tej tablicy jest łatwiejsze niż w przypadku deklarowania zmiennych siedem.

Na poniższej ilustracji pokazano `students` tablicy. Dla każdego elementu tablicy:  
  
-   Indeks elementu reprezentuje kategorii (i klasa reprezentuje indeksem 0).
  
-   Wartość, która jest zawarta w elemencie reprezentuje liczbę studentów w tej klasy.
  
 ![Obraz przedstawiający liczby studentów tablicy](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
Elementy tablicy "studentów"  
 
Poniżej przedstawiono przykład zawierający kod Visual Basic, które tworzy i korzysta z tablicy:

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

Przykład wykonuje trzy czynności:

- Deklaruje `students` tablicy z siedmiu elementów. Liczba `6` w tablicy deklaracji wskazuje ostatni indeks w tablicy, jest jednym mniejszy niż liczba elementów w tablicy.
- Przypisuje do każdego elementu w tablicy wartości. Elementy tablicy uzyskują dostęp przy użyciu nazwy tablicy i, w tym indeks pojedynczego elementu w nawiasach.
- Wyświetla listę każdej wartości w tablicy. W przykładzie użyto [ `For` ](../../../language-reference/statements/for-next-statement.md) instrukcji, aby uzyskać dostęp każdy element tablicy za pomocą numeru indeksu.
  
 `students` Tablicy w poprzednim przykładzie jest tablicą jednowymiarową, ponieważ używa jednego indeksu. Tablica, która korzysta z więcej niż jednego indeksu lub indeks dolny jest nazywany *wielowymiarowe*. Aby uzyskać więcej informacji, zobacz w dalszej części tego artykułu i [wymiary tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="creating-an-array"></a>Tworzenie tablicy  
 
Rozmiar tablicy można zdefiniować na kilka sposobów: 

- Można określić rozmiar, gdy tablica jest zadeklarowany jako:
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - Można użyć `New` klauzuli umożliwiają określanie rozmiaru tablicy po utworzeniu:  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 Jeśli masz istniejącej tablicy, można ponownie zdefiniować jego rozmiar za pomocą [ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md) instrukcji. Można określić, że `Redim` instrukcji Zachowaj wartości, które znajdują się w tablicy lub można określić, aby go utworzyć pustą tablicę. W poniższym przykładzie przedstawiono różne zastosowania `Redim` instrukcji, aby zmienić rozmiar istniejącej tablicy.  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz [instrukcji ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="storing-values-in-an-array"></a>Przechowywanie wartości w tablicy
 
 Dostęp do każdej lokalizacji w tablicy przy użyciu indeksu typu `Integer`. Umożliwia przechowywanie i pobieranie wartości w tablicy za pomocą odwołań do każdej lokalizacji tablicy przy użyciu jej indeksu w nawiasach. Indeksy tablic wielowymiarowych są oddzielone przecinkami (,). Należy jeden indeks dla każdego wymiaru tablicy. 

W poniższym przykładzie przedstawiono niektóre instrukcji, które przechowują i pobierają wartości w tablicach.
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a>Wypełnianie tablicy o Literały tablicy
 Przy użyciu tablicy literału, można wypełnić tablicy o początkowego zestawu wartości, w tym samym czasie, który go utworzyć. Literał tablicy składa się z listy wartości rozdzielanych przecinkami ujętych w nawiasy klamrowe (`{}`).  
  
 Po utworzeniu tablicy przy użyciu literał tablicy można podać typ tablicy lub wnioskowanie umożliwia określenie typu tablicy. W poniższym przykładzie przedstawiono obie opcje.  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 Gdy używasz wnioskowanie o typie typ tablicy jest określany przez *typu dominującą* na liście wartości literałów. Dominującą typem jest typ, do którego poszerzyć wszystkie typy w tablicy. Nie można określić tego typu unikatowy, ten typ dominującej nie jest unikatowy typ, do której wszystkie typy w tablicy można ograniczyć. Jeśli żadna z tych typów unikatowy nie można ustalić, jest typu dominującą `Object`. Na przykład, jeśli lista wartości jest dostarczany do tablicy literału zawiera wartości typu `Integer`, `Long`, i `Double`, wynikowy tablicy jest typu `Double`. Ponieważ `Integer` i `Long` poszerzyć tylko z `Double`, `Double` jest dominującą typu. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). 
 
> [!NOTE] 
> Wnioskowanie o typie można użyć tylko dla tablic, które są zdefiniowane jako zmienne lokalne w przypadku elementu członkowskiego typu. Jeśli istnieje definicja typu jawnego zdefiniowane przy użyciu literałów tablicy na poziomie klasy tablic są typu `Object[]`. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../variables/local-type-inference.md). 

Należy pamiętać, że w poprzednim przykładzie zdefiniowano `values` jako tablica typu `Double` , mimo że Literały tablicy są typu `Integer`. Można utworzyć tej tablicy, ponieważ wartości w tablicy literału można rozszerzyć do `Double` wartości. 
  
 Można również utworzyć i wypełnić tablicy wielowymiarowej przy użyciu *zagnieżdżone Literały tablicy*. Tablica zagnieżdżona literały musi mieć liczbę wymiarów jest zgodna z tablicy wynikowej. W poniższym przykładzie tworzona jest tablicą dwuwymiarową liczb całkowitych przy użyciu literałów tablica zagnieżdżona.  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
Podczas tworzenia i wypełniania tablicy przy użyciu literałów tablica zagnieżdżona, błąd występuje, gdy liczba elementów w literałach tablica zagnieżdżona nie są zgodne. Błąd występuje także jeśli jawnie zadeklarować zmiennej tablicowej mają różną liczbę wymiarów niż Literały tablicy. 
  
Podobnie jak w przypadku tablice jednowymiarowe, tworząc tablicy wielowymiarowej tablicy zagnieżdżonych literały może polegać na wnioskowanie o typie. Wnioskowany typ jest typem dominującą dla wszystkich wartości w literałach tablicy dla wszystkich poziomu zagnieżdżenia. W poniższym przykładzie tworzona jest tablicą dwuwymiarową typu `Double[,]` z wartości typu `Integer` i `Double`.  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 Aby uzyskać dodatkowe przykłady, zobacz [porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="iterating-through-an-array"></a>Iteracja przez tablicy  
 Podczas iteracji tablicy dostęp do każdego elementu w tablicy z najniższym indeksie jako najwyższe lub najwyższą malejąco. Zwykle, albo użyć use [dla... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md) lub [dla każdego... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) do iterowania po elementach tablicy. Jeśli nie znasz górną granicę tablicy, należy wywołać <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> metodę, aby uzyskać najwyższą wartość indeksu. Mimo że najniższa wartość indeksu jest prawie zawsze 0, możesz wywołać <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> metody, aby uzyskać najmniejszą wartość z indeksu.   
  
 Poniższy przykład iteruje tablicą jednowymiarową przy użyciu [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcji. 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 Poniższy przykład iteruje tablicy wielowymiarowej przy użyciu [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) instrukcji. <xref:System.Array.GetUpperBound%2A> Metoda ma parametr, który określa wymiar. `GetUpperBound(0)`Zwraca indeks najwyższy wymiar i `GetUpperBound(1)` zwraca najwyższy indeks drugi wymiar.
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 W poniższym przykładzie użyto [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)do iteracji, a tablicą jednowymiarową tablicą dwuwymiarową.  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a>Rozmiar tablicy  

 Rozmiar tablicy jest produktem długości jej wymiarów. Reprezentuje sumę elementów aktualnie znajdujących się w tablicy.  Na przykład poniższy przykład deklaruje 2-wymiarową tablicą z czterech elementów w każdego wymiaru. Jak pokazano na dane wyjściowe z przykładu, rozmiar tablicy wynosi 16 (lub (3 + 1) * (3 + 1).

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> Rozważania rozmiar tablicy nie ma zastosowania do Tablice nieregularne. Aby uzyskać informacje na Tablice nieregularne i określania rozmiaru tablicy nieregularnej, zobacz [Tablice nieregularne](#jagged-arrays) sekcji.
  
  Rozmiar tablicy można znaleźć przy użyciu <xref:System.Array.Length%2A?displayProperty=nameWithType> właściwości. Długość każdego wymiaru tablicy wielowymiarowej można znaleźć przy użyciu <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.  
  
 Możesz zmienić rozmiar zmienną tablicową przez przypisanie do niego nowy obiekt tablicy lub za pomocą [ `ReDim` instrukcji](../../../../visual-basic/language-reference/statements/redim-statement.md) instrukcji. W poniższym przykładzie użyto `ReDim` instrukcji, aby zmienić tablicy 100 elementu do tablicy 51 elementu.

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 Istnieje kilka kwestii, które należy wziąć pod uwagę podczas pracy nad rozmiar tablicy.  
  
|||  
|---|---|  
|Długość wymiaru|Indeks każdego wymiaru jest oparty na 0, co oznacza, że jej zakresu od 0 do jego górnej granicy. W związku z tym długość danego wymiaru jest większa niż górna granica zadeklarowane tego wymiaru o jeden.|  
|Limity długości|Długość każdego wymiaru tablicy jest ograniczona do maksymalnej wartości `Integer` typ danych, który jest <xref:System.Int32.MaxValue?displayProperty=nameWithType> lub (2 ^ 31) - 1. Całkowity rozmiar tablicy również jest jednak ograniczona przez pamięci w systemie. Jeśli podjęto próbę zainicjowania tablicy przekraczający ilość dostępnej pamięci, zgłasza wyjątek środowiska uruchomieniowego <xref:System.OutOfMemoryException>.|  
|Rozmiar i rozmiaru elementu|Rozmiar tablicy nie zależy od typu danych swoich elementów. Rozmiar zawsze stanowi całkowita liczba elementów, nie liczba bajtów, które wykorzystują one w pamięci.|  
|Zużycie pamięci|Nie jest bezpieczne wszystkie założenia dotyczące sposobu tablicy jest przechowywany w pamięci. Dzięki tej samej tablicy można korzystać z większej ilości pamięci w 64-bitowym systemie niż w 32-bitowym systemie magazynu różni się na platformach szerokości innych danych. W zależności od konfiguracji systemu podczas inicjowania tablicy, środowisko uruchomieniowe języka wspólnego (CLR) można przypisać magazynu albo elementy pakietów, jak blisko siebie jak to możliwe, aby wyrównać je na granice fizyczne sprzętu. Ponadto tablicy wymaga magazynu narzut jego informacje o kontroli, a ten narzut zwiększa się wraz z każdego wymiaru dodany.|  

## <a name="the-array-type"></a>Typ tablicy 
 Co tablica zawiera dane typu, co różni się od typu danych swoich elementów. Nie ma typu danych dla wszystkich tablic. Zamiast tego typu danych tablicy zależy od liczby wymiarów, lub *rangę*z tablicy, a typ danych elementów w tablicy. Dwóch zmiennych tablicowych mają te same dane typu, tylko gdy mają one taką samą rangę, i ich elementy mają ten sam typ danych. Długości wymiary tablicy nie wpływają na dane typu tablicy.  
  
 Co tablica dziedziczy <xref:System.Array?displayProperty=nameWithType> klasy, a można zadeklarować zmiennej typu `Array`, ale nie można utworzyć tablicy typu `Array`. Na przykład chociaż deklaruje następującego kodu `arr` zmiennej typu `Array` i wywołuje <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody tworzenia wystąpienia tablicy typu tablicy okaże się, że obiekt [].

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

Ponadto [instrukcji ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md) nie może działać na zmienną zadeklarowany jako typ `Array`. Z tego względu i bezpieczeństwo typów zalecane jest aby zadeklarować co tablica jako określonego typu.  
  
 Można ustalić typu danych tablicy lub jego elementów na kilka sposobów. 
  
-   Możesz wywołać <xref:System.Object.GetType%2A> metody w zmiennej, aby uzyskać <xref:System.Type> obiekt, który reprezentuje typu run-time zmiennej. <xref:System.Type> Obiekt zawiera szczegółowe informacje w jego właściwości i metody.  
  
-   Można przekazać zmiennej <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkcji, aby pobrać `String` o nazwie typu run-time.  
  
 Poniższy przykład wywołuje zarówno `GetType` — metoda i `TypeName` funkcji można określić typu tablicy. Typ tablicy jest `Byte(,)`. Należy pamiętać, że <xref:System.Type.BaseType%2A?displayProperty=nameWithType> właściwość wskazuje, że typ podstawowy tablicy bajtów jest <xref:System.Array> klasy.  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a>Użycie tablic jako parametry i wartości zwracane  
 Aby zwracało tablicę z `Function` procedury, określ typ tablicy danych i liczby wymiarów jako typ zwracany [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md). W funkcji należy zadeklarować zmiennej lokalnej tablicy z tego samego typu danych i liczby wymiarów. W [zwracać instrukcji](../../../../visual-basic/language-reference/statements/return-statement.md), obejmują zmiennej lokalnej tablicy bez nawiasów.  
  
 Aby określić tablicę jako parametr `Sub` lub `Function` procedury, zdefiniuj dany parametr w postaci tablicy z określonego typu danych i liczby wymiarów. W wywołaniu procedury można przekazać zmiennej tablicowej z tego samego typu danych i liczby wymiarów.  
  
 W poniższym przykładzie `GetNumbers` funkcja zwraca `Integer()`, jest tablicą jednowymiarową typu `Integer`. `ShowNumbers` Akceptuje procedury `Integer()` argumentu. 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 W poniższym przykładzie `GetNumbersMultiDim` funkcja zwraca `Integer(,)`, jest tablicą dwuwymiarową typu `Integer`.  `ShowNumbersMultiDim` Akceptuje procedury `Integer(,)` argumentu.  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a>Tablice nieregularne  
 
Czasami struktury danych w aplikacji jest dwuwymiarowa, ale nie prostokątny. Na przykład można użyć tablicy do przechowywania danych o wysokiej temperatury każdego dnia miesiąca. Pierwszy wymiar tablicy reprezentuje miesiąca, ale drugi wymiar reprezentuje liczbę dni i liczbę dni w miesiącu nie jest uniform. A *tablicy nieregularnej*, który jest również nazywany *tablicy tablic*, jest przeznaczona dla takich scenariuszy. Tablicy nieregularnej jest tablicą, której elementy są również tablic. A każdy element tablicy nieregularnej tablicy nieregularnej może mieć co najmniej jeden wymiar.  
  
 W poniższym przykładzie użyto tablicy miesięcy, każdy element jest tablicą dni. W przykładzie użyto tablicy nieregularnej, ponieważ inny miesiące mają różną liczbę dni.  W przykładzie przedstawiono sposób tworzenia tablicy nieregularnej, przypisz wartości i pobierania i wyświetlania wartości.
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

Poprzedni przykład przypisuje wartości do tablicy nieregularnej na poszczególnych elementów — za pomocą `For...Next` pętli. Można także przypisać wartości do elementów tablicy nieregularnej przy użyciu literałów tablica zagnieżdżona. Jednak zagnieżdżone próbę użycia tablicy literały (na przykład ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) generuje błąd kompilatora [BC30568](../../../,,/../misc/bc30568.md). Aby naprawić błąd, należy umieścić literały wewnętrzny tablicy w nawiasach. Nawiasy wymusić wyrażenie literału tablicy ma zostać obliczone, a wyniki są używane z zewnętrznego tablicowych, jak pokazano na poniższym przykładzie.  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

Tablicy nieregularnej jest tablicą jednowymiarową, której elementy zawierają tablic. W związku z tym <xref:System.Array.Length%2A?displayProperty=nameWithType> właściwości i `Array.GetLength(0)` metoda zwraca liczbę elementów w tablicy jednowymiarowej tablicy, i `Array.GetLength(1)` zgłasza <xref:System.IndexOutOfRangeException> ponieważ nieregularna tablica nie jest wielowymiarowy. Określenie liczby elementów w każdej subarray pobierając wartość każdego subarray <xref:System.Array.Length%2A?displayProperty=nameWithType> właściwości. Poniższy przykład przedstawia sposób określania liczby elementów w tablicy nieregularnej.

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a>Tablice o zerowej długości  
Visual Basic rozróżnia między tablicą niezainicjowanej (tablicy, którego wartość jest `Nothing`) i *o zerowej długości tablicy* lub pusta tablica (tablicę, która nie ma żadnych elementów.) Tablica niezainicjowanej to taki, który nie został wymiarów lub ma przypisane wartości. Na przykład:

```vb
Dim arr() As String
```
Tablicą o zerowej długości jest zadeklarowana z wymiarem-1. Na przykład:

```vb
Dim arrZ(-1) As String
```
Być może musisz utworzyć tablicą o zerowej długości w następujących okolicznościach:  
  
-   Bez ryzyka <xref:System.NullReferenceException> wyjątek, kod muszą uzyskać dostęp do elementów członkowskich <xref:System.Array> klas, takich jak <xref:System.Array.Length%2A> lub <xref:System.Array.Rank%2A>, lub takie jak wywołania funkcji języka Visual Basic <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Aby zachować proste, ponieważ nie ma do sprawdzenia kodu `Nothing` w szczególnych przypadkach.  
  
-   Kod współdziała z interfejs programowania aplikacji (API), które musisz przekazać tablicą o zerowej długości do jednego lub więcej procedur lub zwraca tablicę o zerowej długości z jedną lub więcej procedur.

## <a name="splitting-an-array"></a>Podział tablicy

W niektórych przypadkach może być konieczne podzielone pojedynczą tablicę wiele tablic. Obejmuje to wskazującego punkt lub punkty, w których tablica jest rozliczany, a następnie plucie tablicy w co najmniej dwa oddzielne tablic. 

> [!NOTE] 
> W tej sekcji omówiono dzielenia pojedynczy ciąg w formie tablicy ciągów opartej na niektórych ogranicznika. Uzyskać rozdzielenie ciąg, zobacz <xref:System.String.Split%2A?displayProperty=nameWithType> metody.

Najbardziej typowe kryteria podział tablicy są:

- Liczba elementów w tablicy. Na przykład można podzielić na tablicę więcej niż określoną liczbę elementów w przybliżeniu równe części. W tym celu możesz użyć wartości zwracanych przez jedną <xref:System.Array.Length%2A?displayProperty=nameWithType> lub <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.

- Wartość elementu, który służy jako ogranicznik, który określa, gdzie można podzielić tablicy. Można wyszukać określoną wartość, przez wywołanie metody <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> i <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> metody.
 
Po określeniu indeksu lub indeksy, w których można podzielić tablicy poszczególnych tablic następnie można utworzyć przez wywołanie metody <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody. 

Poniższy przykład dzieli tablicy na dwóch tablic około taki sam rozmiar. (Jeśli łączna liczba elementów tablicy jest nieparzysta, pierwsza tablica ma jeden element więcej niż drugi). 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

Poniższy przykład dzieli tablicy ciągów na dwie tablice, na podstawie obecności elementu, którego wartość wynosi "zzz", która służy jako ogranicznik tablicy. Nowe tablice nie dołączaj element, który zawiera ogranicznik.

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a>Sprzęganie tablic

Można również połączyć wiele tablic w pojedynczą tablicę większy. Aby to zrobić, możesz również użyć <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody. 

> [!NOTE] 
> W tej sekcji omówiono dołączenie tablicy ciągów w jednym ciągu. Aby uzyskać informacje na dołączenie tablicy ciągów, zobacz <xref:System.String.Join%2A?displayProperty=nameWithType> metody.

Przed rozpoczęciem kopiowania elementów każdej macierzy do nowej tablicy, należy najpierw upewnić zostały zainicjowane tablicy, aby był wystarczająco duże, aby accompodate nowej tablicy. Można to zrobić na jeden z dwóch sposobów:

- Użyj [ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md) instrukcji, aby dynamicznie rozwinąć tablicy przed dodaniem nowych elementów do niego. To najprostszy technika, ale może to spowodować spadek wydajności i zmniejszenie zużycia pamięci nadmiernego podczas kopiowania dużych tablic.
- Obliczanie całkowitej liczby elementy potrzebne do nowego dużą tablicę, a następnie dodaj do niej elementy tablicy każdego źródła.

W poniższym przykładzie użyto drugiej metody, aby dodać czterech tablic dziesięć elementów do pojedynczej tablicy.  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

Ponieważ w takim przypadku tablice źródła są wszystkie małe, będziemy również dynamicznie rozwiń tablicy jak możemy dodać do niej elementy każdej nowej tablicy. Poniższy przykład robi to.

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a>Kolekcje alternatywą dla tablic  
 Tablice są najbardziej przydatne do tworzenia i Praca z stała liczba silnie typizowanych obiektów. Kolekcje umożliwiają bardziej elastyczne do pracy z grupy obiektów. W przeciwieństwie do tablic, które wymagają jawnie zmienić rozmiar tablicy z [ `ReDim` instrukcji](../../../../visual-basic/language-reference/statements/redim-statement.md), kolekcje zwiększyć lub zmniejszyć dynamicznie, musi mieć zmiany aplikacji.  
  
 Jeśli używasz `ReDim` do zmiany jego wymiarów tablicy, Visual Basic tworzy nową macierz i zwalnia poprzedni. Trwa to czas wykonania. W związku z tym jeśli liczba elementów, które użytkownik pracuje z ulegają częstym zmianom, lub nie można przewidzieć maksymalną liczbę elementów, które są potrzebne, zazwyczaj będzie uzyskać lepszą wydajność przy użyciu kolekcji.  
  
 Niektóre zbiory klucza można przypisać do wszystkich obiektów, które można umieścić w kolekcji, tak, aby szybko można pobrać obiektu przy użyciu klucza.  
  
 Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólnej kolekcji wymusza zabezpieczenie typów, dzięki czemu można dodać do niego inny typ danych.  
  
 Aby uzyskać więcej informacji o kolekcjach, zobacz [kolekcji](../../concepts/collections.md).
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Termin|Definicja|  
|----------|----------------|  
|[Wymiary tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Wyjaśniono rangę i wymiary tablic.|  
|[Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Opisuje sposób wypełnienia tablic o wartości początkowej.|  
|[Porady: Sortowanie tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Pokazuje sposób sortowania elementów tablicy alfabetycznie.|  
|[Instrukcje: przypisywanie tablicy do innej tablicy](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Opisuje zasady i kroki przypisywanie tablicy do innej tablicy zmiennej.|  
|[Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|W tym artykule omówiono niektóre typowe problemy, które występują podczas pracy z tablicami.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array?displayProperty=nameWithType>  
 [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim, instrukcja](../../../../visual-basic/language-reference/statements/redim-statement.md)
