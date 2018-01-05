---
title: "Porady: zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b79a00533e4ad8960c7f3cb512aafbe36e50b0
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Porady: zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)
Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do bazy danych informacji i wykonywanie zapytań. Domyślnie zapytań LINQ zwrócić listę obiektów typu anonimowego. Można również określić, że zapytanie zwraca listę o typie określonym za pomocą `Select` klauzuli.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server i projektów wyniki jako określonego typu nazwanego. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) i [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
 W przykładach w tym temacie użyto przykładowej bazy danych Northwind. Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1.  W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.  
  
2.  Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.  
  
3.  Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera LINQ do SQL pliku  
  
1.  W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**. Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**. Wybierz **klasy LINQ do SQL** szablon elementu.  
  
3.  Nadaj nazwę plikowi `northwind.dbml`. Kliknij przycisk **Dodaj**. Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla pliku northwind.dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Aby dodać tabele, aby zapytania do Projektanta obiektów relacyjnych  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń węzeł **tabel** folderu.  
  
     Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.  
  
2.  Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta.  
  
     Tworzy nową klasę projektanta `Customer` obiektu dla projektu. Wynik kwerendy w postaci można wyświetlać `Customer` typu lub typem, który można utworzyć. W tym przykładzie utworzysz nowy typ w dalszej części procedury i projektu jako typu wyniku zapytania.  
  
3.  Zapisz zmiany i zamknij projektanta.  
  
4.  Zapisz projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Aby dodać kod, aby w bazie danych i wyświetlić wyniki  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.  
  
2.  Kliknij dwukrotnie Form1 do modyfikowania klasy Form1.  
  
3.  Po `End Class` instrukcji Form1 klasy, Dodaj następujący kod, aby utworzyć `CustomerInfo` typu do przechowywania wyników zapytania dla tego przykładu.  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu do projektu. Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel i uzyskiwać dostęp do poszczególnych obiektów i kolekcji dla każdej tabeli. <xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez Projektanta obiektów relacyjnych.  
  
     W `Load` zdarzeń klasy Form1, Dodaj następujący kod, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości kontekstu danych. `Select` Klauzuli zapytania utworzy nowy `CustomerInfo` typu zamiast typu anonimowego dla każdego elementu wyniku kwerendy.  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
