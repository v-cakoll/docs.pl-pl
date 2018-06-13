---
title: 'Wskazówki: Manipulowanie danych (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: b9b19d4f9a1fb56ddabbf3584c1fb7bb29cd6d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357663"
---
# <a name="walkthrough-manipulating-data-c"></a>Wskazówki: Manipulowanie danych (C#)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza Dodawanie, modyfikowanie i usuwanie danych z bazy danych. Aby dodać klienta, Zmień nazwę klienta i usunąć zamówienie będzie używał kopii przykładowej bazy danych Northwind.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku wymaga następujących elementów:  
  
-   W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest6") do przechowywania plików. Utwórz ten folder przed rozpoczęciem przewodnika.  
  
-   Przykładowa bazy danych Northwind.  
  
     Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest6.  
  
-   Plik kodu C# wygenerowany z bazy danych Northwind.  
  
     Ten plik można wygenerować za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub narzędzie SQLMetal. W tym przewodniku została napisana przy użyciu narzędzia SQLMetal z następującego polecenia:  
  
     **sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" / pluralize**  
  
     Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik obejmuje sześć głównych zadań:  
  
-   Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.  
  
-   Dodawanie plików kodu bazy danych do projektu.  
  
-   Tworzenie nowego obiektu klienta.  
  
-   Modyfikowanie nazwę kontaktu klienta.  
  
-   Usuwanie zamówienia.  
  
-   Przesyłanie te zmiany do bazy danych Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie składnika LINQ to SQL rozwiązania  
 W tym zadaniu pierwszego tworzenia rozwiązania Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć składnika LINQ to SQL rozwiązania  
  
1.  W programie Visual Studio **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **typy projektów** okienka w **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#**.  
  
3.  W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz **LinqDataManipulationApp**.  
  
5.  W **lokalizacji** upewnij się, którym chcesz przechowywać pliki projektu.  
  
6.  Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań LINQ i dyrektywy  
 W tym przewodniku zastosowano zestawy, które nie mogą być instalowane domyślnie w projekcie. Jeśli System.Data.Linq nie jest wymieniony jako odwołanie do projektu, dodaj ją, zgodnie z objaśnieniem w poniższych krokach:  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3.  Dodaj następujące dyrektywy na początku pliku Program.cs:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie plików kodu Northwind do projektu  
 Tych krokach przyjęto założenie, aby wygenerować plik kodu z przykładowej bazy danych Northwind użycie narzędzia SQLMetal. Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu northwind do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
2.  W **Dodaj istniejący element** okno dialogowe, przejdź do c:\linqtest6\northwind.cs, a następnie kliknij przycisk **Dodaj**.  
  
     Plik northwind.cs zostanie dodany do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Trwa konfigurowanie połączenia z bazą danych  
 Najpierw należy przetestować połączenie z bazą danych. Szczególnie Pamiętaj, że bazy danych, Northwnd, nie ma żadnych i znak. Jeśli generować błędy w następnych krokach, przejrzyj plik northwind.cs ustalenie, jak została wpisana Northwind klasy częściowej.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Aby skonfigurować i przetestować połączenie z bazą danych  
  
1.  Wpisz lub wklej następujący kod do `Main` metody w klasie Program:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  Naciśnij klawisz F5, aby przetestować aplikację na tym etapie.  
  
     A **konsoli** zostanie otwarte okno.  
  
     Możesz zamknąć aplikację, naciskając klawisz Enter w **konsoli** okna, lub przez kliknięcie przycisku **Zatrzymaj debugowanie** w programie Visual Studio **debugowania** menu.  
  
## <a name="creating-a-new-entity"></a>Tworzenie nowej jednostki  
 Tworzenie nowej jednostki jest prosta. Można utworzyć obiektów (takich jak `Customer`) przy użyciu `new` — słowo kluczowe.  
  
 W tym i sekcje wprowadzania zmian tylko do lokalnej pamięci podręcznej. Żadne zmiany nie są wysyłane do bazy danych do czasu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> do końca tego przewodnika.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Aby dodać nowy obiekt jednostki klienta  
  
1.  Utwórz nową `Customer` przez dodanie poniższego kodu przed `Console.ReadLine();` w `Main` metody:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  Naciśnij klawisz F5, aby debugować rozwiązania.  
  
3.  Naciśnij klawisz Enter w **konsoli** okno, aby zatrzymać debugowanie i kontynuować przewodnika.  
  
## <a name="updating-an-entity"></a>Aktualizowanie jednostki  
 W poniższych krokach będą pobierane `Customer` obiektów i zmodyfikować jednej z jego właściwości.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Aby zmienić nazwę klienta  
  
-   Dodaj następujący kod powyżej `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Usuwanie jednostki  
 Przy użyciu tego samego obiektu klienta, możesz usunąć pierwszej kolejności.  
  
 Poniższy kod przedstawia sposób sever relacje między wierszami i sposobu usunięcia wiersza z bazy danych. Dodaj następujący kod przed `Console.ReadLine` aby zobaczyć, jak obiekty zostaną usunięte:  
  
#### <a name="to-delete-a-row"></a>Aby usunąć wiersz  
  
-   Dodaj następujący kod po prostu powyżej `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Przesyłanie zmian w bazie danych  
 Ostatni krok wymagany do tworzenia, aktualizowania i usuwania obiektów, jest rzeczywiście przesłać zmiany w bazie danych. Bez tego kroku zmiany są tylko lokalne i nie będą widoczne w wynikach zapytania.  
  
#### <a name="to-submit-changes-to-the-database"></a>Aby przesłać zmiany w bazie danych  
  
1.  Wstaw poniższy kod nad `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  Wstaw następujący kod (po `SubmitChanges`) do wyświetlenia przed i po skutków przesyłanie zmian:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  Naciśnij klawisz F5, aby debugować rozwiązania.  
  
4.  Naciśnij klawisz Enter w **konsoli** okno, aby zamknąć aplikację.  
  
> [!NOTE]
>  Po dodaniu nowego klienta, przesyłając zmiany, nie można wykonać tego rozwiązania jest ponownie. Aby wykonać ponownie rozwiązanie, Zmień nazwę klienta i identyfikator klienta, które ma zostać dodana.  
  
## <a name="see-also"></a>Zobacz też  
 [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
