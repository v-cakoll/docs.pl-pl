---
title: 'Porady: zliczanie, sumowanie, lub uśrednianie danych za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 4584f8ee8b0a87c2150217b1b9eb0c19bc122487
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244205"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>Porady: zliczanie, sumowanie, lub uśrednianie danych za pomocą LINQ (Visual Basic)
Language-Integrated Query (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywania zapytań.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje zapytania względem bazy danych programu SQL Server. Próbka jest liczona sumuje i średnie wyniki za pomocą `Aggregate` i `Group By` klauzul. Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [grupy przez klauzulę](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 W przykładach w tym temacie użyto przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z Microsoft Download Center. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1.  W programie Visual Studio, otwórz **Eksploratora serwera**/**Eksplorator bazy danych** , klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.  
  
2.  Kliknij prawym przyciskiem myszy **połączeń danych** w **Eksploratora serwera**/**Eksplorator bazy danych** a następnie kliknij przycisk **Dodaj połączenie**.  
  
3.  Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera plik LINQ to SQL  
  
1.  W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**. Wybierz pozycję Visual Basic **aplikacja interfejsu Windows Forms** jako typ projektu.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**. Wybierz **klasy LINQ do SQL** szablon elementu.  
  
3.  Nadaj plikowi nazwę `northwind.dbml`. Kliknij przycisk **Dodaj**. Zostanie otwarty plik northwind.dbml Object Relational Designer (O/R Designer).  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Aby dodać tabele do zapytania O/R Designer  
  
1.  W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń **tabel** folderu.  
  
     Po zamknięciu O/R Designer, możesz otworzyć go ponownie, klikając dwukrotnie plik northwind.dbml, który został dodany wcześniej.  
  
2.  Kliknij tabelę klientów i przeciągnij go do okienka po lewej stronie projektanta. Kliknij w tabeli zamówienia, a następnie przeciągnij go do okienka po lewej stronie projektanta.  
  
     Projektant tworzy nowe `Customer` i `Order` obiektów dla Twojego projektu. Należy zauważyć, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości w poszukiwaniu powiązanych obiektów podrzędnych. Na przykład, IntelliSense będzie wynikać, że `Customer` obiekt ma `Orders` właściwości dla wszystkich zamówień związane z tego klienta.  
  
3.  Zapisz zmiany i zamknij projektanta.  
  
4.  Zapisz projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Aby dodać kod do wykonywania zapytań bazy danych i wyświetlić wyniki  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza Windows do projektu formularz Form1.  
  
2.  Kliknij dwukrotnie Form1, aby dodać kod, aby `Load` zdarzenia formularza.  
  
3.  Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodano <xref:System.Data.Linq.DataContext> obiektu w projekcie. Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel i uzyskiwać dostęp do poszczególnych obiektów i kolekcji, dla każdej tabeli. <xref:System.Data.Linq.DataContext> Obiektu dla Twojego projektu jest nazwany na podstawie nazwy pliku dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez projektanta O/R.  
  
     Dodaj następujący kod do `Load` zdarzenie, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości usługi <xref:System.Data.Linq.DataContext> count, Suma i średniej dla otrzymanych wyników. W przykładzie użyto `Aggregate` klauzuli do wykonywania zapytań w jeden wynik i `Group By` klauzuli, aby pokazać średnią dla pogrupowane wyniki.  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Aggregate, klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Group By, klauzula](../../../../visual-basic/language-reference/queries/group-by-clause.md)
