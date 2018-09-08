---
title: 'Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 50a4dff90dc1ce02869978f1da147e530cefc3e1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44176699"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)
Language-Integrated Query (LINQ) ułatwia dostęp do informacji z bazy danych, łącznie z procedurami obiektów, takich jak przechowywane w bazie danych.  
  
 Poniższy przykład pokazuje, jak utworzyć aplikację, która wywołuje procedurę składowaną w bazie danych programu SQL Server. Przykład pokazuje sposób wywoływania dwie różne procedury składowane w bazie danych. Każda procedura zwraca wyniki zapytania. Jednej procedury pobiera parametry wejściowe, a inne procedury nie przyjmuje parametrów.  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Aby dodać procedur składowanych do Projektanta obiektów relacyjnych  
  
1.  W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń **procedur składowanych** folderu.  
  
     Po zamknięciu O/R Designer, możesz otworzyć go ponownie, klikając dwukrotnie plik northwind.dbml, który został dodany wcześniej.  
  
2.  Kliknij przycisk **sprzedaż według roku** procedury składowanej i przeciągnij go do prawego okienka projektanta. Kliknij przycisk **dziesięć najbardziej kosztowne produktów** procedury składowanej przeciągnij go do prawego okienka projektanta.  
  
3.  Zapisz zmiany i zamknij projektanta.  
  
4.  Zapisz projekt.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Aby dodać kod, aby wyświetlić wyniki procedur składowanych  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza Windows do projektu formularz Form1.  
  
2.  Kliknij dwukrotnie Form1, aby dodać kod do jego `Load` zdarzeń.  
  
3.  Po dodaniu procedur składowanych do projektanta O/R designer dodano <xref:System.Data.Linq.DataContext> obiektu w projekcie. Ten obiekt zawiera kod, który musi mieć, aby dostęp do tych procedur. <xref:System.Data.Linq.DataContext> Obiektu dla projektu jest nazwany na podstawie nazwy pliku dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i wywołanie metody procedury składowanej określony przez projektanta O/R. Aby powiązać <xref:System.Windows.Forms.DataGridView> obiektu może być konieczne wymuszenie kwerenda do wykonania od razu, wywołując <xref:System.Linq.Enumerable.ToList%2A> metody w wynikach procedury składowanej.  
  
     Dodaj następujący kod do `Load` zdarzenie, aby wywołać jedną z procedur składowanych, widoczne jako metody dla kontekstu danych.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
