---
title: "Wskazówki: Prosty Model obiektów i zapytanie (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed6436dcac1791d735132c295943519af36e307d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>Wskazówki: Prosty Model obiektów i zapytanie (Visual Basic)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza z minimalnym złożoności. Utworzy klasę jednostki, która modele tabeli klientów Northwind przykładowej bazy danych. Spowoduje to utworzenie prostego zapytania do listy klientów, którzy znajdują się w Londynie.  
  
 Ten przewodnik jest zorientowany kodu zgodnie z projektem, aby ułatwić Pokaż [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pojęcia. Zwykle rzecz biorąc, należy użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do utworzenia obiektu modelu.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu ustawienia środowiska deweloperskiego Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest") do przechowywania plików. Utwórz ten folder przed rozpoczęciem przewodnika.  
  
-   W tym przewodniku wymaga przykładowej bazy danych Northwind. Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik do folderu c:\linqtest.  
  
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
  
1.  Na **pliku** menu, kliknij przycisk **nowy projekt**.  
  
2.  W **typy projektów** okienku **nowy projekt** okno dialogowe, kliknij przycisk **Visual Basic**.  
  
3.  W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz **LinqConsoleApp**.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań LINQ i dyrektywy  
 W tym przewodniku zastosowano zestawy, które nie mogą być instalowane domyślnie w projekcie. Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie do projektu (kliknij **Pokaż wszystkie pliki** w **Eksploratora rozwiązań** i rozwiń **odwołania** węzła), dodaj ją, zgodnie z objaśnieniem w Poniższe kroki.  
  
#### <a name="to-add-systemdatalinq"></a>Aby dodać System.Data.Linq  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3.  Również w **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**przewiń i kliknij przycisk System.Windows.Forms, a następnie kliknij **OK**.  
  
     Ten zestaw, który obsługuje pola wiadomości instruktażem, zostanie dodany do projektu.  
  
4.  Dodaj następujące dyrektywy powyżej `Module1`:  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mapowanie klasę do tabeli bazy danych  
 W tym kroku Utwórz klasę i mapowanie go do tabeli bazy danych. Taka klasa jest określane jako *klasy jednostka*. Należy pamiętać, że mapowanie odbywa się po prostu dodając <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Aby utworzyć klasę jednostki i mapowanie go do tabeli bazy danych  
  
-   Wpisz lub wklej następujący kod do Module1.vb bezpośrednio nad `Sub Main`:  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Wyznaczenie właściwości klasy do reprezentowania kolumnach bazy danych  
 W tym kroku należy wykonać kilka zadań.  
  
-   Możesz użyć <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybut do wyznaczenia `CustomerID` i `City` właściwości w obiekcie klasy reprezentujące kolumn w tabeli bazy danych.  
  
-   Możesz określić `CustomerID` właściwość jako kolumna klucza podstawowego w bazie danych.  
  
-   Możesz określić `_CustomerID` i `_City` pól dla prywatnych magazynu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]można następnie przechowywać i pobierać wartości bezpośrednio, zamiast metody dostępu publicznego, które może obejmować logiki biznesowej.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>Do reprezentowania właściwości dwie kolumny bazy danych  
  
-   Wpisz lub wklej następujący kod do Module1.vb tuż przed `End Class`:  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Określanie połączenia z bazą danych Northwind  
 W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektu do nawiązywania połączenia między struktury kodu na podstawie danych użytkownika i bazy danych. <xref:System.Data.Linq.DataContext> Jest głównym kanału, za pomocą którego możesz pobrać obiektów z bazy danych i przesyłanie zmian.  
  
 Deklarować także `Table(Of Customer)` do działania jako logiczne, typu tabeli dla zapytań względem tabeli klientów w bazie danych. Utworzysz i wykonaj następujące kwerendy w kolejnych krokach.  
  
#### <a name="to-specify-the-database-connection"></a>Aby określić połączenie z bazą danych  
  
-   Wpisz lub wklej następujący kod do `Sub Main` metody.  
  
     Należy pamiętać, że `northwnd.mdf` pliku zakłada, że w folderze linqtest. Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a>Tworzenie prostego zapytania  
 W tym kroku możesz utworzyć zapytanie w celu określenia, którzy klienci tabeli bazy danych znajdują się w Londynie. Kod zapytania w tym kroku opisano tylko zapytania. Nie wykonać go. Takie podejście jest nazywany *odroczonego wykonania*. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Należy również produktów wyjściowych dziennika do wyświetlenia SQL polecenia, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje. Ta funkcja rejestrowania (który korzysta z <xref:System.Data.Linq.DataContext.Log%2A>) jest przydatne w debugowaniu i w określeniu, czy polecenia wysyłane do bazy danych dokładnie reprezentować zapytania.  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
-   Wpisz lub wklej następujący kod do `Sub Main` metody po `Table(Of Customer)` deklaracji:  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a>Wykonywanie zapytania  
 W tym kroku faktycznie wykonać zapytanie. Wyrażenia zapytań, utworzone w poprzednich krokach nie są oceniane, dopóki wyniki są potrzebne. Jeśli rozpoczniesz `For Each` iteracji, wykonywania polecenia SQL z bazą danych i obiektów jest zmaterializowany.  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1.  Wpisz lub wklej następujący kod na końcu `Sub Main` — metoda (po opisu zapytania):  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2.  Naciśnij klawisz F5, aby debugować aplikację.  
  
    > [!NOTE]
    >  Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów z [uczenia przez wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     W oknie komunikatu Wyświetla listę klientów sześć. W oknie konsoli Wyświetla wygenerowanego kodu SQL.  
  
3.  Kliknij przycisk **OK** aby zamknąć okno komunikatu.  
  
     Zamyka aplikację.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
     Jeśli będziesz kontynuować z przewodnikiem dalej należy tej aplikacji.  
  
## <a name="next-steps"></a>Następne kroki  
 [Wskazówki: wykonywanie zapytania na relacje (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) temat będzie kontynuowane, gdy kończy się w tym przewodniku. Przedstawiono wskazówki zapytań w relacjach jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można zbadać między tabelami, podobnie jak *sprzężenia* relacyjnej bazy danych.  
  
 Jeśli chcesz wykonać wskazówki zapytań w relacji, upewnij się zapisać rozwiązanie, aby uzyskać wskazówki, który właśnie został ukończony, które jest wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Learning przez — wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
