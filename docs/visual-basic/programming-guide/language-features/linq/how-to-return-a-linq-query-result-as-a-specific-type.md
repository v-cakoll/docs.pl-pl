---
title: 'Instrukcje: Zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 784a848b02e75d2ae9a6c6530141e69a05a9041b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973499"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Instrukcje: Zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)
Language-Integrated Query (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywania zapytań. Domyślnie zapytania LINQ zwracają listę obiektów jako typu anonimowego. Można również określić, że zapytanie zwraca listę określonego typu przy użyciu `Select` klauzuli.  
  
 Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje zapytania względem bazy danych programu SQL Server i projektami wyniki jako określonego typu nazwanego. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) i [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
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
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Aby dodać tabele do zapytania O/R Designer  
  
1.  W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń **tabel** folderu.  
  
     Po zamknięciu O/R Designer, możesz otworzyć go ponownie, klikając dwukrotnie plik northwind.dbml, który został dodany wcześniej.  
  
2.  Kliknij tabelę klientów i przeciągnij go do okienka po lewej stronie projektanta.  
  
     Projektant tworzy nową `Customer` obiektu w projekcie. Można poddawać projekcji wynik kwerendy w postaci `Customer` typu lub jako typ, który tworzysz. W tym przykładzie utworzysz nowy typ w dalszej części procedury i projektu jako typu wyniku zapytania.  
  
3.  Zapisz zmiany i zamknij projektanta.  
  
4.  Zapisz projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Aby dodać kod do wykonywania zapytań bazy danych i wyświetlić wyniki  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza Windows do projektu formularz Form1.  
  
2.  Kliknij dwukrotnie Form1, aby zmodyfikować klasy Form1.  
  
3.  Po `End Class` instrukcji Form1 klasy, Dodaj następujący kod, aby utworzyć `CustomerInfo` typu do przechowywania wyników zapytania dla tego przykładu.  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4.  Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodano <xref:System.Data.Linq.DataContext> obiektu do projektu. Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel i uzyskiwać dostęp do poszczególnych obiektów i kolekcji, dla każdej tabeli. <xref:System.Data.Linq.DataContext> Obiektu dla Twojego projektu jest nazwany na podstawie nazwy pliku dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez projektanta O/R.  
  
     W `Load` zdarzeń klasy Form1, Dodaj następujący kod, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości kontekstu danych. `Select` Klauzuli zapytania zostanie utworzony nowy `CustomerInfo` typu zamiast typu anonimowego dla każdego elementu wyniku kwerendy.  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5.  Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.  
  
## <a name="see-also"></a>Zobacz także
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
