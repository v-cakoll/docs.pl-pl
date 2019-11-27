---
title: 'Instrukcje: wywoływanie procedury składowanej przy użyciu LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345027"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)
Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych, takich jak obiekty bazy danych, takie jak procedury składowane.  
  
 Poniższy przykład pokazuje, jak utworzyć aplikację, która wywołuje procedurę przechowywaną w bazie danych SQL Server. Przykład pokazuje, jak wywoływać dwie różne procedury składowane w bazie danych. Każda procedura zwraca wyniki zapytania. Jedna procedura przyjmuje parametry wejściowe, a druga procedura nie przyjmuje parametrów.  
  
 Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1. W programie Visual Studio Otwórz **Eksplorator serwera**/**Eksplorator bazy danych** , klikając pozycję **Eksplorator serwera**/**Eksplorator bazy danych** w menu **Widok** .  
  
2. Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera**/**Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.  
  
3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera plik LINQ to SQL  
  
1. W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**. Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.  
  
2. W menu **projekt** kliknij polecenie **Dodaj nowy element**. Wybierz szablon elementu **LINQ to SQL klas** .  
  
3. Nadaj plikowi nazwę `northwind.dbml`. Kliknij przycisk **Dodaj**. Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Aby dodać procedury składowane do projektanta O/R  
  
1. W **Eksplorator serwera**/**Eksplorator bazy danych**rozwiń połączenie z bazą danych Northwind. Rozwiń folder **procedury składowane** .  
  
     Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.  
  
2. Kliknij procedurę składowaną **sprzedaż według roku** i przeciągnij ją do okienka po prawej stronie projektanta. Kliknij **dziesięć najbardziej kosztowne** procedury przechowywane produkty przeciągnij ją do okienka po prawej stronie projektanta.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz projekt.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Aby dodać kod, aby wyświetlić wyniki procedur składowanych  
  
1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.DataGridView> do domyślnego formularza systemu Windows dla projektu, Form1.  
  
2. Kliknij dwukrotnie przycisk Form1, aby dodać kod do jego zdarzenia `Load`.  
  
3. Po dodaniu procedur składowanych do projektanta O/R Projektant dodał obiekt <xref:System.Data.Linq.DataContext> dla projektu. Ten obiekt zawiera kod, który musi być wymagany, aby uzyskać dostęp do tych procedur. Obiekt <xref:System.Data.Linq.DataContext> dla projektu jest nazwany na podstawie nazwy pliku. dbml. Dla tego projektu obiekt <xref:System.Data.Linq.DataContext> ma nazwę `northwindDataContext`.  
  
     Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i wywoływać metody procedury składowanej określone przez projektanta O/R. Aby powiązać z obiektem <xref:System.Windows.Forms.DataGridView>, może być konieczne wymuszenie natychmiastowego wykonania zapytania przez wywołanie metody <xref:System.Linq.Enumerable.ToList%2A> na wynikach procedury składowanej.  
  
     Dodaj następujący kod do zdarzenia `Load`, aby wywołać jedną z procedur składowanych dostępnych jako metody dla kontekstu danych.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
