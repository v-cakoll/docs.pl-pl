---
title: 'Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: 326caf550e8b138b4b968f0021a7fc475dc58c8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037014"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza minimalnej złożoności. Utworzy klasę jednostki, który modeluje tabelę Klienci w przykładowej bazie danych Northwind. Spowoduje to utworzenie prostego zapytania do listy klientów, którzy znajdują się w Londynie.  
  
 Ten przewodnik jest zorientowany kodu zgodnie z projektem, aby ułatwić wyświetlanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pojęcia. Zwykle rzecz biorąc, należy użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia modelu obiektu.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu ustawień środowiska deweloperskiego Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- W tym przewodniku używa dedykowanego folder ("c:\linqtest") do przechowywania plików. Przed rozpoczęciem instruktażu, należy utworzyć ten folder.  
  
- Ten poradnik wymaga przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik do folderu c:\linqtest.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z sześciu głównych zadań:  
  
- Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.  
  
- Mapowanie klasy do tabeli bazy danych.  
  
- Wyznaczanie właściwości klasy do reprezentowania kolumny bazy danych.  
  
- Określenie połączenia z bazą danych Northwind.  
  
- Tworzenie prostego zapytania do bazy danych.  
  
- Wykonywanie zapytania i obserwowania wyniki.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie składnika LINQ to SQL rozwiązanie  
 W tym pierwszym zadaniu tworzyć rozwiązania programu Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć składnika LINQ to SQL rozwiązanie  
  
1. Na **pliku** menu, kliknij przycisk **nowy projekt**.  
  
2. W **typów projektów** okienku **nowy projekt** okno dialogowe, kliknij przycisk **języka Visual Basic**.  
  
3. W **szablony** okienku kliknij **aplikację Konsolową**.  
  
4. W **nazwa** wpisz **LinqConsoleApp**.  
  
5. Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołania do zapytań LINQ i dyrektywy  
 W tym instruktażu wykorzystano zestawów, które nie mogą być instalowane domyślnie w projekcie. Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie do projektu (kliknij **Pokaż wszystkie pliki** w **Eksploratora rozwiązań** i rozwiń **odwołania** węzła), ją dodać, jak wyjaśniono w Poniższe kroki.  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3. Również w **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**przewiń i kliknij przestrzeń nazw System.Windows.Forms, a następnie kliknij przycisk **OK**.  
  
     Ten zestaw, który obsługuje okno komunikatu w instruktażu, jest dodawany do projektu.  
  
4. Dodaj następujące dyrektywy powyżej `Module1`:  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mapowanie klasy do tabeli bazy danych  
 W tym kroku, Utwórz klasę i mapowany do tabeli bazy danych. Taka klasa jest określane jako *Klasa jednostki*. Należy pamiętać, że mapowanie odbywa się przez dodanie <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Aby utworzyć klasę jednostki i mapowany do tabeli bazy danych  
  
- Wpisz lub wklej następujący kod bezpośrednio nad Module1.vb `Sub Main`:  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Wyznaczanie właściwości klasy do reprezentowania kolumny bazy danych  
 W tym kroku należy wykonać kilka zadań.  
  
- Możesz użyć <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć `CustomerID` i `City` właściwości jednostki klasy, reprezentując kolumn w tabeli bazy danych.  
  
- Możesz wyznaczyć `CustomerID` właściwości jako kolumna klucza podstawowego w bazie danych.  
  
- Możesz wyznaczyć `_CustomerID` i `_City` pól magazynu prywatnego. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można następnie przechowywać i pobierać wartości bezpośrednio, zamiast publiczne metody dostępu, które mogą obejmować logiki biznesowej.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>Do reprezentowania charakterystyki dwie kolumny bazy danych  
  
- Wpisz lub wklej następujący kod do Module1.vb tuż przed `End Class`:  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Określanie połączenia z bazą danych Northwind  
 W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektów do nawiązania połączenia między struktury danych w oparciu o kod użytkownika, a sama baza danych. <xref:System.Data.Linq.DataContext> Jest głównym kanał za pomocą którego pobieranie obiektów z bazy danych i przesyłanie zmian.  
  
 Można również zadeklarować `Table(Of Customer)` pełnić rolę w logiczne, wpisane tabeli zapytania względem tabeli Klienci w bazie danych. Utworzysz i wykonaj następujące zapytania w kolejnych krokach.  
  
#### <a name="to-specify-the-database-connection"></a>Aby określić połączenie z bazą danych  
  
- Wpisz lub wklej następujący kod do `Sub Main` metody.  
  
     Należy pamiętać, że `northwnd.mdf` pliku zakłada, że w folderze linqtest. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a>Tworzenie prostego zapytania  
 W tym kroku utworzysz zapytanie w celu określenia, których klientów w tabeli Klienci bazy danych znajdują się w Londynie. Kod zapytania w tym kroku opisano tylko zapytania. Nie wykonuje on. To podejście jest nazywane *wykonanie odroczone*. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Należy również wygenerować dziennika danych wyjściowych do wyświetlenia SQL polecenia, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje. Ta funkcja rejestrowania (wykonującemu <xref:System.Data.Linq.DataContext.Log%2A>) jest przydatne podczas debugowania i określenie, że polecenia są wysyłane do bazy danych, dokładnie reprezentują zapytanie.  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
- Wpisz lub wklej następujący kod do `Sub Main` metody `Table(Of Customer)` deklaracji:  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a>Wykonywanie zapytania  
 W tym kroku faktycznie wykonaj zapytanie. Wyrażenia zapytań, który został utworzony w poprzednich krokach nie są oceniane, dopóki wyniki są potrzebne. Po rozpoczęciu `For Each` iteracji, za pomocą polecenia SQL jest wykonywane względem bazy danych i obiektów jest zmaterializowany.  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1. Wpisz lub wklej następujący kod na końcu `Sub Main` metody (opis kwerendy):  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2. Naciśnij klawisz F5, aby debugować aplikację.  
  
    > [!NOTE]
    >  Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów z [nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     W oknie komunikatu Wyświetla listę sześcioma klientami. W oknie konsoli zostaną wyświetlone wygenerowanego kodu SQL.  
  
3. Kliknij przycisk **OK** aby odrzucić okno komunikatu.  
  
     Zamyka aplikację.  
  
4. Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
     Należy tej aplikacji, jeśli będziesz korzystać z poniższych wskazówek.  
  
## <a name="next-steps"></a>Następne kroki  
 [Instruktażu: Querying w relacjach (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) tematu będzie kontynuowane, gdy kończy się w tym przewodniku. Wykonywanie zapytań w relacjach instruktażu pokazano, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można wykonywanie zapytań względem tabel, podobnie jak *sprzężeń* relacyjnej bazy danych.  
  
 Jeśli chcesz wykonać instrukcje przedstawione zapytań w relacjach, upewnij się zapisać rozwiązanie przewodnik, który właśnie został ukończony, który jest wymaganiem wstępnym.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
