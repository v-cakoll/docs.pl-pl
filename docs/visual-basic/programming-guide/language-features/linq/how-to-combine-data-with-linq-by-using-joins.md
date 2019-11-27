---
title: 'Instrukcje: łączenie danych z LINQ przy użyciu sprzężeń'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345003"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Porady: łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)
Visual Basic zawiera klauzule zapytań `Join` i `Group Join`, które umożliwiają łączenie zawartości wielu kolekcji na podstawie wspólnych wartości między kolekcjami. Te wartości są znane jako wartości *klucza* . Deweloperzy znający koncepcje relacyjnych baz danych będą rozpoznawać klauzulę `Join` jako SPRZĘŻENIe wewnętrzne i klauzulę `Group Join` jako, efektywnie, lewe SPRZĘŻENIe zewnętrzne.  
  
 Przykłady w tym temacie przedstawiają kilka sposobów łączenia danych przy użyciu `Join` i `Group Join` klauzule zapytania.  
  
## <a name="create-a-project-and-add-sample-data"></a>Tworzenie projektu i Dodawanie przykładowych danych  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Aby utworzyć projekt zawierający przykładowe dane i typy  
  
1. Aby uruchomić przykłady w tym temacie, Otwórz program Visual Studio i Dodaj nowy projekt aplikacji konsolowej Visual Basic. Kliknij dwukrotnie plik Module1. vb utworzony przez Visual Basic.  
  
2. Przykłady w tym temacie używają typów `Person` i `Pet` i danych z następującego przykładu kodu. Skopiuj ten kod do domyślnego modułu `Module1` utworzonego przez Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Wykonywanie sprzężenia wewnętrznego przy użyciu klauzuli join  
 SPRZĘŻENIe wewnętrzne łączy dane z dwóch kolekcji. Elementy, dla których są uwzględniane określone wartości klucza. Wszystkie elementy z kolekcji, które nie mają pasującego elementu w innej kolekcji, są wykluczone.  
  
 W Visual Basic LINQ oferuje dwie opcje wykonywania SPRZĘŻENIa wewnętrznego: niejawne sprzężenie i jawne sprzężenie.  
  
 Niejawne sprzężenie określa kolekcje, które mają być sprzężone w klauzuli `From` i identyfikuje pola klucza pasujące w klauzuli `Where`. Visual Basic niejawnie sprzęga dwie kolekcje na podstawie określonych pól kluczy.  
  
 Możesz określić jawne sprzężenie przy użyciu klauzuli `Join`, jeśli chcesz, aby były specyficzne dla pól klucza do użycia w sprzężeniu. W takim przypadku klauzula `Where` może nadal służyć do filtrowania wyników zapytania.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Aby wykonać sprzężenie wewnętrzne przy użyciu klauzuli join  
  
1. Dodaj następujący kod do modułu `Module1` w projekcie, aby zobaczyć przykłady zarówno niejawnego, jak i jawnego sprzężenia wewnętrznego.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Wykonaj lewe sprzężenie zewnętrzne przy użyciu klauzuli Group Join  
 LEWE SPRZĘŻENIe zewnętrzne obejmuje wszystkie elementy z kolekcji po lewej stronie sprzężenia i tylko pasujące wartości z kolekcji po prawej stronie sprzężenia. Wszystkie elementy z kolekcji po prawej stronie sprzężenia, które nie mają pasującego elementu w kolekcji po lewej stronie, są wykluczone z wyniku zapytania.  
  
 Klauzula `Group Join` wykonuje w efekcie lewe SPRZĘŻENIe zewnętrzne. Różnica między to, co jest zwykle znane jako lewe SPRZĘŻENIe zewnętrzne i co zwraca klauzulę `Group Join`, jest to, że klauzula `Group Join` grupuje wyniki z kolekcji po prawej stronie sprzężenia dla każdego elementu w kolekcji po lewej stronie. W relacyjnej bazie danych lewe SPRZĘŻENIe zewnętrzne zwraca niezgrupowane wyniki, w których każdy element w wyniku zapytania zawiera pasujące elementy z obu kolekcji w sprzężeniu. W tym przypadku elementy z kolekcji po lewej stronie sprzężenia są powtórzone dla każdego pasującego elementu z kolekcji po prawej stronie. Po zakończeniu następnej procedury zobaczysz, jak to wygląda.  
  
 Wyniki zapytania `Group Join` można pobrać jako niepogrupowany wynik, rozszerzając zapytanie w celu zwrócenia elementu dla każdego pogrupowanego wyniku zapytania. Aby to osiągnąć, należy się upewnić, że wykonujesz zapytania na `DefaultIfEmpty` metodzie zgrupowanej kolekcji. Dzięki temu elementy z kolekcji po lewej stronie sprzężenia są nadal uwzględniane w wynikach zapytania, nawet jeśli nie mają pasujących wyników z kolekcji po prawej stronie. Możesz dodać kod do zapytania, aby podać domyślną wartość wynikową, gdy nie ma pasującej wartości z kolekcji po prawej stronie sprzężenia.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Aby wykonać lewe sprzężenie zewnętrzne przy użyciu klauzuli Group Join  
  
1. Dodaj następujący kod do modułu `Module1` w projekcie, aby zobaczyć przykłady pogrupowanego lewego sprzężenia zewnętrznego i niezgrupowanego sprzężenia zewnętrznego.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Wykonywanie sprzężenia przy użyciu klucza złożonego  
 Możesz użyć słowa kluczowego `And` w klauzuli `Join` lub `Group Join`, aby zidentyfikować wiele pól klucza do użycia podczas dopasowywania wartości z kolekcji, które są sprzężone. Słowo kluczowe `And` określa, że wszystkie określone pola kluczy muszą być zgodne dla elementów do przyłączenia.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Aby wykonać sprzężenie przy użyciu klucza złożonego  
  
1. Dodaj następujący kod do modułu `Module1` w projekcie, aby zobaczyć przykłady sprzężenia korzystającego z klucza złożonego.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Uruchom kod  
  
#### <a name="to-add-code-to-run-the-examples"></a>Aby dodać kod do uruchamiania przykładów  
  
1. Zastąp `Sub Main` w module `Module1` w projekcie następującym kodem, aby uruchomić przykłady w tym temacie.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Naciśnij klawisz F5, aby uruchomić przykłady.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join, klauzula](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join, klauzula](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From, klauzula](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where, klauzula](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [Przekształcenia danych za pomocą LINQC#()](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
