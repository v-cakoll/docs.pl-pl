---
title: 'Instrukcje: wywoływanie procedury składowanej za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: b451642a16f36c4f7fd19c853fdfd2282f5bede5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405033"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)
Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych, takich jak obiekty bazy danych, takie jak procedury składowane.  
  
 Poniższy przykład pokazuje, jak utworzyć aplikację, która wywołuje procedurę przechowywaną w bazie danych SQL Server. Przykład pokazuje, jak wywoływać dwie różne procedury składowane w bazie danych. Każda procedura zwraca wyniki zapytania. Jedna procedura przyjmuje parametry wejściowe, a druga procedura nie przyjmuje parametrów.  
  
 Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1. W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając pozycję **Eksplorator serwera** / **Eksplorator bazy danych** w menu **Widok** .  
  
2. Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.  
  
3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera plik LINQ to SQL  
  
1. W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**. Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.  
  
2. W menu **projekt** kliknij polecenie **Dodaj nowy element**. Wybierz szablon elementu **LINQ to SQL klas** .  
  
3. Nazwij plik `northwind.dbml`. Kliknij pozycję **Dodaj**. Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Aby dodać procedury składowane do projektanta O/R  
  
1. W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind. Rozwiń folder **procedury składowane** .  
  
     Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.  
  
2. Kliknij procedurę składowaną **sprzedaż według roku** i przeciągnij ją do okienka po prawej stronie projektanta. Kliknij **dziesięć najbardziej kosztowne** procedury przechowywane produkty przeciągnij ją do okienka po prawej stronie projektanta.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz projekt.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Aby dodać kod, aby wyświetlić wyniki procedur składowanych  
  
1. Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.  
  
2. Kliknij dwukrotnie przycisk Form1, aby dodać kod do jego `Load` zdarzenia.  
  
3. Po dodaniu procedur składowanych do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt dla projektu. Ten obiekt zawiera kod, który musi być wymagany, aby uzyskać dostęp do tych procedur. <xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .  
  
     Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i wywołać metody procedury składowanej określone przez projektanta O/R. Aby powiązać z <xref:System.Windows.Forms.DataGridView> obiektem, może być konieczne wymuszenie natychmiastowego wykonania zapytania przez wywołanie <xref:System.Linq.Enumerable.ToList%2A> metody na wynikach procedury składowanej.  
  
     Dodaj następujący kod do zdarzenia, `Load` Aby wywołać jedną z procedur składowanych dostępnych jako metody dla kontekstu danych.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ](index.md)
- [Zapytania](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
