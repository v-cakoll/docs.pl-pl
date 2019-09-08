---
title: 'Przewodnik: Manipulowanie danymi (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: a74216c53c45790b974938c7155e0b5e1043ac13
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792289"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>Przewodnik: Manipulowanie danymi (Visual Basic)
Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz służący do dodawania, modyfikowania i usuwania danych w bazie danych. Zostanie użyta kopia przykładowej bazy danych Northwind, aby dodać klienta, zmienić nazwę klienta i usunąć zamówienie.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Ten Instruktaż został zapisany przy użyciu ustawień tworzenia Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik wymaga następujących czynności:  
  
- W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest2"). Utwórz ten folder przed rozpoczęciem przewodnika.  
  
- Przykładowa bazy danych Northwind.  
  
     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md). Po pobraniu bazy danych Skopiuj plik northwnd. mdf do folderu c:\linqtest2.  
  
- Plik kodu Visual Basic wygenerowany na podstawie bazy danych Northwind.  
  
     Ten plik można wygenerować przy użyciu Object Relational Designer lub narzędzia SQLMetal. Ten Instruktaż został zapisany przy użyciu narzędzia SQLMetal z następującym wierszem polecenia:  
  
     **sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**  
  
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
  
1. W menu **plik** programu Visual Studio kliknij pozycję **Nowy projekt**.  
  
2. W okienku **typy projektów** okna dialogowego **nowy projekt** kliknij **Visual Basic**.  
  
3. W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.  
  
4. W polu **Nazwa** wpisz **LinqDataManipulationApp**.  
  
5. Kliknij przycisk **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań i dyrektyw LINQ  
 W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie. Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie w projekcie (kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań** i rozwiń węzeł **odwołania** ), Dodaj go, jak wyjaśniono w poniższych krokach.  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.  
  
2. W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.  
  
     Zestaw zostanie dodany do projektu.  
  
3. W edytorze kodu Dodaj następujące dyrektywy powyżej **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie pliku kodu Northwind do projektu  
 W tych krokach przyjęto założenie, że użyto narzędzia SQLMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu Northwind do projektu  
  
1. W menu **projekt** kliknij polecenie **Dodaj istniejący element**.  
  
2. W oknie dialogowym **Dodaj istniejący element** przejdź do c:\linqtest2\northwind.vb, a następnie kliknij przycisk **Dodaj**.  
  
     Plik Northwind. vb zostanie dodany do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Konfigurowanie połączenia z bazą danych  
 Najpierw Przetestuj połączenie z bazą danych. Należy pamiętać, że nazwa bazy danych, northwnd, nie ma znaku. W przypadku wygenerowania błędów w następnych krokach przejrzyj plik Northwind. vb, aby określić sposób pisowni klasy częściowej Northwind.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Aby skonfigurować i przetestować połączenie z bazą danych  
  
1. Wpisz lub wklej następujący kod do `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. Naciśnij klawisz F5, aby przetestować aplikację w tym momencie.  
  
     Zostanie otwarte okno **konsoli** .  
  
     Zamknij aplikację, naciskając klawisz ENTER w oknie **konsoli** lub klikając przycisk **Zatrzymaj debugowanie** w menu **debugowanie** programu Visual Studio.  
  
## <a name="creating-a-new-entity"></a>Tworzenie nowej jednostki  
 Tworzenie nowej jednostki jest proste. Możesz tworzyć obiekty (na przykład `Customer`) za `New` pomocą słowa kluczowego.  
  
 W tym i w poniższych sekcjach wprowadzasz zmiany tylko do lokalnej pamięci podręcznej. Żadne zmiany nie są wysyłane do bazy danych do momentu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> końca tego przewodnika.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Aby dodać nowy obiekt jednostki klienta  
  
1. Utwórz nowy `Customer` , dodając następujący kod `Sub Main`przed `Console.ReadLine` :  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
     Wyniki wyświetlane w oknie konsoli są następujące:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Należy zauważyć, że nowy wiersz nie jest wyświetlany w wynikach. Nowe dane nie zostały jeszcze przesłane do bazy danych.  
  
3. Naciśnij klawisz ENTER w oknie **konsoli** , aby zatrzymać debugowanie.  
  
## <a name="updating-an-entity"></a>Aktualizowanie jednostki  
 W poniższych krokach zostanie pobrany `Customer` obiekt i zostanie zmodyfikowana jedna z jego właściwości.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Aby zmienić nazwę klienta  
  
- Dodaj następujący kod powyżej `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Usuwanie jednostki  
 Przy użyciu tego samego obiektu klienta można usunąć pierwszą kolejność.  
  
 Poniższy kod ilustruje sposób tworzenia relacji między wierszami i sposobu usuwania wiersza z bazy danych.  
  
#### <a name="to-delete-a-row"></a>Aby usunąć wiersz  
  
- Dodaj poniższy kod bezpośrednio powyżej `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Przesyłanie zmian do bazy danych  
 Ostatnim krokiem wymaganym do tworzenia, aktualizowania i usuwania obiektów jest faktyczne przesłanie zmian do bazy danych. Bez tego kroku zmiany są tylko lokalne i nie będą wyświetlane w wynikach zapytania.  
  
#### <a name="to-submit-changes-to-the-database"></a>Aby przesłać zmiany do bazy danych  
  
1. Wstaw poniższy kod powyżej `Console.ReadLine`:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. Wstaw poniższy kod (po `SubmitChanges`), aby wyświetlić efekty przesłania zmian:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. Naciśnij klawisz F5, aby debugować rozwiązanie.  
  
     Okno konsoli jest wyświetlane w następujący sposób:  
  
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
  
4. Naciśnij klawisz ENTER w oknie **konsoli** , aby zatrzymać debugowanie.  
  
> [!NOTE]
> Po dodaniu nowego klienta przez przesłanie zmian nie można wykonać tego rozwiązania ponownie, ponieważ nie można ponownie dodać tego samego klienta. Aby ponownie wykonać rozwiązanie, należy zmienić wartość identyfikatora klienta, który ma zostać dodany.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](learning-by-walkthroughs.md)
