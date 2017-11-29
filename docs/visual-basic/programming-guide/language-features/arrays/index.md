---
title: Tablice w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04deeccd19fd4edb3f2c88310d660eedf5c707d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-in-visual-basic"></a>Tablice w Visual Basic
Tablica jest zestaw wartości logicznie powiązanych ze sobą, takie jak liczba studentów w każdej klasy w szkole gramatyki.  Jeśli szukasz pomocy tablic w języku Visual Basic for Applications (VBA), zobacz [materiały referencyjne dotyczące języka](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx).  
  
 Przy użyciu tablicy, można odwoływać się do tych powiązanych wartości o tej samej nazwie i odpowiedni numer została wywołana indeksu lub indeks, aby wiedzieli, od siebie. Poszczególne wartości są określane jako elementy tablicy. Są one ciągłe z indeksem 0 za pośrednictwem najwyższą wartość indeksu.  
  
 W przeciwieństwie do tablicy, nosi nazwę zmiennej, która zawiera pojedynczą wartość *skalarne* zmiennej.  
  
 Przykłady szybkie przed wyjaśnienie:  
  
```vb  
'Declare a single-dimension array of 5 values  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set array element values  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
'Redefine the size of an existing array retaining the current values  
ReDim Preserve numbers(15)  
  
'Redefine the size of an existing array, resetting the values  
ReDim numbers(15)  
  
'Declare a multi-dimensional array  
Dim matrix(5, 5) As Double  
  
'Declare a multi-dimensional array and set array element values  
Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}}  
  
'Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 **W tym temacie**  
  
-   [Elementy tablicy w tablicy proste](#BKMK_ArrayElements)  
  
-   [Tworzenie tablicy](#BKMK_CreatingAnArray)  
  
-   [Przechowywanie wartości w tablicy](#BKMK_StoringValues)  
  
-   [Wypełnianie tablicy o wartości początkowej](#BKMK_Populating)  
  
    -   [Tablica zagnieżdżona literałów](#BKMK_NestedArrayLiterals)  
  
-   [Iteracja przez tablicy](#BKMK_Iterating)  
  
-   [Użycie tablic jako parametry i wartości zwracane](#BKMK_ReturnValues)  
  
-   [Tablice nieregularne](#BKMK_JaggedArrays)  
  
-   [Tablice o zerowej długości](#BKMK_ZeroLength)  
  
-   [Rozmiar tablicy](#BKMK_ArraySize)  
  
-   [Typy tablicy i innych typów](#BKMK_ArrayTypes)  
  
-   [Kolekcje alternatywą dla tablic](#BKMK_Collections)  
  
##  <a name="BKMK_ArrayElements"></a>Elementy tablicy w tablicy proste  
 Poniższy przykład deklaruje zmienną tablicową do przechowania liczby studentów w każdej klasy w szkole gramatyki.  
  
 [!code-vb[VbVbalrArrays#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#2)]  
  
 Tablica `students` w poprzednim przykładzie zawiera elementy siedem. Indeksy elementy zakresu od 0 do 6. Ta tablica o jest łatwiejsze niż deklarowania zmiennych siedem.  
  
 Na poniższej ilustracji przedstawiono tablicy `students`. Dla każdego elementu tablicy:  
  
-   Indeks elementu reprezentuje kategorii (i klasa reprezentuje indeksem 0).  
  
-   Wartość, która jest zawarta w elemencie reprezentuje liczbę studentów w tej klasy.  
  
 ![Obraz przedstawiający liczby studentów tablicy](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
Elementy tablicy "studentów"  
  
 Poniższy przykład przedstawia sposób znaleźć pierwszy, drugi i w ostatnim elemencie tablicy `students`.  
  
 [!code-vb[VbVbalrArrays#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#3)]  
  
 To odwołanie do tablicy jako całość, używając tylko nazwy zmiennej tablicowej bez indeksów.  
  
 Tablica `students` w poprzednim przykładzie używa jeden indeks i ma być jednowymiarowa. Tablica, która korzysta z więcej niż jednego indeksu lub indeks dolny jest nazywany wielowymiarowych. Aby uzyskać więcej informacji, zobacz pozostałej części tego tematu i [wymiary tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="BKMK_CreatingAnArray"></a>Tworzenie tablicy  
 Można określić rozmiaru tablicy na kilka sposobów. Gdy tablica jest zadeklarowany jako w poniższym przykładzie pokazano, możesz podać rozmiar.  
  
 [!code-vb[VbVbalrArrays#12](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#12)]  
  
 Można również użyć `New` klauzuli umożliwiają określanie rozmiaru tablicy po utworzeniu, jak przedstawiono na poniższym przykładzie.  
  
 [!code-vb[VbVbalrArrays#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#11)]  
  
 Jeśli masz istniejącej tablicy, można ponownie zdefiniować jego rozmiar za pomocą `Redim` instrukcji. Można określić, że `Redim` instrukcji należy przechowywać wartości, które znajdują się w tablicy lub można określić, aby go utworzyć pustą tablicę. W poniższym przykładzie przedstawiono różne zastosowania `Redim` instrukcji, aby zmienić rozmiar istniejącej tablicy.  
  
 [!code-vb[VbVbalrArrays#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#13)]  
  
 Aby uzyskać więcej informacji, zobacz [instrukcji ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="BKMK_StoringValues"></a>Przechowywanie wartości w tablicy  
 Dostęp do każdej lokalizacji w tablicy przy użyciu indeksu typu `Integer`. Umożliwia przechowywanie i pobieranie wartości w tablicy za pomocą odwołań do każdej lokalizacji tablicy przy użyciu jej indeksu w nawiasach. Indeksy tablic wielowymiarowych są oddzielone przecinkami (,). Należy jeden indeks dla każdego wymiaru tablicy. W poniższym przykładzie przedstawiono niektóre instrukcje, które przechowują wartości w tablicach.  
  
 [!code-vb[VbVbalrArrays#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#5)]  
  
 W poniższym przykładzie przedstawiono niektóre instrukcji, które pobiera wartości z tablic.  
  
 [!code-vb[VbVbalrArrays#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#6)]  
  
##  <a name="BKMK_Populating"></a>Wypełnianie tablicy o wartości początkowej  
 Przy użyciu tablicy literału, można utworzyć tablicę zawierającą początkowego zestawu wartości. Literał tablicy składa się z listy wartości rozdzielanych przecinkami ujętych w nawiasy klamrowe (`{}`).  
  
 Po utworzeniu tablicy przy użyciu literał tablicy można podać typ tablicy lub wnioskowanie umożliwia określenie typu tablicy. Poniższy kod przedstawia obie opcje.  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#3)]  
  
 Gdy używasz wnioskowanie o typie typu tablicy zależy od dominującą typu na liście wartości dostarczonym do literał tablicy. Typ dominującą jest unikatowy typu, na których wszystkie inne typy w tablicy poszerzyć literał. Nie można określić tego typu unikatowy, ten typ dominującej nie jest unikatowy typ, do której wszystkie typy w tablicy można ograniczyć. Jeśli żadna z tych typów unikatowy nie można ustalić, jest typu dominującą `Object`. Na przykład, jeśli lista wartości jest dostarczany do tablicy literału zawiera wartości typu `Integer`, `Long`, i `Double`, wynikowy tablicy jest typu `Double`. Zarówno `Integer` i `Long` poszerzyć tylko z `Double`. W związku z tym `Double` jest dominującą typu. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Te reguły wnioskowania stosuje się do typów, które są wywnioskowane dla tablic, które są zmienne lokalne, które są zdefiniowane w elemencie członkowskim klasy. Mimo że Literały tablicy można użyć podczas tworzenia klasy zmienne, nie można użyć wnioskowanie o typie na poziomie klasy. W związku z tym Literały tablicy, które są określone na poziomie klasy wywnioskować wartości, które są dostarczane na potrzeby literałów jako typ tablicy `Object`.  
  
 Można jawnie określić typ elementów w tablicy, która jest tworzona przy użyciu literał tablicy. W tym przypadku wartości w tablicy literału należy rozszerzyć na typ elementów tablicy. Poniższy przykład kodu tworzy tablicę typu `Double` z listy liczb całkowitych.  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#4)]  
  
###  <a name="BKMK_NestedArrayLiterals"></a>Tablica zagnieżdżona literałów  
 Przy użyciu literałów tablica zagnieżdżona można utworzyć tablicy wielowymiarowej. Tablica zagnieżdżona literałów muszą mieć wymiaru i liczby wymiarów lub rangi, która jest zgodna z tablicy wynikowej. Poniższy przykład kodu tworzy jest tablicą dwuwymiarową liczb całkowitych za pomocą literału tablicy.  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#7)]  
  
 W poprzednim przykładzie błąd może wystąpić, jeśli liczba elementów w literałach tablica zagnieżdżona nie były zgodne. Wystąpił błąd może również wystąpić, jeśli jawnie zadeklarować zmiennej tablicowej być inne niż dwuwymiarową.  
  
> [!NOTE]
>  Błędu można uniknąć, jeśli podasz literały tablica zagnieżdżona w różnych wymiarach umieszczając literały wewnętrzny tablicy w nawiasach. Nawiasy wymusić wyrażenie literału tablicy ma zostać obliczone, a wyniki są używane z zewnętrznym tablicowych, jak poniższy kod przedstawia.  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#11)]  
  
 Podczas tworzenia tablicy wielowymiarowej przy użyciu literałów tablica zagnieżdżona, można użyć wnioskowanie o typie. Gdy używasz wnioskowanie o typie wnioskowany typ jest typem dominującą wszystkie wartości w literałach tablicy dla poziomu zagnieżdżenia. Poniższy przykład kodu tworzy jest tablicą dwuwymiarową typu `Double` z wartości typu `Integer` i `Double`.  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#8)]  
  
 Aby uzyskać dodatkowe przykłady, zobacz [porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="BKMK_Iterating"></a>Iteracja przez tablicy  
 Podczas iteracji tablicy dostęp do każdego elementu w tablicy najniższym indeksie do najwyższej indeksu.  
  
 Poniższy przykład iteruje tablicą jednowymiarową przy użyciu [dla... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md). <xref:System.Array.GetUpperBound%2A> Metoda zwraca najwyższą wartość, która może mieć indeks. Najniższa wartość indeksu jest zawsze 0.  
  
 [!code-vb[VbVbalrArrays#41](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#41)]  
  
 Poniższy przykład iteruje tablicy wielowymiarowej przy użyciu `For...Next` instrukcji. <xref:System.Array.GetUpperBound%2A> Metoda ma parametr, który określa wymiar. `GetUpperBound(0)`Zwraca wartość indeksu wysokiej wymiar, i `GetUpperBound(1)` zwraca wartość indeksu wysokiej drugi wymiar.  
  
 [!code-vb[VbVbalrArrays#42](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#42)]  
  
 Poniższy przykład iteruje tablicą jednowymiarową przy użyciu [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 [!code-vb[VbVbalrArrays#43](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#43)]  
  
 Poniższy przykład iteruje tablicy wielowymiarowej przy użyciu `For Each...Next` instrukcji. Jednak masz większą kontrolę nad elementy tablicy wielowymiarowej użycie zagnieżdżoną `For…Next` instrukcji, jak w poprzednim przykładzie, zamiast `For Each…Next` instrukcji.  
  
 [!code-vb[VbVbalrArrays#44](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#44)]  
  
##  <a name="BKMK_ReturnValues"></a>Użycie tablic jako parametry i wartości zwracane  
 Aby zwracało tablicę z `Function` procedury, określ typ tablicy danych i liczby wymiarów jako typ zwracany [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md). W funkcji należy zadeklarować zmiennej lokalnej tablicy z tego samego typu danych i liczby wymiarów. W [zwracać instrukcji](../../../../visual-basic/language-reference/statements/return-statement.md), obejmują zmiennej lokalnej tablicy bez nawiasów.  
  
 Aby określić tablicę jako parametr `Sub` lub `Function` procedury, zdefiniuj dany parametr w postaci tablicy z określonego typu danych i liczby wymiarów. W wywołaniu procedury Wyślij zmiennej tablicowej z tego samego typu danych i liczby wymiarów.  
  
 W poniższym przykładzie `GetNumbers` funkcja zwraca `Integer()`. Ten typ tablicy jest Jednowymiarowa tablica typu `Integer`. `ShowNumbers` Akceptuje procedury `Integer()` argumentu.  
  
 [!code-vb[VbVbalrArrays#51](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#51)]  
  
 W poniższym przykładzie `GetNumbersMultiDim` funkcja zwraca `Integer(,)`. Ten typ tablicy jest dwóch wymiarów tablicy typu `Integer`.  `ShowNumbersMultiDim` Akceptuje procedury `Integer(,)` argumentu.  
  
 [!code-vb[VbVbalrArrays#52](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#52)]  
  
##  <a name="BKMK_JaggedArrays"></a>Tablice nieregularne  
 Tablica, która przechowuje tablic jako elementy nosi nazwę tablicy tablic lub tablicą nieregularną. A każdy element tablicy nieregularnej tablicy nieregularnej może mieć co najmniej jeden wymiar. Czasami struktury danych w aplikacji jest dwuwymiarowa, ale nie prostokątny.  
  
 W poniższym przykładzie przedstawiono tablicy miesięcy, każdy element jest tablicą dni. Ponieważ różne miesiące mają różną liczbę dni, elementy nie tworzą prostokątne tablicą dwuwymiarową. W związku z tym tablicy nieregularnej jest używany zamiast tablicy wielowymiarowej.  
  
 [!code-vb[VbVbalrArrays#21](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#21)]  
  
##  <a name="BKMK_ZeroLength"></a>Tablice o zerowej długości  
 Tablica, która nie zawiera żadnych elementów jest również nazywany tablicą o zerowej długości. Zmienna, która przechowuje tablicą o zerowej długości nie ma wartości `Nothing`. Do utworzenia tablicy, która nie ma żadnych elementów, należy zadeklarować jedną wymiary tablicy jako wartość -1, jak przedstawiono na poniższym przykładzie.  
  
 [!code-vb[VbVbalrArrays#14](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#14)]  
  
 Być może musisz utworzyć tablicą o zerowej długości w następujących okolicznościach:  
  
-   Bez ryzyka <xref:System.NullReferenceException> wyjątek, kod muszą uzyskać dostęp do elementów członkowskich <xref:System.Array> klas, takich jak <xref:System.Array.Length%2A> lub <xref:System.Array.Rank%2A>, lub zadzwoń [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] funkcji, takich jak <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Chcesz zachować odbierającą kodu prostszy, ponieważ nie ma do wyszukania `Nothing` w szczególnych przypadkach.  
  
-   Kod współdziała z interfejs programowania aplikacji (API), które musisz przekazać tablicą o zerowej długości do jednego lub więcej procedur lub zwraca tablicę o zerowej długości z jedną lub więcej procedur.  
  
##  <a name="BKMK_ArraySize"></a>Rozmiar tablicy  
 Rozmiar tablicy jest produktem długości jej wymiarów. Reprezentuje sumę elementów aktualnie znajdujących się w tablicy.  
  
 Poniższy przykład deklaruje jest tablicą trójwymiarową.  
  
```vb
Dim prices(3, 4, 5) As Long  
```  
  
 Całkowity rozmiar tablicy w zmiennej `prices` (3 + 1) x (4 + 1) x (5 + 1) = 120.  
  
 Rozmiar tablicy można znaleźć przy użyciu <xref:System.Array.Length%2A> właściwości. Długość każdego wymiaru tablicy wielowymiarowej można znaleźć przy użyciu <xref:System.Array.GetLength%2A> metody.  
  
 Możesz zmienić rozmiar zmienną tablicową przez przypisanie do niego nowy obiekt tablicy lub za pomocą `ReDim` instrukcji.  
  
 Istnieje kilka kwestii, które należy wziąć pod uwagę podczas pracy nad rozmiar tablicy.  
  
|||  
|---|---|  
|Długość wymiaru|Indeks każdego wymiaru jest oparty na 0, co oznacza, że z zakresu od 0, za pośrednictwem jego górnej granicy. W związku z tym długość danego wymiaru jest większa przez 1 niż górna granica zadeklarowana dla tego wymiaru.|  
|Limity długości|Długość każdego wymiaru tablicy jest ograniczona do maksymalnej wartości `Integer` typ danych, który jest (2 ^ 31) - 1. Całkowity rozmiar tablicy również jest jednak ograniczona przez pamięci w systemie. Jeśli podjęto próbę zainicjowania tablicy przekraczający ilość dostępnej pamięci RAM, zgłasza środowisko uruchomieniowe języka wspólnego <xref:System.OutOfMemoryException> wyjątku.|  
|Rozmiar i rozmiaru elementu|Rozmiar tablicy nie zależy od typu danych swoich elementów. Rozmiar zawsze stanowi całkowita liczba elementów, nie liczbę bajtów, które wykorzystują one w magazynie.|  
|Zużycie pamięci|Nie jest bezpieczne wszystkie założenia dotyczące sposobu tablicy jest przechowywany w pamięci. Dzięki tej samej tablicy można korzystać z większej ilości pamięci w 64-bitowym systemie niż w 32-bitowym systemie magazynu różni się na platformach szerokości innych danych. W zależności od konfiguracji systemu podczas inicjowania tablicy, środowisko uruchomieniowe języka wspólnego (CLR) można przypisać magazynu albo elementy pakietów, jak blisko siebie jak to możliwe, aby wyrównać je na granice fizyczne sprzętu. Ponadto tablicy wymaga magazynu narzut jego informacje o kontroli, a ten narzut zwiększa się wraz z każdego wymiaru dodany.|  
  
##  <a name="BKMK_ArrayTypes"></a>Typy tablicy i innych typów  
 Co tablica ma typ danych, ale różni się od typu danych swoich elementów. Nie ma typu danych dla wszystkich tablic. Zamiast tego typu danych tablicy zależy od liczby wymiarów, lub *rangę*z tablicy, a typ danych elementów w tablicy. Dwóch zmiennych tablicowych są uważane danych tego samego typu, tylko gdy mają one taką samą rangę, i ich elementy mają ten sam typ danych. Długości wymiary tablicy nie wpływają na dane typu tablicy.  
  
 Co tablica dziedziczy <xref:System.Array?displayProperty=nameWithType> klasy, a można zadeklarować zmiennej typu `Array`, ale nie można utworzyć tablicy typu `Array`. Ponadto [instrukcji ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md) nie może działać na zmienną zadeklarowany jako typ `Array`. Z tego względu i bezpieczeństwo typów, zaleca się deklarować co tablica jako określonego typu, takich jak `Integer` w poprzednim przykładzie.  
  
 Można ustalić typu danych tablicy lub jego elementów na kilka sposobów.  
  
-   Możesz wywołać <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w zmiennej <xref:System.Type> obiektu dla typu run-time zmiennej. <xref:System.Type> Obiekt zawiera szczegółowe informacje w jego właściwości i metody.  
  
-   Można przekazać zmiennej <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkcję odbierania `String` zawierającą nazwę typu run-time.  
  
-   Można przekazać zmiennej <xref:Microsoft.VisualBasic.Information.VarType%2A> funkcję odbierania `VariantType` wartość reprezentującą klasyfikację typu zmiennej.  
  
 Następujące przykładowe wywołania `TypeName` funkcji typu tablicy i typ elementów w tablicy. Typ tablicy jest `Integer(,)` i elementów w tablicy jest typu `Integer`.  
  
 [!code-vb[VbVbalrArrays#15](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#15)]  
  
##  <a name="BKMK_Collections"></a>Kolekcje alternatywą dla tablic  
 Tablice są najbardziej przydatne do tworzenia i Praca z stała liczba silnie typizowanych obiektów. Kolekcje umożliwiają bardziej elastyczne do pracy z grupy obiektów. W przeciwieństwie do tablic grupy obiektów, które współpracują z można zwiększyć lub zmniejszyć dynamicznie, musi mieć zmiany aplikacji.  
  
 Jeśli musisz zmienić rozmiar tablicy, należy użyć [instrukcji ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md). Gdy to zrobisz, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tworzy nową macierz i zwalnia poprzedniej tablicy do usunięcia. Trwa to czas wykonania. W związku z tym jeśli liczba elementów, które użytkownik pracuje z ulegają częstym zmianom, lub nie można przewidzieć maksymalną liczbę elementów, które są potrzebne, można uzyskać lepszą wydajność przy użyciu kolekcji.  
  
 Niektóre zbiory klucza można przypisać do wszystkich obiektów, które można umieścić w kolekcji, tak, aby szybko można pobrać obiektu przy użyciu klucza.  
  
 Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólnej kolekcji wymusza zabezpieczenie typów, dzięki czemu można dodać do niego inny typ danych. Podczas pobierania elementu z kolekcji uniwersalnej, nie trzeba określić jego typu danych albo przekonwertować go.  
  
 Aby uzyskać więcej informacji o kolekcjach, zobacz [kolekcji](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy ogólnej <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> można utworzyć kolekcję listy `Customer` obiektów.  
  
 [!code-vb[VbVbalrArrays#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#1)]  
  
 Deklaracja `CustomerFile` kolekcji Określa, że może zawierać tylko elementy typu `Customer`. Zapewnia także początkowej pojemności 200 elementów. Procedura `AddNewCustomer` sprawdza nowego elementu ważności i dodaje go do kolekcji. Procedura `PrintCustomers` używa `For Each` pętli do przechodzenia kolekcji i wyświetlić jego elementy.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Termin|Definicja|  
|----------|----------------|  
|[Wymiary tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Wyjaśniono rangę i wymiary tablic.|  
|[Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Opisuje sposób wypełnienia tablic o wartości początkowej.|  
|[Porady: Sortowanie tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Pokazuje sposób sortowania elementów tablicy alfabetycznie.|  
|[Porady: przypisywanie tablicy do innej tablicy](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Opisuje zasady i kroki przypisywanie tablicy do innej tablicy zmiennej.|  
|[Rozwiązywanie problemów z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|W tym artykule omówiono niektóre typowe problemy, które występują podczas pracy z tablicami.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array>  
 [Dim — instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim — instrukcja](../../../../visual-basic/language-reference/statements/redim-statement.md)
