---
title: 'Wskazówki: Tylko przy użyciu przechowywanych procedur (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 223c93a790e610414aa48c2aea8e884b9d841666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>Wskazówki: Tylko przy użyciu przechowywanych procedur (C#)
Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tylko procedury składowane scenariusz do uzyskiwania dostępu do danych, wykonując. Ta metoda jest często używane przez administratorów bazy danych do ograniczenia, jak jest uzyskiwany dostęp do magazynu danych.  
  
> [!NOTE]
>  Można również użyć procedur składowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, aby zastąpić zachowanie domyślne, szczególnie w przypadku `Create`, `Update`, i `Delete` procesów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Do celów tego przewodnika, korzystasz z dwóch metod, które zostały zamapowane do procedur przechowywanych w bazie danych Northwind: CustOrdersDetail i CustOrderHist. Mapowanie występuje podczas uruchamiania narzędzia wiersza polecenia SqlMetal, aby wygenerować plik C#. Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych w dalszej części tego przewodnika.  
  
 Ten przewodnik nie bazuje na [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Za pomocą programu Visual Studio programiści mogą również wykorzystać [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do implementowania procedury składowanej. Zobacz [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku wymaga następujących elementów:  
  
-   W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest7") do przechowywania plików. Utwórz ten folder przed rozpoczęciem przewodnika.  
  
-   Przykładowa bazy danych Northwind.  
  
     Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest7.  
  
-   Plik kodu C# wygenerowany z bazy danych Northwind.  
  
     W tym przewodniku została napisana przy użyciu narzędzia SqlMetal z następującego polecenia:  
  
     **sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralize**  
  
     Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik obejmuje sześć głównych zadań:  
  
-   Konfigurowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.  
  
-   Dodawanie zestawu System.Data.Linq do projektu.  
  
-   Dodawanie plików kodu bazy danych do projektu.  
  
-   Tworzenie połączenia z bazą danych.  
  
-   Konfigurowanie interfejsu użytkownika.  
  
-   Działa i testowania aplikacji.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie składnika LINQ to SQL rozwiązania  
 W tym zadaniu pierwszego tworzenia rozwiązania Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć składnika LINQ to SQL rozwiązania  
  
1.  W programie Visual Studio **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **typy projektów** okienka w **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#**.  
  
3.  W **szablony** okienku, kliknij przycisk **aplikacji Windows Forms**.  
  
4.  W **nazwa** wpisz **SprocOnlyApp**.  
  
5.  W **lokalizacji** upewnij się, którym chcesz przechowywać pliki projektu.  
  
6.  Kliknij przycisk **OK**.  
  
     Zostanie otwarty projektant formularzy systemu Windows.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Dodawanie LINQ do SQL odwołanie do zestawu  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zestaw nie jest dołączony do standardowego szablonu aplikacji formularzy systemu Windows. Należy dodać zestaw samodzielnie, zgodnie z objaśnieniem w poniższych krokach:  
  
#### <a name="to-add-systemdatalinqdll"></a>To add System.Data.Linq.dll  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.  
  
     Zestaw został dodany do projektu.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie plików kodu Northwind do projektu  
 W tym kroku przyjęto założenie, użycie narzędzia SqlMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu northwind do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
2.  W **Dodaj istniejący element** okno dialogowe, Przenieś do c:\linqtest7\northwind.cs, a następnie kliknij przycisk **Dodaj**.  
  
     Plik northwind.cs zostanie dodany do projektu.  
  
## <a name="creating-a-database-connection"></a>Tworzenie połączenia z bazą danych  
 W tym kroku definiowane połączenie z przykładowej bazy danych Northwind. W tym przewodniku zastosowano "c:\linqtest7\northwnd.mdf" jako ścieżka.  
  
#### <a name="to-create-the-database-connection"></a>Aby utworzyć połączenie z bazą danych  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliku Form1.cs**, a następnie kliknij przycisk **kod widoku**.  
  
2.  Wpisz następujący kod do `Form1` klasy:  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a>Konfigurowanie interfejsu użytkownika  
 W tym zadaniu skonfigurowaniu interfejs, dzięki czemu użytkownicy mogą wykonywać procedur składowanych dostępu do danych w bazie danych. W aplikacjach, które tworzysz z tym przewodnikiem użytkownicy mogą korzystać w bazie danych tylko przy użyciu procedur składowanych osadzone w aplikacji.  
  
#### <a name="to-set-up-the-user-interface"></a>Aby skonfigurować interfejs użytkownika  
  
1.  Projektant Forms powrotu do systemu Windows (**Form1.cs[Design]**).  
  
2.  Na **widoku** menu, kliknij przycisk **przybornika**.  
  
     Otwiera przybornika.  
  
    > [!NOTE]
    >  Kliknij przycisk **autohide —** pinezki, aby utrzymać otwarte przybornika podczas przeprowadzania pozostałe kroki w tej sekcji.  
  
3.  Przeciągnij z przybornika do dwóch przycisków, dwa pola tekstowe i dwie etykiety **Form1**.  
  
     Rozmieszczanie formantów jak towarzyszący ilustracji. Rozwiń węzeł **Form1** tak, aby formanty łatwo Dopasuj.  
  
4.  Kliknij prawym przyciskiem myszy **label1**, a następnie kliknij przycisk **właściwości**.  
  
5.  Zmień **tekst** właściwość z **label1** do **wprowadź OrderID:**.  
  
6.  W ten sam sposób dla **label2**, zmień **tekst** właściwość z **label2** do **wprowadź CustomerID:**.  
  
7.  W ten sam sposób, zmień **tekst** właściwość **button1** do **szczegółów zamówienia**.  
  
8.  Zmień **tekst** właściwość **button2** do **historii zamówień**.  
  
     Rozszerzenia kontrolki przycisku, dzięki czemu cały tekst jest widoczny.  
  
#### <a name="to-handle-button-clicks"></a>Do obsługi kliknięcia przycisków  
  
1.  Kliknij dwukrotnie **szczegółów zamówienia** na **Form1** aby otworzyć program obsługi zdarzeń button1 w edytorze kodu.  
  
2.  Wpisz następujący kod do `button1` obsługi:  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  Teraz kliknij dwukrotnie **button2** na **Form1** otworzyć `button2` obsługi  
  
4.  Wpisz następujący kod do `button2` obsługi:  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz nadszedł czas, aby przetestować aplikację. Należy pamiętać, że kontakt z magazynu danych jest ograniczona do dowolnej akcji może zająć dwie procedury składowanej. Te akcje są do zwrócenia produkty uwzględnione wszelkie orderID wprowadzona lub do zwrócenia historii produktów, uporządkowany w celu żadnych CustomerID wprowadzasz.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij klawisz F5, aby rozpocząć debugowania.  
  
     Zostanie wyświetlone Form1.  
  
2.  W **wprowadź OrderID** wpisz `10249`, a następnie kliknij przycisk **szczegółów zamówienia**.  
  
     Okno komunikatu wymieniono produkty uwzględnione w kolejności 10249.  
  
     Kliknij przycisk **OK** aby zamknąć okno komunikatu.  
  
3.  W **wprowadź CustomerID** wpisz `ALFKI`, a następnie kliknij przycisk **historii zamówień**.  
  
     Pojawi się komunikat z listą historii zamówień klienta ALFKI.  
  
     Kliknij przycisk **OK** aby zamknąć okno komunikatu.  
  
4.  W **wprowadź OrderID** wpisz `123`, a następnie kliknij przycisk **szczegółów zamówienia**.  
  
     Pojawi się komunikat wyświetlany "Żadne wyniki".  
  
     Kliknij przycisk **OK** aby zamknąć okno komunikatu.  
  
5.  Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.  
  
     Powoduje zamknięcie sesji debugowania.  
  
6.  Jeśli zakończysz eksperymentowanie, możesz kliknąć **Zamknij projekt** na **pliku** menu i zapisać projekt po wyświetleniu monitu.  
  
## <a name="next-steps"></a>Następne kroki  
 Wprowadzenie pewnych zmian można zwiększyć ten projekt. Na przykład możesz wyświetlić listę dostępnych procedur składowanych w polu listy i użytkownik powinien wybrać, które procedury musisz wykonać. Można również strumienia wyjściowego raportów do pliku tekstowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
