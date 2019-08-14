---
title: 'Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: a7d278dd424fbb3167a30d627379f78d0c65476f
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971784"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)

Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz z minimalnymi złożonością. Utworzysz klasę jednostki, która będzie modelować tabelę Customers w przykładowej bazie danych Northwind. Następnie utworzysz proste zapytanie, aby wyświetlić listę klientów, którzy znajdują się w Londynie.

Ten Instruktaż jest zorientowany na kod według projektu, aby pomóc w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokazywania koncepcji. Zwykle mówiąc, użyj Object Relational Designer do utworzenia modelu obiektów.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Ten Instruktaż został zapisany przy użyciu ustawień tworzenia Visual Basic.

## <a name="prerequisites"></a>Wymagania wstępne

- W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest"). Utwórz ten folder przed rozpoczęciem przewodnika.

- Ten Instruktaż wymaga przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych Skopiuj plik do folderu c:\linqtest.

## <a name="overview"></a>Omówienie

Ten przewodnik składa się z sześciu głównych zadań:

- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tworzenie rozwiązania w programie Visual Studio.

- Mapowanie klasy do tabeli bazy danych.

- Wyznaczanie właściwości klasy w celu reprezentowania kolumn bazy danych.

- Określanie połączenia z bazą danych Northwind.

- Tworzenie prostego zapytania do uruchamiania w bazie danych.

- Wykonywanie zapytania i obserwowanie wyników.

## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie rozwiązania LINQ to SQL

W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.

### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć rozwiązanie LINQ to SQL

1. W menu **plik** kliknij pozycję **Nowy projekt**.

2. W okienku **typy projektów** okna dialogowego **nowy projekt** kliknij **Visual Basic**.

3. W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.

4. W polu **Nazwa** wpisz **LinqConsoleApp**.

5. Kliknij przycisk **OK**.

## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań i dyrektyw LINQ

W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie. Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie w projekcie (kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań** i rozwiń węzeł **odwołania** ), Dodaj go, jak wyjaśniono w poniższych krokach.

### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.

     Zestaw zostanie dodany do projektu.

3. W oknie dialogowym **Dodaj odwołanie** kliknij pozycję **.NET**, przewiń do i kliknij pozycję System. Windows. Forms, a następnie kliknij przycisk **OK**.

     Ten zestaw, który obsługuje okno komunikatu w instruktażu, jest dodawany do projektu.

4. Dodaj powyższe `Module1`dyrektywy poniżej:

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Mapowanie klasy do tabeli bazy danych

W tym kroku utworzysz klasę i zamapujesz ją do tabeli bazy danych. Takie klasy są określane jako *Klasa jednostki*. Należy pamiętać, że mapowanie jest realizowane przez jedynie dodanie <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Aby utworzyć klasę jednostki i zamapować ją na tabelę bazy danych

- Wpisz lub wklej następujący kod do Module1. vb bezpośrednio powyżej `Sub Main`:

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Wyznaczanie właściwości klasy do reprezentowania kolumn bazy danych

W tym kroku wykonujesz kilka zadań.

- Użyj <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć `City` `CustomerID` i właściwości klasy Entity jako reprezentujące kolumny w tabeli bazy danych.

- Należy wyznaczyć `CustomerID` Właściwość reprezentującą kolumnę klucza podstawowego w bazie danych.

- `_CustomerID` Wyznaczysz `_City` pola i dla magazynu prywatnego. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]program może następnie przechowywać i pobierać wartości bezpośrednio, zamiast korzystać z publicznych metod dostępu, które mogą zawierać logikę biznesową.

### <a name="to-represent-characteristics-of-two-database-columns"></a>Do reprezentowania cech dwóch kolumn bazy danych

- Wpisz lub wklej następujący kod do Module1. vb tuż przed `End Class`:

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Określanie połączenia z bazą danych Northwind

W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektu, aby nawiązać połączenie między strukturami danych opartymi na kodzie i samą bazą danych. <xref:System.Data.Linq.DataContext> Jest głównym kanałem, za pośrednictwem którego można pobrać obiekty z bazy danych i przesłać zmiany.

Deklarujemy również, `Table(Of Customer)` aby pełnić rolę logicznej, wpisanej tabeli dla zapytań względem tabeli Customers w bazie danych. Te zapytania zostaną utworzone i wykonane w dalszych krokach.

### <a name="to-specify-the-database-connection"></a>Aby określić połączenie z bazą danych

- Wpisz lub wklej następujący kod w `Sub Main` metodzie.

     Należy pamiętać, `northwnd.mdf` że plik jest założono, że znajduje się w folderze linqtest. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a>Tworzenie prostego zapytania

W tym kroku utworzysz zapytanie, aby sprawdzić, którzy klienci w tabeli Klienci bazy danych znajdują się w Londynie. Kod zapytania w tym kroku tylko opisuje zapytanie. Nie wykonuje go. Takie podejście jest znane jako *odroczone wykonanie*. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Utworzysz również dane wyjściowe dziennika w celu wyświetlenia poleceń SQL, które [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generują. Ta funkcja rejestrowania (która korzysta <xref:System.Data.Linq.DataContext.Log%2A>z programu) jest przydatna podczas debugowania, a przy określaniu, że polecenia wysyłane do bazy danych dokładnie reprezentują zapytanie.

### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie

- Wpisz lub wklej następujący kod do `Sub Main` metody `Table(Of Customer)` po deklaracji:

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a>Wykonywanie zapytania

W tym kroku rzeczywiście wykonujesz zapytanie. Wyrażenia zapytania utworzone w poprzednich krokach nie są oceniane do momentu, gdy będą potrzebne wyniki. Po rozpoczęciu `For Each` iteracji polecenie SQL jest wykonywane względem bazy danych, a obiekty są w materiałach.

### <a name="to-execute-the-query"></a>Aby wykonać zapytanie

1. Wpisz lub wklej następujący kod na końcu `Sub Main` metody (po opisie zapytania):

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. Naciśnij klawisz F5, aby debugować aplikację.

    > [!NOTE]
    > Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów w temacie [uczenie się według przewodników](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).

     W oknie komunikatu zostanie wyświetlona lista sześciu klientów. W oknie konsoli jest wyświetlany wygenerowany kod SQL.

3. Kliknij przycisk **OK** , aby odrzucić okno komunikatu.

     Aplikacja zostanie zamknięta.

4. Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.

     Ta aplikacja będzie potrzebna w przypadku kontynuowania następnego przewodnika.

## <a name="next-steps"></a>Następne kroki

[Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) ) tematu kontynuuje się w przypadku zakończenia tego przewodnika. Instruktaż dotyczący wykonywania zapytań w relacjach [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokazuje, jak można wykonywać zapytania między tabelami, podobnie jak w przypadku *sprzężeń* w relacyjnej bazie danych.

Jeśli chcesz wykonać zapytania dotyczące instrukcji dotyczących relacji, pamiętaj, aby zapisać rozwiązanie dla przewodnika, który właśnie został ukończony, co jest wymaganiem wstępnym.

## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
