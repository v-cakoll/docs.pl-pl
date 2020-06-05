---
title: 'Instrukcje: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: a148d8b726da78261eda152fcaafdd64ea01bb24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404981"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Porady: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania za pomocą LINQ (Visual Basic)
Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację wykonującą zapytania względem bazy danych SQL Server. Przykład określa minimalną i maksymalną wartość dla wyników przy użyciu `Aggregate` `Group By` klauzul i. Aby uzyskać więcej informacji, zobacz [klauzula agregująca](../../../language-reference/queries/aggregate-clause.md) i [klauzula GROUP by](../../../language-reference/queries/group-by-clause.md).  
  
 Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>Utwórz połączenie z bazą danych  
  
1. W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając pozycję **Eksplorator serwera** / **Eksplorator bazy danych** w menu **Widok** .  
  
2. Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.  
  
3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt, który zawiera plik LINQ to SQL  
  
1. W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**. Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.  
  
2. W menu **projekt** kliknij polecenie **Dodaj nowy element**. Wybierz szablon elementu **LINQ to SQL klas** .  
  
3. Nazwij plik `northwind.dbml`. Kliknij pozycję **Dodaj**. Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>Dodawanie tabel do zapytania do projektanta O/R  
  
1. W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind. Rozwiń folder **tabele** .  
  
     Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.  
  
2. Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta. Kliknij tabelę Orders (zamówienia) i przeciągnij ją do okienka po lewej stronie projektanta.  
  
     Projektant tworzy nowe `Customer` i `Order` obiekty dla projektu. Zauważ, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów. Na przykład technologia IntelliSense pokazuje, że `Customer` obiekt ma `Orders` Właściwość dla wszystkich zamówień związanych z tym klientem.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz projekt.  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>Dodaj kod, aby wykonać zapytanie do bazy danych i wyświetlić wyniki  
  
1. Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.  
  
2. Kliknij dwukrotnie przycisk Form1, aby dodać kod do `Load` zdarzenia formularza.  
  
3. Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt dla projektu. Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel, oprócz pojedynczych obiektów i kolekcji dla każdej tabeli. <xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .  
  
     Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.  
  
     Dodaj następujący kod do `Load` zdarzenia. Ten kod wysyła zapytania do tabel, które są uwidocznione jako właściwości kontekstu danych i określają minimalną i maksymalną wartość dla wyników. Przykład używa `Aggregate` klauzuli do zapytania dla pojedynczego wyniku, a `Group By` klauzula, aby wyświetlić średnią dla zgrupowanych wyników.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Naciśnij klawisz **F5** , aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ](index.md)
- [Zapytania](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
