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
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112365"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Porady: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania za pomocą LINQ (Visual Basic)
Zintegrowana z językiem kwerenda (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.  
  
 W poniższym przykładzie pokazano, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server. Próbka określa minimalne i maksymalne wartości dla `Aggregate` `Group By` wyników przy użyciu i klauzul. Aby uzyskać więcej informacji, zobacz [Klauzula agregująca](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [Klauzula grupy według](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Przykłady w tym temacie użyć bazy danych Northwind przykład. Jeśli ta baza danych nie jest zabezpieczone na komputerze deweloperskim, można ją pobrać z Centrum pobierania Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>Tworzenie połączenia z bazą danych  
  
1. W programie Visual Studio otwórz**Eksploratora bazy danych** **Eksploratora**/serwerów, klikając polecenie**Eksplorator baz danych** **Eksploratora**/serwerów w menu **Widok.**  
  
2. Kliknij prawym przyciskiem myszy pozycję **Połączenia danych** w Eksploratorze bazy danych **Eksploratora**/**serwerów,** a następnie kliknij polecenie **Dodaj połączenie**.  
  
3. Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Aby dodać projekt zawierający linq do pliku SQL  
  
1. W programie Visual Studio w menu **Plik** wskaż polecenie **Nowy,** a następnie kliknij polecenie **Projekt**. Jako typ projektu wybierz opcję Visual Basic **Windows Forms Application.**  
  
2. W menu **Projekt** kliknij polecenie **Dodaj nowy element**. Wybierz szablon elementu **LINQ do klas SQL.**  
  
3. Nazwij plik `northwind.dbml`. Kliknij przycisk **Dodaj**. Projektant relacyjnego obiektu (O/R Designer) jest otwarty dla pliku northwind.dbml.  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>Dodawanie tabel do kwerendy do projektanta o/r  
  
1. W/**Eksploratorze bazy danych** **Eksploratora serwerów**rozwiń połączenie z bazą danych Northwind. Rozwiń folder **Tabele.**  
  
     Jeśli projektant o/r został zamknięty, można go ponownie otworzyć, klikając dwukrotnie dodany wcześniej plik northwind.dbml.  
  
2. Kliknij tabelę Klienci i przeciągnij ją w lewe okienko projektanta. Kliknij tabelę Zamówienia i przeciągnij ją w lewe okienko projektanta.  
  
     Projektant tworzy `Customer` nowe `Order` i obiekty dla projektu. Należy zauważyć, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów. Na przykład IntelliSense pokaże, `Customer` że `Orders` obiekt ma właściwość dla wszystkich zamówień związanych z tym klientem.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz swój projekt.  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>Dodaj kod, aby zbadać bazę danych i wyświetlić wyniki  
  
1. Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślny formularz systemu Windows dla projektu Form1.  
  
2. Kliknij dwukrotnie form1, aby `Load` dodać kod do zdarzenia formularza.  
  
3. Po dodaniu tabel do projektanta O/R <xref:System.Data.Linq.DataContext> projektant dodał obiekt dla projektu. Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel, oprócz poszczególnych obiektów i kolekcji dla każdej tabeli. Obiekt <xref:System.Data.Linq.DataContext> dla projektu ma nazwę na podstawie nazwy pliku .dbml. W przypadku tego <xref:System.Data.Linq.DataContext> projektu `northwindDataContext`obiekt nosi nazwę .  
  
     Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i kwerendy tabel określonych przez Projektanta O/R.  
  
     Dodaj następujący kod `Load` do zdarzenia. Ten kod wysyła kwerendy tabel, które są udostępniane jako właściwości kontekstu danych i określa minimalne i maksymalne wartości dla wyników. W przykładzie `Aggregate` używa klauzuli do kwerendy `Group By` dla pojedynczego wyniku i klauzuli, aby wyświetlić średnią dla wyników grupowanych.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Naciśnij **klawisz F5,** aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też

- [Linq](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
