---
title: 'Instrukcje: modyfikowanie danych w bazie danych za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: 9a10efef5ae92dd21888594ae80a3fc07869a8c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344944"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Porady: modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)

Zapytania dotyczące języka (LINQ) w języku zintegrowanym z językiem umożliwiają łatwe uzyskiwanie dostępu do informacji o bazie danych i modyfikowanie wartości w bazie danych.

Poniższy przykład pokazuje, jak utworzyć nową aplikację, która pobiera i aktualizuje informacje w bazie danych SQL Server.

Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych

1. W programie Visual Studio Otwórz **Eksplorator serwera**/**Eksplorator bazy danych** , klikając menu **Widok** , a następnie wybierając pozycję **Eksplorator serwera**/**Eksplorator bazy danych**.

2. Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera**/**Eksplorator bazy danych**, a następnie kliknij pozycję **Dodaj połączenie**.

3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Aby dodać projekt z plikiem LINQ to SQL

1. W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**. Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**. Wybierz szablon elementu **LINQ to SQL klas** .

3. Nadaj plikowi nazwę `northwind.dbml`. Kliknij przycisk **Dodaj**. Dla pliku `northwind.dbml` zostanie otwarty Object Relational Designer (Projektant O/R).

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Aby dodać tabele do zapytania i modyfikować do projektanta

1. W **Eksplorator serwera**/**Eksplorator bazy danych**rozwiń połączenie z bazą danych Northwind. Rozwiń folder **tabele** .

     Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie przez dwukrotne kliknięcie dodanego wcześniej pliku `northwind.dbml`.

2. Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta.

     Projektant tworzy nowy obiekt klienta dla projektu.

3. Zapisz zmiany i zamknij projektanta.

4. Zapisz projekt.

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Aby dodać kod w celu zmodyfikowania bazy danych i wyświetlenia wyników

1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.DataGridView> do domyślnego formularza systemu Windows dla projektu, Form1.

2. Po dodaniu tabel do projektanta O/R Projektant dodał obiekt <xref:System.Data.Linq.DataContext> do projektu. Ten obiekt zawiera kod, którego można użyć w celu uzyskania dostępu do tabeli Customers. Zawiera również kod definiujący lokalny obiekt klienta i kolekcję Customers dla tabeli. Obiekt <xref:System.Data.Linq.DataContext> dla projektu jest nazwany na podstawie nazwy pliku. dbml. Dla tego projektu obiekt <xref:System.Data.Linq.DataContext> ma nazwę `northwindDataContext`.

     Można utworzyć wystąpienie obiektu <xref:System.Data.Linq.DataContext> w kodzie oraz zapytania i zmodyfikować kolekcję klientów określoną przez projektanta O/R. Zmiany wprowadzane w kolekcji Customers nie są odzwierciedlane w bazie danych, dopóki nie zostaną przesłane przez wywołanie metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A> obiektu <xref:System.Data.Linq.DataContext>.

     Kliknij dwukrotnie formularz systemu Windows, Form1, aby dodać kod do zdarzenia <xref:System.Windows.Forms.Form.Load>, aby wykonać zapytanie do tabeli Customers, która jest udostępniona jako właściwość <xref:System.Data.Linq.DataContext>. Dodaj następujący kod:

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. Z **przybornika**przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki na formularz. Wybierz pierwszą kontrolkę `Button`. W oknie **Właściwości** Ustaw `Name` kontrolki `Button` na `AddButton` i `Text` do `Add`. Wybierz drugi przycisk i ustaw właściwość `Name` na `UpdateButton` i Właściwość `Text` na `Update`. Wybierz trzeci przycisk i ustaw właściwość `Name` na `DeleteButton` i Właściwość `Text` na `Delete`.

4. Kliknij dwukrotnie przycisk **Dodaj** , aby dodać kod do jego zdarzenia `Click`. Dodaj następujący kod:

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. Kliknij dwukrotnie przycisk **Aktualizuj** , aby dodać kod do jego zdarzenia `Click`. Dodaj następujący kod:

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. Kliknij dwukrotnie przycisk **Usuń** , aby dodać kod do jego zdarzenia `Click`. Dodaj następujący kod:

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. Naciśnij klawisz F5, aby uruchomić projekt. Kliknij przycisk **Dodaj** , aby dodać nowy rekord. Kliknij przycisk **Aktualizuj** , aby zmodyfikować nowy rekord. Kliknij przycisk **Usuń** , aby usunąć nowy rekord.

## <a name="see-also"></a>Zobacz także

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
