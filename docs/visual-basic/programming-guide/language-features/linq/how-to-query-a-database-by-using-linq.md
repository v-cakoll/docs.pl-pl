---
title: 'Instrukcje: tworzenie zapytań względem bazy danych za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: f4b2510bad2b23d7a0e179383b34c4e425e6564e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344964"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a>Porady: zapytanie dotyczące bazy danych za pomocą LINQ (Visual Basic)
Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację wykonującą zapytania względem bazy danych SQL Server.  
  
 Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1. W programie Visual Studio Otwórz **Eksplorator serwera**/**Eksplorator bazy danych** , klikając pozycję **Eksplorator serwera**/**Eksplorator bazy danych** w menu **Widok** .  
  
2. Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera**/**Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.  
  
3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera plik LINQ to SQL  
  
1. W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**. Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.  
  
2. W menu **projekt** kliknij polecenie **Dodaj nowy element**. Wybierz szablon elementu **LINQ to SQL klas** .  
  
3. Nadaj plikowi nazwę `northwind.dbml`. Kliknij przycisk **Dodaj**. Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a>Aby dodać tabele do zapytania do projektanta O/R  
  
1. W **Eksplorator serwera**/**Eksplorator bazy danych**rozwiń połączenie z bazą danych Northwind. Rozwiń folder **tabele** .  
  
     Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.  
  
2. Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta. Kliknij tabelę Orders (zamówienia) i przeciągnij ją do okienka po lewej stronie projektanta.  
  
     Projektant tworzy nowe obiekty `Customer` i `Order` dla projektu. Zauważ, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów. Na przykład technologia IntelliSense pokazuje, że obiekt `Customer` ma właściwość `Orders` dla wszystkich zamówień związanych z tym klientem.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz projekt.  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Aby dodać kod do zapytania do bazy danych i wyświetlić wyniki  
  
1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.DataGridView> do domyślnego formularza systemu Windows dla projektu, Form1.  
  
2. Kliknij dwukrotnie przycisk Form1, aby dodać kod do zdarzenia `Load` formularza.  
  
3. Po dodaniu tabel do projektanta O/R Projektant dodał obiekt <xref:System.Data.Linq.DataContext> dla projektu. Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel, oprócz pojedynczych obiektów i kolekcji dla każdej tabeli. Obiekt <xref:System.Data.Linq.DataContext> dla projektu jest nazwany na podstawie nazwy pliku. dbml. Dla tego projektu obiekt <xref:System.Data.Linq.DataContext> ma nazwę `northwindDataContext`.  
  
     Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.  
  
     Dodaj następujący kod do zdarzenia `Load`, aby wykonać zapytanie dotyczące tabel, które są uwidocznione jako właściwości kontekstu danych.  
  
     [!code-vb[VbLINQToSQLHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#3)]  
  
4. Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
5. Poniżej znajdują się dodatkowe zapytania, które można wypróbować:  
  
     [!code-vb[VbLINQToSQLHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#4)]  
    [!code-vb[VbLINQToSQLHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
