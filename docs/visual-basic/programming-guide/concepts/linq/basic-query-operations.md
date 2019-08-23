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
ms.openlocfilehash: 12f10f30dd767f3435044f2bbebe0eb865c29d0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939368"
---
# <a name="basic-query-operations-visual-basic"></a>Podstawowe operacje zapytań (Visual Basic)
Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażeń w Visual Basic oraz do niektórych typowych rodzajów operacji wykonywanych w kwerendzie. Więcej informacji znajduje się w następujących tematach:  
  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Zapytania](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Przewodnik: Pisanie zapytań w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Określanie źródła danych (z)  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] W zapytaniu pierwszym krokiem jest określenie źródła danych, które ma zostać zbadane. W związku z `From` tym, klauzula w zapytaniu zawsze jest w pierwszej kolejności. Operatory zapytań zaznaczają i kształtują wynik w oparciu o typ źródła.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 Klauzula określa `customers`źródło danych, `cust`i *zmienną zakresu.* `From` Zmienna zakresu jest jak Zmienna iteracji pętli, z tą różnicą, że w wyrażeniu zapytania nie występuje rzeczywista iteracja. Gdy zapytanie jest wykonywane, często przy użyciu `For Each` pętli, zmienna zakresu służy jako odwołanie do każdego kolejnego elementu w. `customers` Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określać go jawnie. Aby zapoznać się z przykładami zapytań pisanych z i bez jawnego wpisywania, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Aby uzyskać więcej informacji na temat używania `From` klauzuli w Visual Basic, zobacz [klauzula FROM](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrowanie danych (gdzie)  
 Prawdopodobnie najbardziej typowa operacja zapytania stosuje filtr w postaci wyrażenia logicznego. Zapytanie zwraca następnie tylko te elementy, dla których wyrażenie ma wartość true. `Where` Klauzula służy do przeprowadzenia filtrowania. Filtr określa, które elementy w źródle danych mają być uwzględnione w wyniku sekwencji. W poniższym przykładzie uwzględniono tylko tych klientów, którzy mają adres w Londynie.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Operatory logiczne, takie jak `And` i, `Or` służą do `Where` łączenia wyrażeń filtru w klauzuli. Na przykład, aby zwrócić tylko tych klientów, którzy są z Londyn, których nazwa to Devon, użyj następującego kodu:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Aby zwrócić klientów z Londyn lub Paryż, użyj następującego kodu:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Aby uzyskać więcej informacji na temat używania `Where` klauzuli w Visual Basic, zobacz [klauzula WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Szeregowanie danych (porządkuj wg)  
 Często jest wygodne do sortowania zwracanych danych w określonej kolejności. `Order By` Klauzula spowoduje, że elementy w zwracanej sekwencji będą sortowane według określonego pola lub pola. Na przykład następujące zapytanie sortuje wyniki na podstawie `Name` właściwości. Ponieważ `Name` jest ciągiem, zwracane dane zostaną posortowane alfabetycznie, od a do z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Aby zamówić wyniki w odwrotnej kolejności, od z do A, użyj `Order By...Descending` klauzuli. Wartość domyślna to `Ascending` , gdy `Ascending` `Descending` nie jest ani określony.  
  
 Aby uzyskać więcej informacji na temat używania `Order By` klauzuli w Visual Basic, zobacz [klauzula Order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Wybieranie danych (wybór)  
 `Select` Klauzula określa formę i zawartość zwróconych elementów. Można na przykład określić, czy wyniki będą składać się z kompletnych `Customer` obiektów, tylko jednej `Customer` właściwości, podzestawu właściwości, kombinacji właściwości z różnych źródeł danych, czy pewnego nowego typu wyników na podstawie obliczeń. Gdy klauzula generuje coś innego niż kopia elementu źródłowego, operacja jest nazywana projekcją. `Select`  
  
 Aby pobrać kolekcję, która składa się `Customer` z kompletnych obiektów, wybierz samą zmienną zakresu:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Jeśli wystąpienie jest dużym obiektem, który ma wiele pól, a wszystkie, które chcesz pobrać, to nazwa, można wybrać `cust.Name`, jak pokazano w poniższym przykładzie. `Customer` Wnioskowanie typu lokalnego rozpoznaje, że ta zmiana typu wyniku z kolekcji `Customer` obiektów do kolekcji ciągów.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:  
  
- `Select` W klauzuli należy określić pola, które mają zostać uwzględnione w wyniku. Kompilator określi typ anonimowy, który ma te pola jako właściwości. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Ponieważ zwracane elementy w poniższym przykładzie są wystąpieniami typu anonimowego, nie można odwołać się do typu według nazwy w innym miejscu w kodzie. Nazwa oznaczona przez kompilator dla typu zawiera znaki, które nie są prawidłowe w normalnym Visual Basic kodzie. W poniższym przykładzie elementy w kolekcji, które są zwracane przez zapytanie w `londonCusts4` , są wystąpieniami typu anonimowego  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     —lub—  
  
- Zdefiniuj nazwany typ, który zawiera określone pola, które chcesz dołączyć do wyniku, i Utwórz i zainicjuj wystąpienia typu w `Select` klauzuli. Użyj tej opcji tylko wtedy, gdy musisz użyć pojedynczych wyników poza kolekcją, w której są zwracane, lub jeśli musisz przekazać je jako parametry w wywołaniach metod. Typ `londonCusts5` w poniższym przykładzie to IEnumerable (of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Aby uzyskać więcej informacji na temat używania `Select` klauzuli w Visual Basic, zobacz SELECT — [klauzula](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Przyłączanie danych (łączenie i łączenie grupy)  
 Więcej niż jedno źródło danych w `From` klauzuli można połączyć na kilka sposobów. Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu nich w wyniku. Zapytanie wybiera uczniów, których nazwiska zaczynają się od samogłosek.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Ten kod można uruchomić z listą uczniów utworzonych w [temacie How to: Utwórz listę elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Słowo kluczowe jest odpowiednikiem `INNER JOIN` w SQL. `Join` Łączy dwie kolekcje na podstawie pasujących wartości klucza między elementami w dwóch kolekcjach. Zapytanie zwraca wszystkie lub część elementów kolekcji, które mają zgodne wartości klucza. Na przykład poniższy kod duplikuje akcję poprzedniego niejawnego sprzężenia.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`łączy kolekcje w jedną hierarchiczną kolekcję, podobnie jak w `LEFT JOIN` przypadku języka SQL. Aby uzyskać więcej informacji, zobacz Klauzula [Join](../../../../visual-basic/language-reference/queries/join-clause.md) i [Klauzula join Group](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Grupowanie danych (grupuj według)  
 Można dodać `Group By` klauzulę, aby zgrupować elementy w wyniku zapytania zgodnie z co najmniej jednym polem elementów. Na przykład poniższy kod grupuje uczniów według klasy Year.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Jeśli uruchamiasz ten kod przy użyciu listy uczniów utworzonych w [temacie How to: Utwórz listę elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), dane wyjściowe `For Each` instrukcji to:  
  
 Czteroletniego Młodsz  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Czteroletniego Wyższy  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Czteroletniego Nowy  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 Wariant przedstawiony w poniższym kodzie porządkuje lata klasy, a następnie porządkuje uczniów w każdym roku według nazwiska.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Aby uzyskać więcej informacji `Group By`na temat, zobacz [klauzula GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.IEnumerable%601>
- [Wprowadzenie ze składnikami LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
