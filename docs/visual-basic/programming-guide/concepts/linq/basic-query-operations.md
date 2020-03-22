---
title: Podstawowe operacje zapytań
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
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266381"
---
# <a name="basic-query-operations-visual-basic"></a>Podstawowe operacje zapytań (Visual Basic)
Ten temat zawiera krótkie wprowadzenie do wyrażeń linq (Language-Integrated Query) w języku Visual Basic i niektórych typowych rodzajów operacji, które można wykonać w kwerendzie. Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Zapytania](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Wskazówki: Pisanie zapytań w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Określanie źródła danych (z)  
 W kwerendzie LINQ pierwszym krokiem jest określenie źródła danych, które chcesz zbadać. W związku `From` z tym klauzuli w kwerendzie zawsze jest na pierwszym miejscu. Operatorzy kwerend zaznaczają i kształtują wynik na podstawie typu źródła.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 Klauzula `From` określa źródło danych `customers`i *zmienną* `cust`zakresu , . Zmienna zakresu jest jak zmienna iteracji pętli, z tą różnicą, że w wyrażeniu kwerendy nie występuje żadna rzeczywista iteracja. Gdy kwerenda jest wykonywana, `For Each` często przy użyciu pętli, zmienna zakresu `customers`służy jako odwołanie do każdego kolejnego elementu w . Ponieważ kompilator można wywnioskować typ `cust`, nie trzeba go jawnie określić. Aby zapoznać się z przykładami zapytań napisanych z jawnym wpisaniem i bez niego, zobacz [Relacje typów w operacjach kwerend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Aby uzyskać więcej informacji `From` na temat używania klauzuli w języku Visual Basic, zobacz [Od klauzuli](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrowanie danych (gdzie)  
 Prawdopodobnie najczęstszą operacją kwerendy jest zastosowanie filtru w postaci wyrażenia logicznego. Następnie kwerenda zwraca tylko te elementy, dla których wyrażenie jest prawdziwe. Klauzula `Where` jest używana do wykonywania filtrowania. Filtr określa, które elementy w źródle danych mają być uwzględniane w wynikowej sekwencji. W poniższym przykładzie uwzględniono tylko tych klientów, którzy mają adres w Londynie.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Operatory logiczne, `And` takie `Or` jak i do `Where` łączenia wyrażeń filtru w klauzuli. Na przykład, aby zwrócić tylko tych klientów, którzy są z Londynu i których nazwa jest Devon, należy użyć następującego kodu:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 Aby zwrócić klientów z Londynu lub Paryża, użyj następującego kodu:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Aby uzyskać więcej informacji `Where` na temat używania klauzuli w języku Visual Basic, zobacz [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Szeregowanie danych (porządkuj wg)  
 Często jest to wygodne do sortowania zwróconych danych w określonej kolejności. Klauzula `Order By` spowoduje, że elementy w zwróconej sekwencji mają być sortowane na określonym polu lub polach. Na przykład następujące zapytanie sortuje `Name` wyniki na podstawie właściwości. Ponieważ `Name` jest ciągiem, zwrócone dane zostaną posortowane alfabetycznie, od A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Aby zamówić wyniki w odwrotnej kolejności, `Order By...Descending` od Z do A, należy użyć klauzuli. Wartość domyślna `Ascending` jest `Ascending` `Descending` wtedy, gdy ani nie jest określony.  
  
 Aby uzyskać więcej informacji `Order By` na temat używania klauzuli w języku Visual Basic, zobacz [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Wybieranie danych (wybór)  
 Klauzula `Select` określa formę i zawartość zwróconych elementów. Na przykład można określić, czy wyniki `Customer` będą składać `Customer` się z kompletnych obiektów, tylko jedna właściwość, podzbiór właściwości, kombinacja właściwości z różnych źródeł danych lub jakiś nowy typ wyniku na podstawie obliczeń. Gdy `Select` klauzula tworzy coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcji*.  
  
 Aby pobrać kolekcję, która `Customer` składa się z kompletnych obiektów, wybierz samą zmienną zakresu:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Jeśli `Customer` wystąpienie jest dużym obiektem, który ma wiele pól, a wszystko, `cust.Name`co chcesz pobrać, to nazwa, można wybrać , jak pokazano w poniższym przykładzie. Wnioskowanie o typie lokalnym rozpoznaje, że `Customer` zmienia to typ wyniku z kolekcji obiektów na kolekcję ciągów.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:  
  
- W `Select` klauzuli określ pola, które mają zostać uwzględnione w wyniku. Kompilator zdefiniuje typ anonimowy, który ma te pola jako jego właściwości. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Ponieważ zwrócone elementy w poniższym przykładzie są wystąpienia typu anonimowego, nie można odwoływać się do typu według nazwy w innym miejscu w kodzie. Nazwa wyznaczona przez kompilator dla tego typu zawiera znaki, które nie są prawidłowe w normalnym kodzie języka Visual Basic. W poniższym przykładzie elementy w kolekcji, która `londonCusts4` jest zwracana przez kwerendę w są wystąpienia typu anonimowego  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     — lub —  
  
- Zdefiniuj nazwany typ, który zawiera określone pola, które chcesz uwzględnić w wyniku, i utwórz i zainicjalizuj wystąpienia typu w klauzuli. `Select` Tej opcji należy używać tylko wtedy, gdy trzeba użyć poszczególnych wyników poza kolekcji, w którym są zwracane lub jeśli trzeba przekazać je jako parametry w wywołania metody. Typ w `londonCusts5` poniższym przykładzie jest IEnumerable(NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Aby uzyskać więcej informacji `Select` na temat używania klauzuli w języku Visual Basic, zobacz [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Przyłączanie danych (łączenie i łączenie grupy)  
 Można połączyć więcej niż jedno `From` źródło danych w klauzuli na kilka sposobów. Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu z nich w wyniku. Kwerenda wybiera uczniów, których nazwiska zaczynają się od samogłoski.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Możesz uruchomić ten kod z listą uczniów utworzonych w [jak: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Słowo `Join` kluczowe jest `INNER JOIN` równoważne w sql. Łączy dwie kolekcje na podstawie dopasowania wartości klucza między elementami w dwóch kolekcjach. Kwerenda zwraca wszystkie lub część elementów kolekcji, które mają pasujące wartości klucza. Na przykład poniższy kod powiela akcję poprzedniego sprzężenia niejawnego.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`łączy kolekcje w jedną kolekcję hierarchiczną, podobnie jak `LEFT JOIN` w języku SQL. Aby uzyskać więcej informacji, zobacz [Klauzula dołączania](../../../../visual-basic/language-reference/queries/join-clause.md) i [klauzula dołączania do grupy](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Grupowanie danych (grupuj według)  
 Można dodać `Group By` klauzulę do grupy elementów w wyniku kwerendy zgodnie z jednym lub więcej pól elementów. Na przykład następujący kod grupuje uczniów według roku zajęć.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Jeśli uruchomisz ten kod przy użyciu listy studentów utworzonych w [Jak: Tworzenie listy elementów,](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)dane wyjściowe z `For Each` instrukcji jest:  
  
 Rok: Junior  
  
 Tucker, Michał  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Rok: Senior  
  
 Omelczenko, Swietłana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Rok: Freshman  
  
 Mortensen  
  
 Garcia, Cesar  
  
 Zmiana przedstawiona w poniższym kodzie zamówi lata zajęć, a następnie zamawia uczniów w ciągu każdego roku po imieniu.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Aby uzyskać `Group By`więcej informacji na temat , zobacz [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic.IEnumerable%601>
- [Wprowadzenie do programu LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [Omówienie standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Linq](../../../../visual-basic/programming-guide/language-features/linq/index.md)
