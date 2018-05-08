---
title: Podstawowe operacje zapytań (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 5587a60e97464324659b325e38a18ac25488d30d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="basic-query-operations-visual-basic"></a>Podstawowe operacje zapytań (Visual Basic)
Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażenia w Visual Basic i niektórych typowych rodzajów operacji wykonywanych w zapytaniu. Więcej informacji znajduje się w następujących tematach:  
  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [Wskazówki: Pisanie zapytań w języku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Określanie źródła danych (z)  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, pierwszym krokiem jest określenie źródła danych, które chcesz zbadać. W związku z tym `From` podklauzul zawsze zostanie osiągnięty jako pierwszy. Operatory zapytań wybierz i kształt wyniku na podstawie typu źródła.  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 `From` Klauzuli Określa źródło danych, `customers`, a *zmiennej zakresu*, `cust`. Zmienna zakresu przypomina zmiennej iteracji pętli, z wyjątkiem tego, że w wyrażeniu zapytania nie rzeczywiste iteracji występuje. Podczas wykonywania zapytania, często przy użyciu `For Each` pętli, zmienna zakresu służy jako punkt odniesienia, aby każdy element w `customers`. Ponieważ kompilator można wywnioskować typu elementu `cust`, nie trzeba określić ręcznie. Przykłady zapytań zapisywane z i bez wprowadzania jawne, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Aby uzyskać więcej informacji o sposobie używania `From` klauzuli w języku Visual Basic, zobacz [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrowanie danych (gdzie)  
 Prawdopodobnie najbardziej typowych operacji zapytania jest stosowanie filtru w postaci wyrażenia logicznego. Następnie zapytanie zwraca tylko te elementy, dla których wyrażenie jest prawdziwe. A `Where` jest używana do wykonywania filtrowania. Filtr określa elementy, które w źródle danych, aby uwzględnić w wynikowa sekwencja. W poniższym przykładzie zawarte są tylko klientów, którzy mają adres w Londynie.  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 Można użyć operatorów logicznych, takich jak `And` i `Or` do filtru wyrażeń w `Where` klauzuli. Na przykład aby przywrócić tylko tych klientów, którzy są w Londynie i której nazwa jest Devon, należy użyć poniższego kodu:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Aby przywrócić klientów w Londynie lub Paryża, należy użyć poniższego kodu:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Aby uzyskać więcej informacji o sposobie używania `Where` klauzuli w języku Visual Basic, zobacz [klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Szeregowanie danych (porządkuj wg)  
 Często jest wygodne posortuj zwrócone dane w określonej kolejności. `Order By` Klauzuli spowoduje, że elementy w sekwencji zwróconego można sortować według określonego pola lub pól. Na przykład poniższe zapytanie sortujące wyniki na podstawie `Name` właściwości. Ponieważ `Name` ciągiem i zwrócone dane są sortowane alfabetycznie, od A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Aby w odwrotnej kolejności kolejność wyników z malejąco, należy użyć `Order By...Descending` klauzuli. Wartość domyślna to `Ascending` podczas ani `Ascending` ani `Descending` jest określona.  
  
 Aby uzyskać więcej informacji o sposobie używania `Order By` klauzuli w języku Visual Basic, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Wybieranie danych (wybór)  
 `Select` Klauzuli określa formularza i zawartości zwracane elementy. Na przykład można określić, czy wyniki będzie składać się z pełną `Customer` obiektów, co najmniej jeden `Customer` właściwości, podzbiór właściwości, kombinację właściwości z różnych źródeł danych lub nowego typu wyniku w oparciu o obliczenie. Gdy `Select` klauzuli powoduje inną niż kopię elementu źródła, operacja jest wywoływana *projekcji*.  
  
 Aby pobrać kolekcję, która składa się z pełną `Customer` obiektów, zaznacz samej zmiennej zakresu:  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 Jeśli `Customer` wystąpienie jest dużego obiektu, który ma wiele pól i wszystkie punkty, które ma zostać pobrane to nazwa, możesz wybrać `cust.Name`, jak pokazano w poniższym przykładzie. Wnioskowanie o typie lokalnym rozpoznaje, spowoduje to zmianę typu wyników z kolekcji `Customer` obiekty do kolekcji ciągów.  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:  
  
-   W `Select` klauzuli, określ pola, które mają zostać uwzględnione w wynikach. Kompilator będzie zdefiniować typu anonimowego, który ma te pola z jego właściwości. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Zwracane elementy w poniższym przykładzie są wystąpienia typu anonimowego, użytkownik nie może odwoływać się do typu według nazwy w innym miejscu w kodzie. Nazwa wyznaczony przez kompilator typu zawiera znaki, które nie są dozwolone w normalnym kod Visual Basic. W poniższym przykładzie elementów w kolekcji zwracane przez zapytanie w `londonCusts4` wystąpień typu anonimowego  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     —lub—  
  
-   Zdefiniuj typ nazwany, zawierający określonego pola, które mają być zawarte w wyniku, tworzenie i Inicjowanie wystąpień typu w `Select` klauzuli. Użyj tej opcji tylko wtedy, gdy należy użyć poszczególnych wyników poza kolekcji, w której są zwracane lub jeśli zajdzie potrzeba przekazywane jako parametry w wywołaniach metody. Typ `londonCusts5` w poniższym przykładzie jest IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Aby uzyskać więcej informacji o sposobie używania `Select` klauzuli w języku Visual Basic, zobacz [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Przyłączanie danych (łączenie i łączenie grupy)  
 Możesz łączyć więcej niż jedno źródło danych w `From` klauzuli na kilka sposobów. Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu z nich w wyniku. Zapytanie wybiera studentów, których ostatniego nazwy rozpoczynają się od samogłosek.  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  Można uruchomić ten kod z listy studentów utworzone w [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 `Join` — Słowo kluczowe jest odpowiednikiem `INNER JOIN` w języku SQL. Łączy dwie kolekcje oparte na pasujących wartości klucza między elementami w dwie kolekcje. Zapytanie zwraca całość lub część elementy kolekcji, które pasują do wartości klucza. Na przykład następujący kod stanowi duplikat Akcja poprzedniego niejawne sprzężenia.  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` łączy kolekcji do pojedynczego hierarchiczną kolekcję, tak jak `LEFT JOIN` w języku SQL. Aby uzyskać więcej informacji, zobacz [klauzuli Join](../../../../visual-basic/language-reference/queries/join-clause.md) i [klauzuli Join grupy](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Grupowanie danych (grupuj według)  
 Możesz dodać `Group By` klauzuli grupować elementy znajdujące się w wyniku zapytania, zgodnie z polami co najmniej jeden z elementów. Na przykład następujący kod grupy studentów przez rok klasy.  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 Jeśli możesz uruchomić ten kod przy użyciu listy studentów utworzone w [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), dane wyjściowe z `For Each` instrukcja jest:  
  
 Rok: inny poziom  
  
 Tucker, Michael  
  
 Kowalski, Hugo  
  
 Kowalski, Magdalena  
  
 Tucker, Lance  
  
 Rok: starszy  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Pracownicy, Terry  
  
 Rok: IV rok  
  
 Rolecki, Tadeusz  
  
 Kowalski, Cesarowi  
  
 Zmiana pokazano w poniższym kodzie porządkuje lat klasy, a następnie zamówienia studentów w ramach co roku przez nazwisko.  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 Aby uzyskać więcej informacji na temat `Group By`, zobacz [grupy przez klauzuli](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Wprowadzenie do korzystania z LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
