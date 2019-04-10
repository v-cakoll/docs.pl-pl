---
title: 'Przewodnik: Używanie tylko procedur składowanych (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 1527e3b4b614d4e700ae0c2c0fc555e14c7bc8d2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314831"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>Przewodnik: Używanie tylko procedur składowanych (Visual Basic)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz do uzyskiwania dostępu do danych za pomocą procedury składowane tylko. To podejście jest często używana przez administratorów baz danych, aby ograniczyć sposób dostępu do magazynu danych.  
  
> [!NOTE]
>  Można również użyć procedur składowanych w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, aby zastąpić domyślne zachowanie, szczególnie w przypadku `Create`, `Update`, i `Delete` procesów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Do celów tego przewodnika będziesz używać dwóch metod, które zostały zmapowane do procedur składowanych w bazie danych Northwind: CustOrdersDetail i CustOrderHist. Mapowanie występuje po uruchomieniu narzędzia wiersza polecenia SqlMetal, aby wygenerować plik języka Visual Basic. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne w dalszej części tego przewodnika.  
  
 W tym przewodniku nie zależą od [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Deweloperzy korzystający z programu Visual Studio można również użyć [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do implementowania procedury składowanej. Zobacz [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu ustawień środowiska deweloperskiego Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik wymaga następujących elementów:  
  
-   W tym przewodniku używa dedykowanego folder ("c:\linqtest3") do przechowywania plików. Przed rozpoczęciem instruktażu, należy utworzyć ten folder.  
  
-   Przykładowa bazy danych Northwind.  
  
     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest3.  
  
-   Plik kodu języka Visual Basic, wygenerowany na podstawie bazy danych Northwind.  
  
     Ten instruktaż został napisany za pomocą narzędzia SqlMetal za pomocą następującego polecenia:  
  
     **Program sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralize**  
  
     Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z sześciu głównych zadań:  
  
-   Konfigurowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.  
  
-   Trwa dodawanie zestawu System.Data.Linq do projektu.  
  
-   Dodawanie pliku kodu bazy danych do projektu.  
  
-   Tworzenie połączenia z bazą danych.  
  
-   Konfigurowanie interfejsu użytkownika.  
  
-   Uruchamianie i testowanie aplikacji.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie składnika LINQ to SQL rozwiązanie  
 W tym pierwszym zadaniu tworzyć rozwiązania programu Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć składnika LINQ to SQL rozwiązanie  
  
1. W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.  
  
2. W **typów projektów** okienka **nowy projekt** okna dialogowego rozwiń **języka Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
3. W **szablony** okienku kliknij **aplikacja interfejsu Windows Forms**.  
  
4. W **nazwa** wpisz **SprocOnlyApp**.  
  
5. Kliknij przycisk **OK**.  
  
     Zostanie otwarty projektant formularzy Windows.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Dodawanie programu LINQ do SQL odwołanie do zestawu  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Moduł nie jest dołączony do standardowego szablonu aplikacja interfejsu Windows Forms. Trzeba będzie dodać zestaw samodzielnie, zgodnie z opisem w poniższych krokach:  
  
#### <a name="to-add-systemdatalinqdll"></a>To add System.Data.Linq.dll  
  
1. W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**.  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
3. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie pliku Northwind kodu do projektu  
 Tego kroku przyjęto założenie, że trzeba użyć narzędzia SqlMetal do generowania pliku kodu z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu northwind do projektu  
  
1. Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
2. W **Dodaj istniejący element** przenieść c:\linqtest3\northwind.vb okno dialogowe, a następnie kliknij przycisk **Dodaj**.  
  
     Plik northwind.vb zostanie dodany do projektu.  
  
## <a name="creating-a-database-connection"></a>Tworzenie połączenia z bazą danych  
 W tym kroku zdefiniujesz połączenia z przykładową bazą danych Northwind. W tym instruktażu wykorzystano "c:\linqtest3\northwnd.mdf", jako ścieżkę.  
  
#### <a name="to-create-the-database-connection"></a>Aby utworzyć połączenie z bazą danych  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.vb**, a następnie kliknij przycisk **Wyświetl kod**.  
  
     `Class Form1` zostanie wyświetlony w edytorze kodu.  
  
2. Wpisz następujący kod do `Form1` blok kodu:  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>Konfigurowanie interfejsu użytkownika  
 W tym zadaniu utworzysz interfejs, dzięki czemu użytkownicy mogą wykonać procedur składowanych na dostęp do danych w bazie danych. W aplikacji, która jest tworzona przy użyciu tego przewodnika użytkownicy mogą korzystać tylko przy użyciu procedur składowanych osadzone w aplikacji, dane z bazy danych.  
  
#### <a name="to-set-up-the-user-interface"></a>Aby skonfigurować interfejs użytkownika  
  
1. Wróć do Windows Forms Designer (**Form1.vb[Design]**).  
  
2. Na **widoku** menu, kliknij przycisk **przybornika**.  
  
     Przybornik zostaje otwarty.  
  
    > [!NOTE]
    >  Kliknij przycisk **autoukrywania** pinezki, aby nie zamykaj przybornika podczas wykonywania pozostałych kroków w tej sekcji.  
  
3. Przeciągnij z przybornika na dwa przyciski, dwóch pól tekstowych i dwie etykiety **Form1**.  
  
     Kontrolki będą ułożone, jak pokazano na ilustracji towarzyszącej. Rozwiń **Form1** tak, aby łatwo mieści się kontrolki.  
  
4. Kliknij prawym przyciskiem myszy **Label1**, a następnie kliknij przycisk **właściwości**.  
  
5. Zmiana **tekstu** właściwość **Label1** do **wprowadź OrderID:**.  
  
6. W ten sam sposób, aby uzyskać **etykiety 2**, zmienić **tekstu** właściwość **etykiety 2** do **wprowadź CustomerID:**.  
  
7. W ten sam sposób, jak zmienić **tekstu** właściwość **Button1** do **Orderdetails**.  
  
8. Zmiana **tekstu** właściwość **Button2** do **historii zamówień**.  
  
     Tak, aby cały tekst jest widoczne, mogą zostać poszerzone formanty przycisków.  
  
#### <a name="to-handle-button-clicks"></a>Do obsługi kliknięcia przycisków  
  
1. Kliknij dwukrotnie **Orderdetails** na **Form1** utworzyć `Button1` program obsługi zdarzeń i otworzyć Edytor kodu.  
  
2. Wpisz następujący kod do `Button1` procedury obsługi:  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. Teraz kliknij dwukrotnie **Button2** na formularzu Form1, aby utworzyć `Button2` program obsługi zdarzeń i otworzyć Edytor kodu.  
  
4. Wpisz następujący kod do `Button2` procedury obsługi:  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz nadszedł czas, aby przetestować aplikację. Należy pamiętać, że kontaktu z magazynu danych jest ograniczony do dowolnych akcje można wykonać dwie procedury składowane. Te akcje są do zwrócenia produktów, dostępny dla dowolnego orderID wprowadzona lub w celu zwrócenia historii produktów uporządkowane do dowolnego CustomerID wprowadzeniu.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Naciśnij klawisz F5, aby rozpocząć debugowanie.  
  
     Zostanie wyświetlony formularz Form1.  
  
2. W **wprowadź OrderID** wpisz **10249** a następnie kliknij przycisk **Orderdetails**.  
  
     Okno komunikatu Wyświetla listę produktów dołączone w kolejności 10249.  
  
     Kliknij przycisk **OK** aby zamknąć okno komunikatu.  
  
3. W **wprowadź CustomerID** wpisz `ALFKI`, a następnie kliknij przycisk **historii zamówień**.  
  
     Okno komunikatu Wyświetla listę historii zamówień klienta Customer ALFKI.  
  
     Kliknij przycisk **OK** aby zamknąć okno komunikatu.  
  
4. W **wprowadź OrderID** wpisz `123`, a następnie kliknij przycisk **Orderdetails**.  
  
     Okno komunikatu Wyświetla "Brak wyników".  
  
     Kliknij przycisk **OK** aby zamknąć okno komunikatu.  
  
5. Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.  
  
     Powoduje zamknięcie sesji debugowania.  
  
6. Jeśli zakończysz, eksperymentowanie, możesz kliknąć **Zamknij projekt** na **pliku** menu i zapisać projekt, po wyświetleniu monitu.  
  
## <a name="next-steps"></a>Następne kroki  
 Ten projekt można zwiększyć, dokonując pewnych zmian. Na przykład możesz wyświetlić listę dostępnych procedur składowanych w polu listy i użytkownik powinien wybrać, które procedury musisz wykonać. Można również przesyłać strumieniowo dane wyjściowe raportów do pliku tekstowego.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
