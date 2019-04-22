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
ms.openlocfilehash: ed5ed56366911c3676c4413711207ac0a8f85765
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826200"
---
# <a name="basic-query-operations-visual-basic"></a>Podstawowe operacje zapytań (Visual Basic)
Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażenia w języku Visual Basic i niektóre typowe rodzaje operacji, które można wykonywać w zapytaniu. Więcej informacji znajduje się w następujących tematach:  
  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Zapytania](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Przewodnik: Pisanie zapytań w języku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Określanie źródła danych (z)  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, pierwszym krokiem jest określenie źródła danych, które chcesz zbadać. W związku z tym `From` podklauzul zawsze wykorzystasz. Operatory zapytań wybierz i kształtów wyników na podstawie typu źródła.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From` Klauzula Określa źródło danych `customers`, a *zmiennej zakresu*, `cust`. Zmienna zakresu przypomina Zmienna iteracji pętli, z tą różnicą, że w wyrażeniu zapytania wystąpi nie rzeczywiste iteracji. Jeśli zapytanie jest wykonywane, często za pomocą `For Each` pętli, zmienna zakresu służy jako punkt odniesienia, aby każdy element w `customers`. Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określić ręcznie. Przykłady zapytań napisane i bez jawnych typowań, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Aby uzyskać więcej informacji o sposobie używania `From` klauzuli w języku Visual Basic, zobacz [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrowanie danych (gdzie)  
 Prawdopodobnie najbardziej typowych operacji zapytania jest stosowanie filtru w postaci wyrażenia logicznego. Zapytanie jest następnie zwraca tylko te elementy, dla których wyrażenie jest prawdziwe. Element `Where` jest używana do wykonywania filtrowania. Filtr określa, które elementy w źródle danych, które mają zostać objęte wynikowa sekwencja. W poniższym przykładzie dołączono tych klientów, którzy mają adres w Londynie.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Można użyć operatorów logicznych, takich jak `And` i `Or` połączyć wyrażenia filtru w `Where` klauzuli. Na przykład aby zwrócić tylko tych klientów, którzy są z Londynu, i której nazwa to Devon, należy użyć następującego kodu:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Aby zwrócić klienci z Londynu lub Paryż, użyj następującego kodu:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Aby uzyskać więcej informacji o sposobie używania `Where` klauzuli w języku Visual Basic, zobacz [klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Szeregowanie danych (porządkuj wg)  
 Często jest wygodne posortować dane zwrócone w określonej kolejności. `Order By` Klauzuli spowoduje, że elementy w zwracanej sekwencji sortowania na określone pole lub pola. Na przykład poniższe zapytanie sortuje wyniki na podstawie `Name` właściwości. Ponieważ `Name` jest ciągiem, zwrócone dane zostaną posortowane alfabetycznie, od A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Aby uporządkować wyniki w odwrotnej kolejności od Z do A, należy użyć `Order By...Descending` klauzuli. Wartość domyślna to `Ascending` podczas ani `Ascending` ani `Descending` jest określony.  
  
 Aby uzyskać więcej informacji o sposobie używania `Order By` klauzuli w języku Visual Basic, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Wybieranie danych (wybór)  
 `Select` Klauzula określa formularza i zawartości zwróconych elementów. Na przykład można określić, czy wyniki będą zawierać pełną `Customer` obiektów, co najmniej jeden `Customer` właściwości, podzbiór właściwości, kombinacja właściwości z różnych źródeł danych lub nowego typu wyniku w oparciu o obliczenie. Gdy `Select` klauzuli tworzy coś innego niż kopię elementu źródłowego, operacja jest nazywana *projekcji*.  
  
 Aby pobrać kolekcję, która składa się z pełną `Customer` obiektów, zaznacz sama zmienna zakresu:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Jeśli `Customer` wystąpienie jest dużego obiektu, który ma wiele pól i wszystkie opcje, które mają zostać pobrane to nazwa, możesz wybrać `cust.Name`, jak pokazano w poniższym przykładzie. Wnioskowanie o typie lokalnym rozpoznaje, spowoduje to zmianę typu wyniku z kolekcji `Customer` obiekty kolekcji ciągów.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:  
  
-   W `Select` klauzuli, określ pola, które chcesz uwzględnić w wyniku. Kompilator określi typ anonimowy, który ma te pola z jego właściwości. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Ponieważ zwróconych elementów w poniższym przykładzie są wystąpieniami typu anonimowego, nie możesz odwołać się do typu według nazwy innym miejscu w kodzie. Nazwy wyznaczony przez kompilator typu zawiera znaki, które nie są dozwolone w normalnym kodu języka Visual Basic. W poniższym przykładzie elementów w kolekcji, który jest zwracany przez zapytanie w `londonCusts4` są wystąpieniami typu anonimowego  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     —lub—  
  
-   Definiowanie typu nazwanego, który zawiera określonego pola, które chcesz uwzględnić w wyniku i tworzenie i Inicjowanie wystąpienia typu w `Select` klauzuli. Użyj tej opcji tylko wtedy, gdy trzeba użyć poszczególnych wyników spoza kolekcji, w której są zwracane, lub jeśli trzeba przekazać je jako parametry w wywołaniach metod. Typ `londonCusts5` w poniższym przykładzie jest IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Aby uzyskać więcej informacji o sposobie używania `Select` klauzuli w języku Visual Basic, zobacz [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Przyłączanie danych (łączenie i łączenie grupy)  
 Można połączyć więcej niż jednego źródła danych w `From` klauzuli na kilka sposobów. Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu z nich w wyniku. Zapytanie wybiera studentów, w których nazwiska rozpoczynać się od samogłosek.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  Ten kod można uruchomić za pomocą listy studentów utworzone w [jak: Utwórz listę elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 `Join` — Słowo kluczowe jest odpowiednikiem `INNER JOIN` w języku SQL. Łączy dwie kolekcje na podstawie dopasowania wartości kluczy między elementami w dwóch kolekcjach. Zapytanie zwraca całości lub części elementów kolekcji, które pasują do wartości klucza. Na przykład poniższy kod duplikuje Akcja poprzedniego łączenia niejawnego.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` Podobnie jak łączy kolekcje w jedną hierarchiczną kolekcję `LEFT JOIN` w języku SQL. Aby uzyskać więcej informacji, zobacz [klauzuli Join](../../../../visual-basic/language-reference/queries/join-clause.md) i [Group Join — klauzula](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Grupowanie danych (grupuj według)  
 Możesz dodać `Group By` klauzuli do grupowania elementów w wyniku zapytania zgodnie z co najmniej jednego pola elementów. Na przykład poniższy kod grupy uczniów według klasy, roku.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Jeśli można uruchomić ten kod przy użyciu listy studentów utworzone w [jak: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), dane wyjściowe z `For Each` instrukcja jest:  
  
 Rok: Inny poziom  
  
 Tucker, Michael  
  
 Garcia-Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Rok: Starszy  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 We Feng, Hanying  
  
 Adams, Terry  
  
 Rok: IV rok  
  
 Mortensen, Sven  
  
 Garcia-Cesarowi  
  
 Odmiany pokazano w poniższym kodzie porządkuje lat klasy, a następnie porządkuje według nazwiska uczniów w każdym roku.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Aby uzyskać więcej informacji na temat `Group By`, zobacz [grupy przez klauzulę](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.IEnumerable%601>
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
