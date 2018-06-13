---
title: 'Wskazówki: Manipulowanie danych (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: e0bf8b32595f656d3bff424610f193bd84d0f5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361656"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>Wskazówki: Manipulowanie danych (Visual Basic)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza Dodawanie, modyfikowanie i usuwanie danych z bazy danych. Aby dodać klienta, Zmień nazwę klienta i usunąć zamówienie będzie używał kopii przykładowej bazy danych Northwind.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu ustawienia środowiska deweloperskiego Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku wymaga następujących elementów:  
  
-   W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest2") do przechowywania plików. Utwórz ten folder przed rozpoczęciem przewodnika.  
  
-   Przykładowa bazy danych Northwind.  
  
     Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest2.  
  
-   Plik kodu języka Visual Basic wygenerowany z bazy danych Northwind.  
  
     Ten plik można wygenerować za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub narzędzie SQLMetal. W tym przewodniku została napisana przy użyciu narzędzia SQLMetal z następującego polecenia:  
  
     **sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**  
  
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
  
1.  W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.  
  
2.  W **typy projektów** okienka w **nowy projekt** okno dialogowe, kliknij przycisk **Visual Basic**.  
  
3.  W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.  
  
4.  W **nazwa** wpisz **LinqDataManipulationApp**.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań LINQ i dyrektywy  
 W tym przewodniku zastosowano zestawy, które nie mogą być instalowane domyślnie w projekcie. Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie do projektu (kliknij **Pokaż wszystkie pliki** w **Eksploratora rozwiązań** i rozwiń **odwołania** węzła), dodaj ją, zgodnie z objaśnieniem w Poniższe kroki.  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3.  W edytorze kodu, Dodaj następujące dyrektywy powyżej **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie plików kodu Northwind do projektu  
 Tych krokach przyjęto założenie, aby wygenerować plik kodu z przykładowej bazy danych Northwind użycie narzędzia SQLMetal. Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu northwind do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
2.  W **Dodaj istniejący element** okno dialogowe, przejdź do c:\linqtest2\northwind.vb, a następnie kliknij przycisk **Dodaj**.  
  
     Plik northwind.vb zostanie dodany do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Trwa konfigurowanie połączenia z bazą danych  
 Najpierw należy przetestować połączenie z bazą danych. Szczególnie Pamiętaj, że nazwa bazy danych, Northwnd, nie ma żadnych i znak. Jeśli generować błędy w następnych krokach, przejrzyj plik northwind.vb ustalenie, jak została wpisana Northwind klasy częściowej.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Aby skonfigurować i przetestować połączenie z bazą danych  
  
1.  Wpisz lub wklej następujący kod do `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  Naciśnij klawisz F5, aby przetestować aplikację na tym etapie.  
  
     A **konsoli** zostanie otwarte okno.  
  
     Zamknij aplikację, naciskając klawisz Enter w **konsoli** okna, lub przez kliknięcie przycisku **Zatrzymaj debugowanie** w programie Visual Studio **debugowania** menu.  
  
## <a name="creating-a-new-entity"></a>Tworzenie nowej jednostki  
 Tworzenie nowej jednostki jest prosta. Można utworzyć obiektów (takich jak `Customer`) przy użyciu `New` — słowo kluczowe.  
  
 W tym i sekcje wprowadzania zmian tylko do lokalnej pamięci podręcznej. Żadne zmiany nie są wysyłane do bazy danych do czasu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> do końca tego przewodnika.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Aby dodać nowy obiekt jednostki klienta  
  
1.  Utwórz nową `Customer` przez dodanie poniższego kodu przed `Console.ReadLine` w `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  Naciśnij klawisz F5, aby debugować rozwiązania.  
  
     Wyniki, które są wyświetlane w oknie konsoli są następujące:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Należy pamiętać, że nowy wiersz nie są wyświetlane w wynikach. Nowe dane nie ma jeszcze przesłane do bazy danych.  
  
3.  Naciśnij klawisz Enter w **konsoli** okno, aby zatrzymać debugowanie.  
  
## <a name="updating-an-entity"></a>Aktualizowanie jednostki  
 W poniższych krokach będą pobierane `Customer` obiektów i zmodyfikować jednej z jego właściwości.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Aby zmienić nazwę klienta  
  
-   Dodaj następujący kod powyżej `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Usuwanie jednostki  
 Przy użyciu tego samego obiektu klienta, możesz usunąć pierwszej kolejności.  
  
 Poniższy kod przedstawia sposób sever relacje między wierszami i sposobu usunięcia wiersza z bazy danych.  
  
#### <a name="to-delete-a-row"></a>Aby usunąć wiersz  
  
-   Dodaj następujący kod po prostu powyżej `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Przesyłanie zmian w bazie danych  
 Ostatni krok wymagany do tworzenia, aktualizowania i usuwania obiektów jest rzeczywiście przesłać zmiany w bazie danych. Bez tego kroku zmiany są tylko lokalne i nie będą widoczne w wynikach zapytania.  
  
#### <a name="to-submit-changes-to-the-database"></a>Aby przesłać zmiany w bazie danych  
  
1.  Wstaw poniższy kod nad `Console.ReadLine`:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  Wstaw następujący kod (po `SubmitChanges`) do wyświetlenia przed i po skutków przesyłanie zmian:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  Naciśnij klawisz F5, aby debugować rozwiązania.  
  
     W oknie konsoli wygląda następująco:  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  Naciśnij klawisz Enter w **konsoli** okno, aby zatrzymać debugowanie.  
  
> [!NOTE]
>  Po dodaniu nowego klienta, przesyłając zmiany, nie można wykonać tego rozwiązania ponownie, ponieważ nie można dodać tego samego klienta ponownie jako jest. Aby wykonać ponownie rozwiązanie, zmienić wartości Identyfikatora klienta ma zostać dodana.  
  
## <a name="see-also"></a>Zobacz też  
 [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
