---
title: 'Instrukcje: Łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 66255a9bfa2a4f9acb33073bae755efbab61042e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977989"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Instrukcje: Łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)
Visual Basic oferuje `Join` i `Group Join` klauzul, aby umożliwić łączenie zawartości wielu kolekcji na podstawie wartości typowych między kolekcjami zapytania. Wartości te są znane jako *klucz* wartości. Deweloperzy znasz koncepcji relacyjnych baz danych będzie także rozpoznawał `Join` klauzuli jako INNER JOIN i `Group Join` klauzuli jako skutecznie, z LEFT OUTER JOIN.  
  
 W przykładach w tym temacie pokazano kilka sposobów na łączenie danych za pomocą `Join` i `Group Join` klauzul zapytania.  
  
## <a name="create-a-project-and-add-sample-data"></a>Tworzenie projektu i Dodawanie przykładowych danych  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Aby utworzyć projekt, który zawiera przykładowe dane i typy  
  
1.  Aby uruchomić przykłady w tym temacie, Otwórz program Visual Studio i Dodaj nowy projekt aplikacji konsoli Visual Basic. Kliknij dwukrotnie plik Module1.vb utworzone przez program Visual Basic.  
  
2.  Przykłady w tym temacie `Person` i `Pet` typów i danych w poniższym przykładzie kodu. Skopiuj ten kod jest to domyślna `Module1` modułu utworzony przez program Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Wykonania sprzężenia wewnętrznego przy użyciu klauzuli Join  
 INNER JOIN łączy dane z dwóch kolekcji. Elementy, dla których odpowiada określonej wartości klucza są uwzględniane. Wszystkie elementy z kolekcji lub kolekcji, które nie mają pasujący element w innej kolekcji są wyłączone.  
  
 W języku Visual Basic LINQ oferuje dwie opcje umożliwiające wykonywanie sprzężenia wewnętrznego: sprzężenie niejawne i jawne sprzężenia.  
  
 Sprzężenie niejawne Określa, kolekcji, który ma zostać umieszczony `From` klauzuli i identyfikuje dopasowania pól klucza w `Where` klauzuli. Visual Basic niejawnie łączy dwie kolekcje, w oparciu o określone pola klucza.  
  
 Należy określić jawnego łączenia za pomocą `Join` klauzuli, gdy użytkownik chce konkretnym pola, który klucz do użycia w sprzężeniu. W tym przypadku `Where` klauzuli nadal może służyć do filtrowania wyników zapytania.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Aby wykonać Inner Join przy użyciu klauzuli Join  
  
1.  Dodaj następujący kod do `Module1` modułu w projekcie, aby zobaczyć przykłady zarówno jawne i niejawne sprzężenia wewnętrznego.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Przeprowadź lewe sprzężenie zewnętrzne, używając Group Join — klauzula  
 LEWE sprzężenie zewnętrzne zawiera wszystkie elementy z kolekcji po lewej stronie, sprzężenia i tylko pasujących wartości z kolekcji po prawej stronie sprzężenia. Wszystkie elementy z kolekcji po prawej stronie sprzężenia, które nie mają pasujący element w kolekcji po lewej stronie są wykluczane z wyników kwerendy.  
  
 `Group Join` Klauzuli wykonuje w praktyce z LEFT OUTER JOIN. Różnica między zwykle określane jako LEWE sprzężenie zewnętrzne i jakie `Group Join` klauzula zwraca, jest to, że `Group Join` klauzuli grupy wyników z kolekcji po prawej stronie sprzężenia dla każdego elementu w kolekcji po lewej stronie. W relacyjnej bazie danych LEWE sprzężenie zewnętrzne zwraca wynik niezgrupowane, w której wynik każdego elementu w zapytaniu zawiera pasujące elementy z obu kolekcji sprzężenia. W tym przypadku elementy z kolekcji po lewej stronie sprzężenia są powtarzane dla każdego pasującego elementu z kolekcji po prawej stronie. Zobaczysz, jak to wygląda po zakończeniu następnej procedury.  
  
 Możesz pobrać wyniki `Group Join` zapytania, ponieważ wynik niezgrupowane, rozszerzając swoje zapytanie, aby zwrócić element dla każdego wyniku kwerendy zgrupowane. Aby to osiągnąć, należy upewnić się, czy wysyłać zapytania o `DefaultIfEmpty` metoda zgrupowaną kolekcję. Daje to gwarancję, że elementy z kolekcji po lewej stronie sprzężenia, nadal będą uwzględniane w wyniku zapytania, nawet jeśli mają one nie pasujących wyników z kolekcji po prawej stronie. Można dodać kod do zapytania Podaj wartość wyniku domyślną, gdy nie ma dopasowania wartości z kolekcji po prawej stronie sprzężenia.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Aby wykonać Left Outer Join przy użyciu klauzuli Join grupy  
  
1.  Dodaj następujący kod do `Module1` modułu w projekcie, aby zobaczyć przykłady pogrupowanych lewe sprzężenie zewnętrzne i niezgrupowane lewego sprzężenia zewnętrznego.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Przeprowadź sprzężenia, używając klucz złożony  
 Możesz użyć `And` — słowo kluczowe w `Join` lub `Group Join` klauzulę, aby zidentyfikować wiele pól klucza do użycia podczas dopasowywania wartości z kolekcji jest dołączony. `And` — Słowo kluczowe Określa, że wszystkie określone pola klucza musi być zgodna dla elementów, które ma zostać umieszczony.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Do wykonania sprzężenia, przy użyciu klucza złożonego  
  
1.  Dodaj następujący kod do `Module1` modułu w projekcie, aby zobaczyć przykłady sprzężenia, który używa klucza złożonego.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Uruchamianie kodu  
  
#### <a name="to-add-code-to-run-the-examples"></a>Aby dodać kod, aby uruchomić przykłady  
  
1.  Zastąp `Sub Main` w `Module1` modułu w projekcie, używając następującego kodu, aby uruchomić przykłady w tym temacie.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2.  Naciśnij klawisz F5, aby uruchomić przykłady.  
  
## <a name="see-also"></a>Zobacz także
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join, klauzula](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Klauzula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From, klauzula](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where, klauzula](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [Przekształcanie danych za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
