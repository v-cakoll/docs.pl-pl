---
title: 'Instrukcje: zapytanie dotyczące bazy danych za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: ad4744e1734fd968f610ec02b60814eadd3ebe9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404968"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a>Porady: zapytanie dotyczące bazy danych za pomocą LINQ (Visual Basic)
Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację wykonującą zapytania względem bazy danych SQL Server.  
  
 Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1. W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając pozycję **Eksplorator serwera** / **Eksplorator bazy danych** w menu **Widok** .  
  
2. Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.  
  
3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera plik LINQ to SQL  
  
1. W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**. Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.  
  
2. W menu **projekt** kliknij polecenie **Dodaj nowy element**. Wybierz szablon elementu **LINQ to SQL klas** .  
  
3. Nazwij plik `northwind.dbml`. Kliknij pozycję **Dodaj**. Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a>Aby dodać tabele do zapytania do projektanta O/R  
  
1. W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind. Rozwiń folder **tabele** .  
  
     Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.  
  
2. Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta. Kliknij tabelę Orders (zamówienia) i przeciągnij ją do okienka po lewej stronie projektanta.  
  
     Projektant tworzy nowe `Customer` i `Order` obiekty dla projektu. Zauważ, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów. Na przykład technologia IntelliSense pokazuje, że `Customer` obiekt ma `Orders` Właściwość dla wszystkich zamówień związanych z tym klientem.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz projekt.  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Aby dodać kod do zapytania do bazy danych i wyświetlić wyniki  
  
1. Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.  
  
2. Kliknij dwukrotnie przycisk Form1, aby dodać kod do `Load` zdarzenia formularza.  
  
3. Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt dla projektu. Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel, oprócz pojedynczych obiektów i kolekcji dla każdej tabeli. <xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .  
  
     Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.  
  
     Dodaj następujący kod do zdarzenia, `Load` Aby wykonać zapytanie dotyczące tabel, które są uwidocznione jako właściwości kontekstu danych.  
  
     [!code-vb[VbLINQToSQLHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#3)]  
  
4. Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
5. Poniżej znajdują się dodatkowe zapytania, które można wypróbować:  
  
     [!code-vb[VbLINQToSQLHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#4)]  
    [!code-vb[VbLINQToSQLHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- [LINQ](index.md)
- [Zapytania](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
