---
title: 'Przewodnik: Używanie tylko procedur składowanych (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 69419dd5bb49c2e47315d0079df3a7b575ad9afd
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971777"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>Przewodnik: Używanie tylko procedur składowanych (C#)

Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz uzyskiwania dostępu do danych przez wykonywanie procedur składowanych. Ta metoda jest często używana przez administratorów bazy danych do ograniczania dostępu do magazynu.

> [!NOTE]
> Można również użyć procedur składowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacjach, aby przesłonić zachowanie domyślne `Create`, szczególnie w `Delete` przypadku procesów, `Update`i. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).

Na potrzeby tego instruktażu zostaną użyte dwie metody, które zostały zamapowane na procedury składowane w przykładowej bazie danych Northwind: CustOrdersDetail i CustOrderHist. Mapowanie odbywa się po uruchomieniu narzędzia wiersza polecenia SqlMetal w celu wygenerowania C# pliku. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne w dalszej części tego przewodnika.

Ten Instruktaż nie bazuje na Object Relational Designer. Deweloperzy korzystający z programu Visual Studio mogą również używać projektanta O/R do implementowania funkcjonalności procedury składowanej. Zobacz [narzędzia LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik wymaga następujących czynności:

- W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest7"). Utwórz ten folder przed rozpoczęciem przewodnika.

- Przykładowa bazy danych Northwind.

     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po pobraniu bazy danych Skopiuj plik northwnd. mdf do folderu c:\linqtest7.

- Plik C# kodu wygenerowany na podstawie bazy danych Northwind.

     Ten Instruktaż został zapisany przy użyciu narzędzia SqlMetal z następującym wierszem polecenia:

     **SQLMetal/Code: "c:\linqtest7\northwind.cs"/Language: CSharp "c:\linqtest7\northwnd.mdf"/sprocs/Functions/pluralize**

     Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).

## <a name="overview"></a>Omówienie

Ten przewodnik składa się z sześciu głównych zadań:

- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Konfigurowanie rozwiązania w programie Visual Studio.

- Dodawanie zestawu System. Data. LINQ do projektu.

- Dodawanie pliku kodu bazy danych do projektu.

- Tworzenie połączenia z bazą danych.

- Konfigurowanie interfejsu użytkownika.

- Uruchamianie i testowanie aplikacji.

## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie rozwiązania LINQ to SQL

W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.

### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć rozwiązanie LINQ to SQL

1. W menu **plik** programu Visual Studio wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W okienku **typy projektów** okna dialogowego **Nowy projekt** kliknij pozycję Wizualizacja. **C#**

3. W okienku **Szablony** kliknij pozycję **Windows Forms aplikacji**.

4. W polu **Nazwa** wpisz **SprocOnlyApp**.

5. W polu **Lokalizacja** Sprawdź, gdzie mają być przechowywane pliki projektu.

6. Kliknij przycisk **OK**.

     Zostanie otwarty Projektant formularzy systemu Windows.

## <a name="adding-the-linq-to-sql-assembly-reference"></a>Dodawanie odwołania do zestawu LINQ to SQL

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zestaw nie jest uwzględniony w szablonie standardowej aplikacji Windows Forms. Musisz samodzielnie dodać zestaw, jak wyjaśniono w następujących krokach:

### <a name="to-add-systemdatalinqdll"></a>To add System.Data.Linq.dll

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.

     Zestaw zostanie dodany do projektu.

## <a name="adding-the-northwind-code-file-to-the-project"></a>Dodawanie pliku kodu Northwind do projektu

W tym kroku przyjęto założenie, że użyto narzędzia SqlMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.

### <a name="to-add-the-northwind-code-file-to-the-project"></a>Aby dodać plik kodu Northwind do projektu

1. W menu **projekt** kliknij polecenie **Dodaj istniejący element**.

2. W oknie dialogowym **Dodaj istniejący element** przejdź do c:\linqtest7\northwind.cs, a następnie kliknij przycisk **Dodaj**.

     Plik northwind.cs jest dodawany do projektu.

## <a name="creating-a-database-connection"></a>Tworzenie połączenia z bazą danych

W tym kroku zdefiniujesz połączenie z przykładową bazą danych Northwind. W tym instruktażu jako ścieżki jest stosowany "c:\linqtest7\northwnd.mdf".

### <a name="to-create-the-database-connection"></a>Aby utworzyć połączenie z bazą danych

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1.cs**, a następnie kliknij pozycję **Wyświetl kod**.

2. Wpisz następujący kod do `Form1` klasy:

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a>Konfigurowanie interfejsu użytkownika

To zadanie służy do konfigurowania interfejsu, dzięki czemu użytkownicy mogą wykonywać procedury składowane w celu uzyskania dostępu do danych w bazie danych. W aplikacjach opracowywanych przy użyciu tego przewodnika użytkownicy mogą uzyskać dostęp do danych w bazie danych tylko przy użyciu procedur przechowywanych osadzonych w aplikacji.

### <a name="to-set-up-the-user-interface"></a>Aby skonfigurować interfejs użytkownika

1. Wróć do Projektant formularzy systemu Windows (**Form1. cs [Design]** ).

2. W menu **Widok** kliknij pozycję **Przybornik**.

     Zostanie otwarty Przybornik.

    > [!NOTE]
    > Kliknij przycisk **Autoukrywanie** pinezki, aby zachować Przybornik otwarty podczas wykonywania pozostałych kroków w tej sekcji.

3. Przeciągnij dwa przyciski, dwa pola tekstowe i dwie etykiety z przybornika na **formularz Form1**.

     Rozmieść formanty jako towarzyszącą ilustrację. Rozwiń **formularz Form1** , aby umożliwić łatwe dopasowanie formantów.

4. Kliknij prawym przyciskiem myszy pozycję **Label1**, a następnie kliknij pozycję **Właściwości**.

5. Zmień właściwość **Text** z **Label1** , aby **wprowadzić IDZamówienia:** .

6. W ten sam sposób dla **etykiety 2**Zmień właściwość **Text** z **etykiety 2** , aby **wprowadzić CustomerID:** .

7. W ten sam sposób Zmień właściwość **Text** dla **Button1** na **Order**details.

8. Zmień właściwość **Text** dla **Button2** na **historię kolejności**.

     Rozszerz kontrolki przycisku, aby cały tekst był widoczny.

### <a name="to-handle-button-clicks"></a>Aby obsłużyć kliknięcia przycisku

1. Kliknij dwukrotnie pozycję **szczegóły zamówienia** na **formularzu Form1** , aby otworzyć program obsługi zdarzeń Button1 w edytorze kodu.

2. Wpisz następujący kod do `button1` procedury obsługi:

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. Teraz kliknij dwukrotnie pozycję **Button2** na **formularzu Form1** , `button2` aby otworzyć procedurę obsługi

4. Wpisz następujący kod do `button2` procedury obsługi:

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz czas na przetestowanie aplikacji. Należy pamiętać, że kontakt z magazynem danych jest ograniczony do wszelkich akcji, które mogą wykonać dwie procedury składowane. Te akcje mają na celu zwrócenie produktów uwzględnionych w dowolnym przypisanym identyfikatorze IDZamówienia lub zwrócenie historii produktów zamówionych dla dowolnego elementu IDKlienta, który wprowadzasz.

### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij klawisz F5, aby rozpocząć debugowanie.

     Zostanie wyświetlony formularz Form1.

2. W polu **Wprowadź identyfikator zamówienia** wpisz `10249`, a następnie kliknij pozycję **szczegóły zamówienia**.

     Okno komunikatu zawiera listę produktów uwzględnionych w kolejności 10249.

     Kliknij przycisk **OK** , aby zamknąć okno komunikatu.

3. W polu **wprowadź wartość IDKlienta** wpisz `ALFKI`, a następnie kliknij pozycję **historia kolejności**.

     Zostanie wyświetlone okno komunikatu z listą historii zamówień dla klienta ALFKI.

     Kliknij przycisk **OK** , aby zamknąć okno komunikatu.

4. W polu **Wprowadź identyfikator zamówienia** wpisz `123`, a następnie kliknij pozycję **szczegóły zamówienia**.

     Zostanie wyświetlone okno komunikatu z napisem "Brak wyników".

     Kliknij przycisk **OK** , aby zamknąć okno komunikatu.

5. W menu **debugowanie** kliknij **Zatrzymaj debugowanie**.

     Sesja debugowania zostanie zamknięta.

6. Jeśli zakończysz eksperymentowanie, możesz kliknąć przycisk **Zamknij projekt** w menu **plik** i zapisać projekt po wyświetleniu monitu.

## <a name="next-steps"></a>Następne kroki

Możesz udoskonalić ten projekt, wprowadzając pewne zmiany. Na przykład można wyświetlić listę dostępnych procedur składowanych w polu listy i wybrać procedury, które należy wykonać. Możesz również przesyłać strumieniowo dane wyjściowe raportów do pliku tekstowego.

## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
