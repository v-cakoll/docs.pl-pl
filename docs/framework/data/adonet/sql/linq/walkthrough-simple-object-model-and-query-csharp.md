---
title: 'Przewodnik: Prosty Model obiektu i zapytanie (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 25e23b77f6f5547a5516c6db240537cb00685edc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686871"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>Przewodnik: Prosty Model obiektu i zapytanie (C#)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza minimalnej złożoności. Utworzy klasę jednostki, który modeluje tabelę Klienci w przykładowej bazie danych Northwind. Spowoduje to utworzenie prostego zapytania do listy klientów, którzy znajdują się w Londynie.  
  
 Ten przewodnik jest zorientowany kodu zgodnie z projektem, aby ułatwić wyświetlanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pojęcia. Zwykle rzecz biorąc, należy użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia modelu obiektu.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu Visual C# ustawieniami środowiska deweloperskiego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   W tym przewodniku używa dedykowanego folder ("c:\linqtest5") do przechowywania plików. Przed rozpoczęciem instruktażu, należy utworzyć ten folder.  
  
-   Ten poradnik wymaga przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik do folderu c:\linqtest5.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z sześciu głównych zadań:  
  
-   Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.  
  
-   Mapowanie klasy do tabeli bazy danych.  
  
-   Wyznaczanie właściwości klasy do reprezentowania kolumny bazy danych.  
  
-   Określenie połączenia z bazą danych Northwind.  
  
-   Tworzenie prostego zapytania do bazy danych.  
  
-   Wykonywanie zapytania i obserwowania wyniki.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie składnika LINQ to SQL rozwiązanie  
 W tym pierwszym zadaniu tworzyć rozwiązania programu Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć składnika LINQ to SQL rozwiązanie  
  
1.  W programie Visual Studio **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2.  W **typów projektów** okienku **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** .  
  
3.  W **szablony** okienku kliknij **aplikację Konsolową**.  
  
4.  W **nazwa** wpisz **LinqConsoleApp**.  
  
5.  W **lokalizacji** upewnij się, którym chcesz przechowywać swoje pliki projektu.  
  
6.  Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołania do zapytań LINQ i dyrektywy  
 W tym instruktażu wykorzystano zestawów, które nie mogą być instalowane domyślnie w projekcie. Jeśli System.Data.Linq nie jest wymieniony jako odwołanie w projekcie (rozwiń **odwołania** w węźle **Eksploratora rozwiązań**), ją dodać, zgodnie z opisem w poniższych krokach.  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3.  Dodaj następujące dyrektywy w górnej części **Program.cs**:  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mapowanie klasy do tabeli bazy danych  
 W tym kroku, Utwórz klasę i mapowany do tabeli bazy danych. Taka klasa jest określane jako *Klasa jednostki*. Należy pamiętać, że mapowanie odbywa się przez dodanie <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Aby utworzyć klasę jednostki i mapowany do tabeli bazy danych  
  
-   Wpisz lub wklej następujący kod do pliku Program.cs bezpośrednio nad `Program` deklaracji klasy:  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Wyznaczanie właściwości klasy do reprezentowania kolumny bazy danych  
 W tym kroku należy wykonać kilka zadań.  
  
-   Możesz użyć <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć `CustomerID` i `City` właściwości jednostki klasy, reprezentując kolumn w tabeli bazy danych.  
  
-   Możesz wyznaczyć `CustomerID` właściwości jako kolumna klucza podstawowego w bazie danych.  
  
-   Możesz wyznaczyć `_CustomerID` i `_City` pól magazynu prywatnego. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można następnie przechowywać i pobierać wartości bezpośrednio, zamiast publiczne metody dostępu, które mogą obejmować logiki biznesowej.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>Do reprezentowania charakterystyki dwie kolumny bazy danych  
  
-   Wpisz lub wklej następujący kod do pliku Program.cs wewnątrz nawiasów klamrowych dla `Customer` klasy.  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Określanie połączenia z bazą danych Northwind  
 W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektów do nawiązania połączenia między struktury danych w oparciu o kod użytkownika, a sama baza danych. <xref:System.Data.Linq.DataContext> Jest głównym kanał za pomocą którego pobieranie obiektów z bazy danych i przesyłanie zmian.  
  
 Można również zadeklarować `Table<Customer>` pełnić rolę w logiczne, wpisane tabeli zapytania względem tabeli Klienci w bazie danych. Utworzysz i wykonaj następujące zapytania w kolejnych krokach.  
  
#### <a name="to-specify-the-database-connection"></a>Aby określić połączenie z bazą danych  
  
-   Wpisz lub wklej następujący kod do `Main` metody.  
  
     Należy pamiętać, że `northwnd.mdf` pliku zakłada, że w folderze linqtest5. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a>Tworzenie prostego zapytania  
 W tym kroku utworzysz zapytanie w celu określenia, których klientów w tabeli Klienci bazy danych znajdują się w Londynie. Kod zapytania w tym kroku opisano tylko zapytania. Nie wykonuje on. To podejście jest nazywane *wykonanie odroczone*. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Należy również wygenerować dziennika danych wyjściowych do wyświetlenia SQL polecenia, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje. Ta funkcja rejestrowania (wykonującemu <xref:System.Data.Linq.DataContext.Log%2A>) jest przydatne podczas debugowania i określenie, że polecenia są wysyłane do bazy danych, dokładnie reprezentują zapytanie.  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
-   Wpisz lub wklej następujący kod do `Main` metody `Table<Customer>` deklaracji.  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a>Wykonywanie zapytania  
 W tym kroku faktycznie wykonaj zapytanie. Wyrażenia zapytań, który został utworzony w poprzednich krokach nie są oceniane, dopóki wyniki są potrzebne. Po rozpoczęciu `foreach` iteracji, za pomocą polecenia SQL jest wykonywane względem bazy danych i obiektów jest zmaterializowany.  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1.  Wpisz lub wklej następujący kod na końcu `Main` metody (opis kwerendy).  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  Naciśnij klawisz F5, aby debugować aplikację.  
  
    > [!NOTE]
    >  Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów z [nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     Wyniki zapytania w oknie konsoli powinna wyglądać następująco:  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  Naciśnij klawisz Enter w oknie konsoli, aby zamknąć aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 [Instruktażu: Relacje między querying (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) tematu będzie kontynuowane, gdy kończy się w tym przewodniku. Instruktaż zapytań w relacjach demonstruje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można wykonywanie zapytań względem tabel, podobnie jak *sprzężeń* relacyjnej bazy danych.  
  
 Jeśli chcesz wykonać instrukcje przedstawione zapytań w relacjach, upewnij się zapisać rozwiązanie przewodnik, który właśnie został ukończony, który jest wymaganiem wstępnym.  
  
## <a name="see-also"></a>Zobacz także
- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
