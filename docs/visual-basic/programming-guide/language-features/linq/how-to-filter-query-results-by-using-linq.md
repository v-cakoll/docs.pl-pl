---
title: "Porady: filtrowanie wyników zapytania za pomocą LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09f2eb65858853fd759ae033f749151b348c124d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>Porady: filtrowanie wyników zapytania za pomocą LINQ (Visual Basic)
Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do bazy danych informacji i wykonywanie zapytań.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server i filtruje wyniki według określonej wartości przy użyciu `Where` klauzuli. Aby uzyskać więcej informacji, zobacz [klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
 W przykładach w tym temacie użyto przykładowej bazy danych Northwind. Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](https://msdn.microsoft.com/library/bb399411).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1.  W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.  
  
2.  Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.  
  
3.  Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera LINQ do SQL pliku  
  
1.  W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**. Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**. Wybierz **klasy LINQ do SQL** szablon elementu.  
  
3.  Nadaj nazwę plikowi `northwind.dbml`. Kliknij przycisk **Dodaj**. Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) otwiera plik northwind.dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Aby dodać tabele, aby zapytania do Projektanta obiektów relacyjnych  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń węzeł **tabel** folderu.  
  
     Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.  
  
2.  Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta. Tabela zamówienia kliknij i przeciągnij go do lewego okienka projektanta.  
  
     Projektant tworzy nowy `Customer` i `Order` obiektów dla projektu. Zwróć uwagę, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości w poszukiwaniu powiązanych obiektów podrzędnych. Na przykład IntelliSense będzie wynikać, że `Customer` obiekt ma `Orders` właściwości dla wszystkich zleceń związane z tego klienta.  
  
3.  Zapisz zmiany i zamknij projektanta.  
  
4.  Zapisz projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Aby dodać kod, aby w bazie danych i wyświetlić wyniki  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.  
  
2.  Kliknij dwukrotnie Form1 kod, aby dodać `Load` zdarzenia formularza.  
  
3.  Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu dla projektu. Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel, oprócz poszczególnych obiektów i kolekcji dla każdej tabeli. <xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez Projektanta obiektów relacyjnych.  
  
     Dodaj następujący kod do `Load` zdarzenie, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości kontekstu danych. Kwerenda filtruje wyniki i zwraca tylko klienci, którzy znajdują się w `London`.  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
5.  Poniżej przedstawiono niektóre filtry, których można spróbować.  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ do SQL](https://msdn.microsoft.com/library/bb386976)  
 [Metody DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
