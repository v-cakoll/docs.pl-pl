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
ms.openlocfilehash: b9216dba23f49e4d9fd99687e38f5c13addde8fb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636877"
---
# <a name="basic-query-operations-visual-basic"></a>Podstawowe operacje zapytań (Visual Basic)
Ten temat zawiera krótkie wprowadzenie do wyrażeń programu Query-Integrated Language (LINQ) w Visual Basic oraz do niektórych typowych rodzajów operacji wykonywanych w zapytaniu. Więcej informacji znajduje się w następujących tematach:  
  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Zapytania](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Przewodnik: Pisanie zapytań w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Określanie źródła danych (z)  
 W zapytaniu LINQ pierwszy krok to określenie źródła danych, które chcesz zbadać. W związku z tym, klauzula `From` w zapytaniu zawsze jest w pierwszej kolejności. Operatory zapytań zaznaczają i kształtują wynik w oparciu o typ źródła.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 Klauzula `From` określa źródło danych, `customers`i *zmienną zakresu*, `cust`. Zmienna zakresu jest jak Zmienna iteracji pętli, z tą różnicą, że w wyrażeniu zapytania nie występuje rzeczywista iteracja. Gdy zapytanie jest wykonywane, często przy użyciu pętli `For Each`, zmienna zakresu służy jako odwołanie do każdego kolejnego elementu w `customers`. Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określać go jawnie. Aby zapoznać się z przykładami zapytań pisanych z i bez jawnego wpisywania, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Aby uzyskać więcej informacji na temat używania klauzuli `From` w Visual Basic, zobacz [klauzula FROM](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrowanie danych (gdzie)  
 Prawdopodobnie najbardziej typowa operacja zapytania stosuje filtr w postaci wyrażenia logicznego. Zapytanie zwraca następnie tylko te elementy, dla których wyrażenie ma wartość true. Klauzula `Where` jest używana do przeprowadzenia filtrowania. Filtr określa, które elementy w źródle danych mają być uwzględnione w wyniku sekwencji. W poniższym przykładzie uwzględniono tylko tych klientów, którzy mają adres w Londynie.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Operatory logiczne, takie jak `And` i `Or`, służą do łączenia wyrażeń filtru w klauzuli `Where`. Na przykład, aby zwrócić tylko tych klientów, którzy są z Londyn, których nazwa to Devon, użyj następującego kodu:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Aby zwrócić klientów z Londyn lub Paryż, użyj następującego kodu:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Aby uzyskać więcej informacji na temat używania klauzuli `Where` w Visual Basic, zobacz [klauzula WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Szeregowanie danych (porządkuj wg)  
 Często jest wygodne do sortowania zwracanych danych w określonej kolejności. Klauzula `Order By` powoduje, że elementy w zwracanej sekwencji będą sortowane według określonego pola lub pola. Na przykład następujące zapytanie sortuje wyniki na podstawie właściwości `Name`. Ponieważ `Name` jest ciągiem, zwracane dane zostaną posortowane alfabetycznie, od A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Aby zamówić wyniki w odwrotnej kolejności, od z do A, użyj klauzuli `Order By...Descending`. Wartość domyślna to `Ascending`, gdy nie `Ascending` ani `Descending` nie została określona.  
  
 Aby uzyskać więcej informacji na temat używania klauzuli `Order By` w Visual Basic, zobacz [klauzula Order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Wybieranie danych (wybór)  
 Klauzula `Select` określa formę i zawartość zwróconych elementów. Można na przykład określić, czy wyniki będą składać się z kompletnych `Customer` obiektów, tylko jednej `Customer` właściwości, podzestawu właściwości, kombinacji właściwości z różnych źródeł danych, czy też nowego typu wyników na podstawie obliczeń. Gdy klauzula `Select` generuje coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcją*.  
  
 Aby pobrać kolekcję, która składa się z kompletnych obiektów `Customer`, wybierz zmienną zakresu:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Jeśli wystąpienie `Customer` jest dużym obiektem, który ma wiele pól, a wszystkie elementy, które chcesz pobrać, są nazwami, możesz wybrać `cust.Name`, jak pokazano w poniższym przykładzie. Wnioskowanie typu lokalnego rozpoznaje, że ta zmiana typu wyniku z kolekcji obiektów `Customer` do kolekcji ciągów.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:  
  
- W klauzuli `Select` Określ pola, które mają zostać uwzględnione w wyniku. Kompilator określi typ anonimowy, który ma te pola jako właściwości. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Ponieważ zwracane elementy w poniższym przykładzie są wystąpieniami typu anonimowego, nie można odwołać się do typu według nazwy w innym miejscu w kodzie. Nazwa oznaczona przez kompilator dla typu zawiera znaki, które nie są prawidłowe w normalnym Visual Basic kodzie. W poniższym przykładzie elementy w kolekcji, które są zwracane przez zapytanie w `londonCusts4` są wystąpieniami typu anonimowego  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     lub  
  
- Zdefiniuj nazwany typ, który zawiera określone pola, które chcesz dołączyć do wyniku, i Utwórz i zainicjuj wystąpienia typu w klauzuli `Select`. Użyj tej opcji tylko wtedy, gdy musisz użyć pojedynczych wyników poza kolekcją, w której są zwracane, lub jeśli musisz przekazać je jako parametry w wywołaniach metod. Typ `londonCusts5` w poniższym przykładzie to IEnumerable (of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Aby uzyskać więcej informacji na temat używania klauzuli `Select` w Visual Basic, zobacz [SELECT — klauzula](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Przyłączanie danych (łączenie i łączenie grupy)  
 Można połączyć więcej niż jedno źródło danych w klauzuli `From` na kilka sposobów. Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu nich w wyniku. Zapytanie wybiera uczniów, których nazwiska zaczynają się od samogłosek.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Ten kod można uruchomić z listą uczniów utworzonych w temacie [How to: Create a list of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Słowo kluczowe `Join` jest odpowiednikiem `INNER JOIN` w SQL. Łączy dwie kolekcje na podstawie pasujących wartości klucza między elementami w dwóch kolekcjach. Zapytanie zwraca wszystkie lub część elementów kolekcji, które mają zgodne wartości klucza. Na przykład poniższy kod duplikuje akcję poprzedniego niejawnego sprzężenia.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` łączy kolekcje w jedną hierarchiczną kolekcję, podobnie jak `LEFT JOIN` w języku SQL. Aby uzyskać więcej informacji, zobacz Klauzula [Join](../../../../visual-basic/language-reference/queries/join-clause.md) i [Klauzula join Group](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Grupowanie danych (grupuj według)  
 Można dodać klauzulę `Group By`, aby zgrupować elementy w wyniku zapytania zgodnie z co najmniej jednym polem elementów. Na przykład poniższy kod grupuje uczniów według klasy Year.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Jeśli uruchomisz ten kod przy użyciu listy uczniów utworzonych w [instrukcje: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), dane wyjściowe instrukcji `For Each` są następujące:  
  
 Year: młodszy  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Rok: starszy  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Year: odświeżacz  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 Wariant przedstawiony w poniższym kodzie porządkuje lata klasy, a następnie porządkuje uczniów w każdym roku według nazwiska.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Aby uzyskać więcej informacji na temat `Group By`, zobacz [klauzula GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.IEnumerable%601>
- [Wprowadzenie ze składnikami LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
