---
title: 'Porady: zwracanie wyniku zapytania LINQ jako określonego typu'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: c8ed792bf3ffefd903d60522f621958e44546d32
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404955"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Porady: zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)
Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań. Domyślnie zapytania LINQ zwracają listę obiektów jako typ anonimowy. Możesz również określić, że zapytanie zwróci listę określonego typu przy użyciu `Select` klauzuli.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje zapytania dotyczące bazy danych SQL Server i projektuje wyniki jako określony nazwany typ. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../objects-and-classes/anonymous-types.md) i [klauzula SELECT](../../../language-reference/queries/select-clause.md).  
  
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
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Aby dodać tabele do zapytania do projektanta O/R  
  
1. W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind. Rozwiń folder **tabele** .  
  
     Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.  
  
2. Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta.  
  
     Projektant tworzy nowy `Customer` obiekt dla projektu. Wyniki zapytania można projektować jako `Customer` Typ lub jako typ, który tworzysz. Ten przykład utworzy nowy typ w późniejszej procedurze i projektuje wynik zapytania jako ten typ.  
  
3. Zapisz zmiany i zamknij projektanta.  
  
4. Zapisz projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Aby dodać kod do zapytania do bazy danych i wyświetlić wyniki  
  
1. Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.  
  
2. Kliknij dwukrotnie przycisk Form1, aby zmodyfikować klasę Form1.  
  
3. Po `End Class` instrukcji klasy Form1 Dodaj następujący kod, aby utworzyć `CustomerInfo` Typ do przechowywania wyników zapytania dla tego przykładu.  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt do projektu. Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel i uzyskać dostęp do poszczególnych obiektów i kolekcji dla każdej tabeli. <xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .  
  
     Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.  
  
     W `Load` przypadku klasy Form1 Dodaj następujący kod, aby wykonać zapytanie dotyczące tabel, które są uwidocznione jako właściwości kontekstu danych. `Select`Klauzula zapytania utworzy nowy `CustomerInfo` Typ zamiast typu anonimowego dla każdego elementu wyniku zapytania.  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ](index.md)
- [Zapytania](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
