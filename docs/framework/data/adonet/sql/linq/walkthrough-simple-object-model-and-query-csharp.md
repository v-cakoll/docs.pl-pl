---
title: "Wskazówki: Prosty Model obiektów i kwerendy (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 444692cb035d97b0fe57c1ea9ba7802491ca2160
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>Wskazówki: Prosty Model obiektów i kwerendy (C#)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza z minimalnym złożoności. Utworzy klasę jednostki, która modele tabeli klientów Northwind przykładowej bazy danych. Spowoduje to utworzenie prostego zapytania do listy klientów, którzy znajdują się w Londynie.  
  
 Ten przewodnik jest zorientowany kodu zgodnie z projektem, aby ułatwić Pokaż [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pojęcia. Zwykle rzecz biorąc, należy użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do utworzenia obiektu modelu.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest5") do przechowywania plików. Utwórz ten folder przed rozpoczęciem przewodnika.  
  
-   W tym przewodniku wymaga przykładowej bazy danych Northwind. Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik do folderu c:\linqtest5.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik obejmuje sześć głównych zadań:  
  
-   Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Mapowania klasy tabeli bazy danych.  
  
-   Wyznaczenie właściwości klasy do reprezentowania kolumnach bazy danych.  
  
-   Określanie połączenia z bazą danych Northwind.  
  
-   Tworzenie prostego zapytania do bazy danych.  
  
-   Wykonywanie zapytania i obserwowania wyniki.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie składnika LINQ to SQL rozwiązania  
 W tym zadaniu pierwszym utworzeniu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] rozwiązania zawierającego niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć składnika LINQ to SQL rozwiązania  
  
1.  Na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **typy projektów** okienku **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#**.  
  
3.  W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz **LinqConsoleApp**.  
  
5.  W **lokalizacji** upewnij się, którym chcesz przechowywać pliki projektu.  
  
6.  Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań LINQ i dyrektywy  
 W tym przewodniku zastosowano zestawy, które nie mogą być instalowane domyślnie w projekcie. Jeśli System.Data.Linq nie jest wymieniony jako odwołanie do projektu (rozwiń **odwołania** w węźle **Eksploratora rozwiązań**), dodaj ją, zgodnie z objaśnieniem w poniższych krokach.  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3.  Dodaj następujące dyrektywy w górnej części **Program.cs**:  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mapowanie klasę do tabeli bazy danych  
 W tym kroku Utwórz klasę i mapowanie go do tabeli bazy danych. Taka klasa jest określane jako *klasy jednostka*. Należy pamiętać, że mapowanie odbywa się po prostu dodając <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Aby utworzyć klasę jednostki i mapowanie go do tabeli bazy danych  
  
-   Wpisz lub wklej następujący kod do pliku Program.cs bezpośrednio nad `Program` deklaracji klasy:  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Wyznaczenie właściwości klasy do reprezentowania kolumnach bazy danych  
 W tym kroku należy wykonać kilka zadań.  
  
-   Możesz użyć <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybut do wyznaczenia `CustomerID` i `City` właściwości w obiekcie klasy reprezentujące kolumn w tabeli bazy danych.  
  
-   Możesz określić `CustomerID` właściwość jako kolumna klucza podstawowego w bazie danych.  
  
-   Możesz określić `_CustomerID` i `_City` pól dla prywatnych magazynu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]można następnie przechowywać i pobierać wartości bezpośrednio, zamiast metody dostępu publicznego, które może obejmować logiki biznesowej.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>Do reprezentowania właściwości dwie kolumny bazy danych  
  
-   Wpisz lub wklej następujący kod do pliku Program.cs wewnątrz nawiasów klamrowych dla `Customer` klasy.  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Określanie połączenia z bazą danych Northwind  
 W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektu do nawiązywania połączenia między struktury kodu na podstawie danych użytkownika i bazy danych. <xref:System.Data.Linq.DataContext> Jest głównym kanału, za pomocą którego możesz pobrać obiektów z bazy danych i przesyłanie zmian.  
  
 Deklarować także `Table<Customer>` do działania jako logiczne, typu tabeli dla zapytań względem tabeli klientów w bazie danych. Utworzysz i wykonaj następujące kwerendy w kolejnych krokach.  
  
#### <a name="to-specify-the-database-connection"></a>Aby określić połączenie z bazą danych  
  
-   Wpisz lub wklej następujący kod do `Main` metody.  
  
     Należy pamiętać, że `northwnd.mdf` pliku zakłada, że w folderze linqtest5. Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a>Tworzenie prostego zapytania  
 W tym kroku możesz utworzyć zapytanie w celu określenia, którzy klienci tabeli bazy danych znajdują się w Londynie. Kod zapytania w tym kroku opisano tylko zapytania. Nie wykonać go. Takie podejście jest nazywany *odroczonego wykonania*. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Należy również produktów wyjściowych dziennika do wyświetlenia SQL polecenia, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje. Ta funkcja rejestrowania (który korzysta z <xref:System.Data.Linq.DataContext.Log%2A>) jest przydatne w debugowaniu i w określeniu, czy polecenia wysyłane do bazy danych dokładnie reprezentować zapytania.  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
-   Wpisz lub wklej następujący kod do `Main` metody po `Table<Customer>` deklaracji.  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a>Wykonywanie zapytania  
 W tym kroku faktycznie wykonać zapytanie. Wyrażenia zapytań, utworzone w poprzednich krokach nie są oceniane, dopóki wyniki są potrzebne. Jeśli rozpoczniesz `foreach` iteracji, wykonywania polecenia SQL z bazą danych i obiektów jest zmaterializowany.  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1.  Wpisz lub wklej następujący kod na końcu `Main` — metoda (po opis kwerendy).  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  Naciśnij klawisz F5, aby debugować aplikację.  
  
    > [!NOTE]
    >  Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów z [uczenia przez wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     Wyniki zapytania w oknie konsoli powinna wyglądać następująco:  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  Naciśnij klawisz Enter w oknie konsoli, aby zamknąć aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 [Wskazówki: wykonywanie zapytania na relacje (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) temat będzie kontynuowane, gdy kończy się w tym przewodniku. Przedstawia wskazówki zapytania w relacji jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można zbadać między tabelami, podobnie jak *sprzężenia* relacyjnej bazy danych.  
  
 Jeśli chcesz wykonać wskazówki zapytania w relacji, upewnij się zapisać rozwiązanie, aby uzyskać wskazówki, który właśnie został ukończony, które jest wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
