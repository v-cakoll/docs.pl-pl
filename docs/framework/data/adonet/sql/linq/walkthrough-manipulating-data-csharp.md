---
title: 'Przewodnik: Manipulowanie danymi (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 5418bdbdeee162bbc8c0abcb11fd39f2cc82ce73
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330782"
---
# <a name="walkthrough-manipulating-data-c"></a>Przewodnik: Manipulowanie danymi (C#)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz dotyczący dodawania, modyfikowania i usuwania danych w bazie danych. Kopię przykładowej bazy danych Northwind użyje do dodawania klienta, Zmień nazwę klienta i usunąć zamówienie.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu Visual C# ustawieniami środowiska deweloperskiego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik wymaga następujących elementów:  
  
-   W tym przewodniku używa dedykowanego folder ("c:\linqtest6") do przechowywania plików. Przed rozpoczęciem instruktażu, należy utworzyć ten folder.  
  
-   Przykładowa bazy danych Northwind.  
  
     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest6.  
  
-   A C# plik kod wygenerowany z bazy danych Northwind.  
  
     Ten plik można wygenerować za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub narzędzia SQLMetal. Ten instruktaż został napisany za pomocą narzędzia SQLMetal za pomocą następującego polecenia:  
  
     **Program sqlmetal /code:"c:\linqtest6\northwind.cs" / Language: CSharp "C:\linqtest6\northwnd.mdf" / pluralize**  
  
     Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z sześciu głównych zadań:  
  
-   Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.  
  
-   Dodawanie pliku kodu bazy danych do projektu.  
  
-   Tworzenie nowego obiektu klienta.  
  
-   Modyfikowanie nazwa kontaktu klienta.  
  
-   Usuwanie zamówienia.  
  
-   Przesyłanie tych zmian w bazie danych Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie składnika LINQ to SQL rozwiązanie  
 W tym pierwszym zadaniu tworzyć rozwiązania programu Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć składnika LINQ to SQL rozwiązanie  
  
1. W programie Visual Studio **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2. W **typów projektów** okienka **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** .  
  
3. W **szablony** okienku kliknij **aplikację Konsolową**.  
  
4. W **nazwa** wpisz **LinqDataManipulationApp**.  
  
5. W **lokalizacji** upewnij się, którym chcesz przechowywać swoje pliki projektu.  
  
6. Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołania do zapytań LINQ i dyrektywy  
 W tym instruktażu wykorzystano zestawów, które nie mogą być instalowane domyślnie w projekcie. Jeśli System.Data.Linq nie jest wymieniony jako odwołanie w projekcie, należy dodać ją, zgodnie z opisem w poniższych krokach:  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3. Dodaj następujące dyrektywy, w górnej części pliku Program.cs:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie pliku Northwind kodu do projektu  
 Te czynności zakładają, że trzeba użyć narzędzia SQLMetal do generowania pliku kodu z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu northwind do projektu  
  
1. Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
2. W **Dodaj istniejący element** okno dialogowe, przejdź do c:\linqtest6\northwind.cs, a następnie kliknij przycisk **Dodaj**.  
  
     Plik northwind.cs zostanie dodany do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Konfigurowanie połączenia z bazą danych  
 Najpierw Przetestuj połączenie z bazą danych. Zwróć uwagę szczególnie, że bazy danych, Northwnd, zawiera i nie znak. Jeśli użytkownik generuje błędy w następnych krokach, przejrzyj plik northwind.cs, aby określić, jak została wpisana klasy częściowej Northwind.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Aby skonfigurować i przetestować połączenie z bazą danych  
  
1. Wpisz lub wklej następujący kod do `Main` metody w klasie Program:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. Naciśnij klawisz F5, aby przetestować aplikację na tym etapie.  
  
     A **konsoli** zostanie otwarte okno.  
  
     Możesz zamknąć aplikację, naciskając klawisz Enter w **konsoli** okna, lub przez kliknięcie przycisku **Zatrzymaj debugowanie** w programie Visual Studio **debugowania** menu.  
  
## <a name="creating-a-new-entity"></a>Tworzenie nowej jednostki  
 Tworzenie nowej jednostki jest bardzo proste. Możesz tworzyć obiekty (takie jak `Customer`) przy użyciu `new` — słowo kluczowe.  
  
 W tym i sekcje w przypadku wprowadzania zmian tylko do lokalnej pamięci podręcznej. Żadne zmiany nie są wysyłane do bazy danych, dopóki nie zostanie wywołana <xref:System.Data.Linq.DataContext.SubmitChanges%2A> pod koniec tego przewodnika.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Aby dodać nowy obiekt jednostki klienta  
  
1. Utwórz nową `Customer` , dodając następujący kod przed `Console.ReadLine();` w `Main` metody:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
3. Naciśnij klawisz Enter w **konsoli** okna, aby zatrzymać debugowanie i kontynuować instruktażu.  
  
## <a name="updating-an-entity"></a>Aktualizowanie jednostki  
 W poniższych krokach będą pobierane `Customer` i zmodyfikować jedną z jej właściwości.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Aby zmienić nazwę klienta  
  
-   Dodaj następujący kod powyżej `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Usuwanie jednostki  
 Przy użyciu tego samego obiektu klienta, możesz usunąć pierwszej kolejności.  
  
 Poniższy kod przedstawia sposób sever relacje między wierszami i jak usunąć wiersz z bazy danych. Dodaj następujący kod przed `Console.ReadLine` aby zobaczyć, jak można usunąć obiektów:  
  
#### <a name="to-delete-a-row"></a>Aby usunąć wiersz  
  
-   Dodaj poniższy kod tuż nad `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Przesyłanie zmian do bazy danych  
 Ostatni krok wymagany do tworzenia, aktualizowania i usuwania obiektów, jest rzeczywiście przesłać zmiany w bazie danych. Bez tego kroku zmiany są tylko lokalne i nie będą widoczne w wynikach kwerendy.  
  
#### <a name="to-submit-changes-to-the-database"></a>Aby przesłać zmiany do bazy danych  
  
1. Wstaw poniższy kod tuż nad `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. Wstaw następujący kod (po `SubmitChanges`) do wyświetlenia przed i po nim skutki przesyłanie zmian:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
4. Naciśnij klawisz Enter w **konsoli** okna, aby zamknąć aplikację.  
  
> [!NOTE]
>  Po dodaniu nowego klienta, przesyłając żądanie zmiany, nie można wykonać tego rozwiązania jest ponownie. Aby wykonać ponownie rozwiązanie, należy zmienić nazwę klienta i identyfikator klienta, które mają zostać dodane.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
