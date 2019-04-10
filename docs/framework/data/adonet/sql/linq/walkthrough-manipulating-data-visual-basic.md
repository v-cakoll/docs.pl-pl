---
title: 'Przewodnik: Manipulowanie danymi (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 34049f113ce9da0ed1c4cc63fd53093a0775bbad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208309"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>Przewodnik: Manipulowanie danymi (Visual Basic)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz dotyczący dodawania, modyfikowania i usuwania danych w bazie danych. Kopię przykładowej bazy danych Northwind użyje do dodawania klienta, Zmień nazwę klienta i usunąć zamówienie.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu ustawień środowiska deweloperskiego Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik wymaga następujących elementów:  
  
-   W tym przewodniku używa dedykowanego folder ("c:\linqtest2") do przechowywania plików. Przed rozpoczęciem instruktażu, należy utworzyć ten folder.  
  
-   Przykładowa bazy danych Northwind.  
  
     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest2.  
  
-   Plik kodu języka Visual Basic, wygenerowany na podstawie bazy danych Northwind.  
  
     Ten plik można wygenerować za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub narzędzia SQLMetal. Ten instruktaż został napisany za pomocą narzędzia SQLMetal za pomocą następującego polecenia:  
  
     **Program sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" / pluralize**  
  
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
  
1.  W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.  
  
2.  W **typów projektów** okienka **nowy projekt** okno dialogowe, kliknij przycisk **języka Visual Basic**.  
  
3.  W **szablony** okienku kliknij **aplikację Konsolową**.  
  
4.  W **nazwa** wpisz **LinqDataManipulationApp**.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołania do zapytań LINQ i dyrektywy  
 W tym instruktażu wykorzystano zestawów, które nie mogą być instalowane domyślnie w projekcie. Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie do projektu (kliknij **Pokaż wszystkie pliki** w **Eksploratora rozwiązań** i rozwiń **odwołania** węzła), ją dodać, jak wyjaśniono w Poniższe kroki.  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
3.  W edytorze kodu Dodaj następujące dyrektywy powyżej **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie pliku Northwind kodu do projektu  
 Te czynności zakładają, że trzeba użyć narzędzia SQLMetal do generowania pliku kodu z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu northwind do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
2.  W **Dodaj istniejący element** okno dialogowe, przejdź do c:\linqtest2\northwind.vb, a następnie kliknij przycisk **Dodaj**.  
  
     Plik northwind.vb zostanie dodany do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Konfigurowanie połączenia z bazą danych  
 Najpierw Przetestuj połączenie z bazą danych. Zwróć uwagę szczególnie, że nazwa bazy danych, Northwnd, zawiera i nie znak. Jeśli użytkownik generuje błędy w następnych krokach, przejrzyj plik northwind.vb, aby określić, jak została wpisana klasy częściowej Northwind.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Aby skonfigurować i przetestować połączenie z bazą danych  
  
1.  Wpisz lub wklej następujący kod do `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  Naciśnij klawisz F5, aby przetestować aplikację na tym etapie.  
  
     A **konsoli** zostanie otwarte okno.  
  
     Zamknij aplikację, naciskając klawisz Enter w **konsoli** okna, lub przez kliknięcie przycisku **Zatrzymaj debugowanie** w programie Visual Studio **debugowania** menu.  
  
## <a name="creating-a-new-entity"></a>Tworzenie nowej jednostki  
 Tworzenie nowej jednostki jest bardzo proste. Możesz tworzyć obiekty (takie jak `Customer`) przy użyciu `New` — słowo kluczowe.  
  
 W tym i sekcje w przypadku wprowadzania zmian tylko do lokalnej pamięci podręcznej. Żadne zmiany nie są wysyłane do bazy danych, dopóki nie zostanie wywołana <xref:System.Data.Linq.DataContext.SubmitChanges%2A> pod koniec tego przewodnika.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Aby dodać nowy obiekt jednostki klienta  
  
1.  Utwórz nową `Customer` , dodając następujący kod przed `Console.ReadLine` w `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
     Wyniki, które są wyświetlane w oknie konsoli są następujące:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Należy pamiętać, że nowy wiersz nie jest wyświetlana w wynikach. Nowe dane nie ma jeszcze przesłane do bazy danych.  
  
3.  Naciśnij klawisz Enter w **konsoli** okno, aby zatrzymać debugowanie.  
  
## <a name="updating-an-entity"></a>Aktualizowanie jednostki  
 W poniższych krokach będą pobierane `Customer` i zmodyfikować jedną z jej właściwości.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Aby zmienić nazwę klienta  
  
-   Dodaj następujący kod powyżej `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Usuwanie jednostki  
 Przy użyciu tego samego obiektu klienta, możesz usunąć pierwszej kolejności.  
  
 Poniższy kod przedstawia sposób sever relacje między wierszami i jak usunąć wiersz z bazy danych.  
  
#### <a name="to-delete-a-row"></a>Aby usunąć wiersz  
  
-   Dodaj poniższy kod tuż nad `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Przesyłanie zmian do bazy danych  
 Ostatni krok wymagany do tworzenia, aktualizowania i usuwania obiektów, to aby rzeczywiście przesłać zmiany w bazie danych. Bez tego kroku zmiany są tylko lokalne i nie będą widoczne w wynikach kwerendy.  
  
#### <a name="to-submit-changes-to-the-database"></a>Aby przesłać zmiany do bazy danych  
  
1.  Wstaw poniższy kod tuż nad `Console.ReadLine`:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  Wstaw następujący kod (po `SubmitChanges`) do wyświetlenia przed i po nim skutki przesyłanie zmian:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
     W oknie konsoli zostanie wyświetlony w następujący sposób:  
  
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
>  Po dodaniu nowego klienta, przesyłając żądanie zmiany, nie można wykonać to rozwiązanie ponownie, ponieważ nie można dodać tego samego klienta ponownie jako jest. Aby wykonać ponownie rozwiązanie, należy zmienić wartość Identyfikatora klienta, który ma zostać dodany.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
