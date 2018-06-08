---
title: 'Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 8aad85ce3369f84e82100072bccf389b03c38221
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826922"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)
Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do informacji z bazy danych, łącznie z bazy danych obiektów, takich jak przechowywane procedury.  
  
 Poniższy przykład przedstawia sposób tworzenia aplikacji, która wywołuje procedurę przechowywaną w bazie danych programu SQL Server. Przykład przedstawia sposób wywołania dwie różne procedury przechowywanej w bazie danych. Każdej procedury zwraca wyniki zapytania. Jednej procedury przyjmuje parametry wejściowe i inne procedury nie przyjmuje parametry.  
  
 W przykładach w tym temacie użyto przykładowej bazy danych Northwind. Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z Microsoft Download Center. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1.  W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.  
  
2.  Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.  
  
3.  Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera LINQ do SQL pliku  
  
1.  W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**. Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**. Wybierz **klasy LINQ do SQL** szablon elementu.  
  
3.  Nadaj nazwę plikowi `northwind.dbml`. Kliknij przycisk **Dodaj**. Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla pliku northwind.dbml.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Aby dodać procedur składowanych do Projektanta obiektów relacyjnych  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń węzeł **procedur składowanych** folderu.  
  
     Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.  
  
2.  Kliknij przycisk **sprzedaży przez rok** procedury składowanej i przeciągnij go w okienku po prawej stronie projektanta. Kliknij przycisk **10 najbardziej kosztowne produktów** procedury składowanej przeciągnij go w okienku po prawej stronie projektanta.  
  
3.  Zapisz zmiany i zamknij projektanta.  
  
4.  Zapisz projekt.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Aby dodać kod, aby wyświetlić wyniki procedury składowane  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.  
  
2.  Kliknij dwukrotnie Form1, aby dodać kod, aby jego `Load` zdarzeń.  
  
3.  Po dodaniu procedur składowanych do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu dla projektu. Ten obiekt zawiera kod, który jest potrzebny dostęp do tych procedur. <xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i wywołanie metody procedury składowanej określony przez Projektanta obiektów relacyjnych. Aby powiązać <xref:System.Windows.Forms.DataGridView> obiektów, może zajść potrzeba wymuszenia zapytanie, aby natychmiast wykonać przez wywołanie metody <xref:System.Linq.Enumerable.ToList%2A> metody w wynikach procedury składowanej.  
  
     Dodaj następujący kod do `Load` zdarzeń do wywołania jedną z procedur składowanych udostępniony jako metody dla kontekstu danych.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
