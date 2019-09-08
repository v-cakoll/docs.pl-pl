---
title: 'Przewodnik: Manipulowanie danymi (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 8941ac30a67406346e5448ca5af4af8512d168a8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781006"
---
# <a name="walkthrough-manipulating-data-c"></a>Przewodnik: Manipulowanie danymi (C#)
Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz służący do dodawania, modyfikowania i usuwania danych w bazie danych. Zostanie użyta kopia przykładowej bazy danych Northwind, aby dodać klienta, zmienić nazwę klienta i usunąć zamówienie.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik wymaga następujących czynności:  
  
- W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest6"). Utwórz ten folder przed rozpoczęciem przewodnika.  
  
- Przykładowa bazy danych Northwind.  
  
     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md). Po pobraniu bazy danych Skopiuj plik northwnd. mdf do folderu c:\linqtest6.  
  
- Plik C# kodu wygenerowany na podstawie bazy danych Northwind.  
  
     Ten plik można wygenerować przy użyciu Object Relational Designer lub narzędzia SQLMetal. Ten Instruktaż został zapisany przy użyciu narzędzia SQLMetal z następującym wierszem polecenia:  
  
     **SQLMetal/Code: "c:\linqtest6\northwind.cs"/Language: CSharp "C:\linqtest6\northwnd.mdf"/pluralize**  
  
     Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z sześciu głównych zadań:  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tworzenie rozwiązania w programie Visual Studio.  
  
- Dodawanie pliku kodu bazy danych do projektu.  
  
- Tworzenie nowego obiektu klienta.  
  
- Modyfikowanie nazwy kontaktu klienta.  
  
- Usuwanie zamówienia.  
  
- Przesyłanie tych zmian do bazy danych Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie rozwiązania LINQ to SQL  
 W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć rozwiązanie LINQ to SQL  
  
1. W menu **plik** programu Visual Studio wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.  
  
2. W okienku **typy projektów** okna dialogowego **Nowy projekt** kliknij pozycję **Wizualizacja C#** .  
  
3. W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.  
  
4. W polu **Nazwa** wpisz **LinqDataManipulationApp**.  
  
5. W polu **Lokalizacja** Sprawdź, gdzie mają być przechowywane pliki projektu.  
  
6. Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań i dyrektyw LINQ  
 W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie. Jeśli element System. Data. LINQ nie jest wymieniony jako odwołanie w projekcie, Dodaj go, jak wyjaśniono w następujących krokach:  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.  
  
2. W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.  
  
     Zestaw zostanie dodany do projektu.  
  
3. Dodaj następujące dyrektywy w górnej części Program.cs:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie pliku kodu Northwind do projektu  
 W tych krokach przyjęto założenie, że użyto narzędzia SQLMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu Northwind do projektu  
  
1. W menu **projekt** kliknij polecenie **Dodaj istniejący element**.  
  
2. W oknie dialogowym **Dodaj istniejący element** przejdź do c:\linqtest6\northwind.cs, a następnie kliknij przycisk **Dodaj**.  
  
     Plik northwind.cs jest dodawany do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Konfigurowanie połączenia z bazą danych  
 Najpierw Przetestuj połączenie z bazą danych. Należy pamiętać, że w szczególności baza danych, northwnd, nie ma znaku. W przypadku wygenerowania błędów w następnych krokach przejrzyj plik northwind.cs, aby określić, w jaki sposób jest sprawdzana pisownia klasy częściowej Northwind.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Aby skonfigurować i przetestować połączenie z bazą danych  
  
1. Wpisz lub wklej następujący kod do `Main` metody w klasie program:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. Naciśnij klawisz F5, aby przetestować aplikację w tym momencie.  
  
     Zostanie otwarte okno **konsoli** .  
  
     Możesz zamknąć aplikację, naciskając klawisz ENTER w oknie **konsoli** lub klikając przycisk **Zatrzymaj debugowanie** w menu **debugowanie** programu Visual Studio.  
  
## <a name="creating-a-new-entity"></a>Tworzenie nowej jednostki  
 Tworzenie nowej jednostki jest proste. Możesz tworzyć obiekty (na przykład `Customer`) za `new` pomocą słowa kluczowego.  
  
 W tym i w poniższych sekcjach wprowadzasz zmiany tylko do lokalnej pamięci podręcznej. Żadne zmiany nie są wysyłane do bazy danych do momentu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> końca tego przewodnika.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Aby dodać nowy obiekt jednostki klienta  
  
1. Utwórz nowy `Customer` , dodając następujący kod przed użyciem `Console.ReadLine();` `Main` metody:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
3. Naciśnij klawisz ENTER w oknie **konsoli** , aby zatrzymać debugowanie i kontynuować przewodnik.  
  
## <a name="updating-an-entity"></a>Aktualizowanie jednostki  
 W poniższych krokach zostanie pobrany `Customer` obiekt i zostanie zmodyfikowana jedna z jego właściwości.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Aby zmienić nazwę klienta  
  
- Dodaj następujący kod powyżej `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Usuwanie jednostki  
 Przy użyciu tego samego obiektu klienta można usunąć pierwszą kolejność.  
  
 Poniższy kod ilustruje sposób tworzenia relacji między wierszami i sposobu usuwania wiersza z bazy danych. Dodaj poniższy kod przed `Console.ReadLine` , aby zobaczyć, jak można usunąć obiekty:  
  
#### <a name="to-delete-a-row"></a>Aby usunąć wiersz  
  
- Dodaj poniższy kod bezpośrednio powyżej `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Przesyłanie zmian do bazy danych  
 Ostatnim krokiem wymaganym do tworzenia, aktualizowania i usuwania obiektów jest faktyczne przesłanie zmian do bazy danych. Bez tego kroku zmiany są tylko lokalne i nie będą wyświetlane w wynikach zapytania.  
  
#### <a name="to-submit-changes-to-the-database"></a>Aby przesłać zmiany do bazy danych  
  
1. Wstaw poniższy kod powyżej `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. Wstaw poniższy kod (po `SubmitChanges`), aby wyświetlić efekty przesłania zmian:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
4. Naciśnij klawisz ENTER w oknie **konsoli** , aby zamknąć aplikację.  
  
> [!NOTE]
> Po dodaniu nowego klienta przez przesłanie zmian nie można wykonać tego rozwiązania ponownie, ponieważ jest to możliwe. Aby ponownie wykonać rozwiązanie, Zmień nazwę klienta i identyfikator klienta, który ma zostać dodany.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](learning-by-walkthroughs.md)
