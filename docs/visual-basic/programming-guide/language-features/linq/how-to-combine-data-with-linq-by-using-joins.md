---
title: "Porady: łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Porady: łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)
Visual Basic zapewnia `Join` i `Group Join` zapytania klauzule umożliwiają łączenie zawartości wielu kolekcji na podstawie wartości typowych między kolekcjami. Te wartości są określane jako *klucza* wartości. Rozpozna znasz koncepcji relacyjnej bazy danych dla deweloperów `Join` klauzuli jako INNER JOIN i `Group Join` klauzuli jako efektywnie LEFT OUTER JOIN.  
  
 W przykładach w tym temacie przedstawiono kilka sposobów na łączenie danych za pomocą `Join` i `Group Join` klauzule zapytań.  
  
## <a name="create-a-project-and-add-sample-data"></a>Tworzenie projektu i Dodawanie przykładowych danych  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Aby utworzyć projekt, który zawiera przykładowych danych i typów  
  
1.  Aby uruchomić przykłady w tym temacie, Otwórz program Visual Studio i dodać nowy projekt aplikacji konsoli języka Visual Basic. Kliknij dwukrotnie plik Module1.vb utworzony przez program Visual Basic.  
  
2.  Przykłady w tym temacie `Person` i `Pet` typów i danych w poniższym przykładzie kodu. Skopiuj ten kod do domyślnej `Module1` modułu utworzony przez program Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Przeprowadzanie sprzężenie wewnętrzne przy użyciu klauzuli Join  
 SPRZĘŻENIA wewnętrznego łączy dane z dwóch kolekcji. Uwzględniane są elementy, dla których określonej wartości klucza są zgodne. Wszystkie elementy z jednej kolekcji, które nie ma pasującego elementu w innej kolekcji są wyłączone.  
  
 W języku Visual Basic LINQ są dostępne dwie opcje umożliwiające wykonywanie sprzężenie wewnętrzne: sprzężenie niejawnych i jawnych sprzężenia.  
  
 Sprzężenie niejawne określa kolekcje, które ma zostać umieszczony `From` klauzuli i identyfikuje dopasowania pól kluczy w `Where` klauzuli. Visual Basic niejawnie łączy dwie kolekcje, w oparciu o określone pola klucza.  
  
 Można określić jawnego sprzężenia przy użyciu `Join` klauzuli umożliwia konkretnym klucz, do którego pola, aby użyć sprzężenia. W takim przypadku `Where` nadal można używać klauzuli mają być filtrowane wyniki zapytania.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Do wykonania sprzężenia wewnętrznego przy użyciu klauzuli Join  
  
1.  Dodaj następujący kod do `Module1` modułu w projekcie, aby wyświetlić przykłady obu jawne i niejawne sprzężenia wewnętrznego.  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Przeprowadź lewe sprzężenie zewnętrzne, używając Group Join — klauzula  
 LEWE sprzężenie zewnętrzne zawiera wszystkie elementy z kolekcji po lewej stronie, a tylko do pasujących wartości z kolekcji po prawej stronie sprzężenia. Wszystkie elementy z kolekcji po prawej stronie sprzężenia, które nie ma pasującego elementu w kolekcji po lewej stronie są wykluczane z wyników zapytania.  
  
 `Group Join` Klauzuli wykonuje w efekcie LEFT OUTER JOIN. Różnica między co to jest często nazywana jest LEWE sprzężenie zewnętrzne, a co `Group Join` klauzula zwraca jest to, że `Group Join` klauzuli grupy wyników z kolekcji po prawej stronie sprzężenia dla każdego elementu w kolekcji po lewej stronie. W relacyjnej bazie danych LEWE sprzężenie zewnętrzne zwraca wynik niezgrupowane powoduje każdego elementu w zapytaniu zawiera pasujących elementów z obu kolekcji sprzężenia. W takim przypadku elementów z kolekcji po lewej stronie sprzężenia są powtarzane dla każdego pasującego elementu z kolekcji po prawej stronie. Pojawi się to wygląd po zakończeniu następnej procedury.  
  
 Można pobrać wyniki `Group Join` zapytania niezgrupowane wyniku rozszerzając zapytania do zwrócenia elementu dla każdego wyniku grupowanych zapytania. W tym celu należy upewnić się, że zapytania na `DefaultIfEmpty` metody zgrupowaną kolekcję. Daje to pewność, że elementy z kolekcji po lewej stronie sprzężenia nadal są uwzględniane w wyniku zapytania, nawet jeśli ma zgodnych wyników z kolekcji po prawej stronie. Kod można dodać do zapytania udzielać wynik domyślnie nie istnieje wartość zgodną z kolekcji po prawej stronie sprzężenia.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Aby wykonać Left Outer Join przy użyciu klauzuli Join grupy  
  
1.  Dodaj następujący kod do `Module1` modułu w projekcie, aby wyświetlić przykłady grupowanych lewe sprzężenie zewnętrzne, jak i niezgrupowane lewe sprzężenie zewnętrzne.  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Przeprowadź sprzężenia, używając klucz złożony  
 Można użyć `And` — słowo kluczowe w `Join` lub `Group Join` klauzuli do identyfikowania wielu pól klucza do użycia podczas dopasowywania wartości z kolekcji jest dołączony. `And` — Słowo kluczowe Określa, że wszystkie określone pola klucza musi być zgodna dla elementów, które ma zostać umieszczony.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Aby wykonać sprzężenia przy użyciu klucza złożonego  
  
1.  Dodaj następujący kod do `Module1` modułu w projekcie, aby wyświetlić przykłady sprzężenia, który używa klucza złożonego.  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>Kod uruchomienia  
  
#### <a name="to-add-code-to-run-the-examples"></a>Aby dodać kod do uruchamiania przykładów  
  
1.  Zastąp `Sub Main` w `Module1` modułu w projekcie z następujący kod, aby uruchomić przykłady w tym temacie.  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Naciśnij klawisz F5, aby uruchomić przykłady.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [JOIN — klauzula](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join — klauzula](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Klauzula FROM](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Gdy klauzula](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
 [Przekształcanie danych za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
