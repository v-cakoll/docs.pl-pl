---
title: 'Instrukcje: Modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)'
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
ms.openlocfilehash: 8770a8761af4b55394d9280b21d2a6a5b71b6ed5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304899"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Instrukcje: Modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)
Language-Integrated Query (LINQ) zapytania ułatwiają dostęp do bazy danych informacji i zmodyfikuj wartości w bazie danych.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację, która pobiera i informacji o aktualizacjach w bazie danych programu SQL Server.  
  
 W przykładach w tym temacie użyto przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z Microsoft Download Center. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1. W programie Visual Studio, otwórz **Eksploratora serwera**/**Eksplorator bazy danych** , klikając **widoku** menu, a następnie wybierz pozycję **Eksploratora serwera** / **Database Explorer**.  
  
2. Kliknij prawym przyciskiem myszy **połączeń danych** w **Eksploratora serwera**/**Eksplorator bazy danych**i kliknij przycisk **Dodaj połączenie**.  
  
3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Aby dodać projekt za pomocą LINQ do pliku SQL  
  
1. W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**. Wybierz pozycję Visual Basic **aplikacja interfejsu Windows Forms** jako typ projektu.  
  
2. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**. Wybierz **klasy LINQ do SQL** szablon elementu.  
  
3. Nadaj plikowi nazwę `northwind.dbml`. Kliknij przycisk **Dodaj**. Object Relational Designer (O/R Designer) jest otwarty w celu `northwind.dbml` pliku.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Aby dodać tabele do zapytania i modyfikację do projektanta  
  
1. W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń **tabel** folderu.  
  
     Jeśli zamknięto O/R Designer, należy go ponownie otworzyć przez dwukrotne kliknięcie `northwind.dbml` pliku, który dodano wcześniej.  
  
2. Kliknij tabelę klientów i przeciągnij go do okienka po lewej stronie projektanta.  
  
     Projektant tworzy nowy obiekt klienta dla Twojego projektu.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz projekt.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Aby dodać kod do modyfikowania bazy danych i wyświetlić wyniki  
  
1. Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza Windows do projektu formularz Form1.  
  
2. Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodano <xref:System.Data.Linq.DataContext> obiektu do projektu. Ten obiekt zawiera kod, który umożliwia dostęp do tabeli Customers. Zawiera kod, który definiuje lokalnego obiektu klienta i kolekcji klientów dla tabeli. <xref:System.Data.Linq.DataContext> Obiektu dla Twojego projektu jest nazwany na podstawie nazwy pliku dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> obiektu w kodzie i zapytań i modyfikowania kolekcji klientów określone przez projektanta O/R. Zmiany wprowadzone do kolekcji klientów nie są odzwierciedlane w bazie danych, dopóki przesyłanie ich przez wywołanie metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody <xref:System.Data.Linq.DataContext> obiektu.  
  
     Kliknij dwukrotnie pozycję Windows formularzu Form1, aby dodać kod, aby <xref:System.Windows.Forms.Form.Load> zdarzeń do wykonywania zapytań w tabeli Klienci, który jest udostępniany jako właściwość swoje <xref:System.Data.Linq.DataContext>. Dodaj następujący kod:  
  
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
  
3. Z **przybornika**, przeciągnij trzy <xref:System.Windows.Forms.Button> formanty do formularza. Zaznacz pierwszą pozycję `Button` kontroli. W **właściwości** oknie `Name` z `Button` kontrolę `AddButton` i `Text` do `Add`. Wybierz drugi przycisk i ustaw `Name` właściwości `UpdateButton` i `Text` właściwość `Update`. Wybierz trzeci przycisk i ustaw `Name` właściwości `DeleteButton` i `Text` właściwość `Delete`.  
  
4. Kliknij dwukrotnie **Dodaj** przycisk, aby dodać kod do jego `Click` zdarzeń. Dodaj następujący kod:  
  
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
  
5. Kliknij dwukrotnie **aktualizacji** przycisk, aby dodać kod do jego `Click` zdarzeń. Dodaj następujący kod:  
  
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
  
6. Kliknij dwukrotnie **Usuń** przycisk, aby dodać kod do jego `Click` zdarzeń. Dodaj następujący kod:  
  
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
  
7. Naciśnij klawisz F5, aby uruchomić projekt. Kliknij przycisk **Dodaj** do dodawania nowego rekordu. Kliknij przycisk **aktualizacji** do modyfikowania nowego rekordu. Kliknij przycisk **Usuń** można usunąć nowy rekord.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
