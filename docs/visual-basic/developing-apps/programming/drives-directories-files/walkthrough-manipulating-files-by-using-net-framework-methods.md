---
title: Manipulowanie plikami za pomocą metod .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333787"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Wskazówki: manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)

W tym instruktażu pokazano, jak otworzyć i odczytać plik przy <xref:System.IO.StreamReader> użyciu klasy, sprawdzić, czy jest uzyskiwany dostęp do pliku, wyszukać ciąg w pliku odczytanym z wystąpieniem <xref:System.IO.StreamReader> klasy i zapisać w pliku przy użyciu <xref:System.IO.StreamWriter> klasy.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Tworzenie aplikacji

Uruchom program Visual Studio i Rozpocznij projekt, tworząc formularz, którego użytkownik może użyć do zapisu w wytworzonym pliku.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. W menu **plik** wybierz pozycję **Nowy projekt**.

2. W okienku **Nowy projekt** kliknij pozycję **aplikacja systemu Windows**.

3. W polu **Nazwa** wpisz `MyDiary` i kliknij przycisk **OK**.

     Program Visual Studio dodaje projekt do **Eksplorator rozwiązań**, a **Projektant formularzy systemu Windows** zostanie otwarty.

4. Dodaj kontrolki w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|**Stream**|**Właściwości**|**Wartościami**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Submit`<br /><br /> **Prześlij wpis**|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Clear`<br /><br /> **Wyczyść wpis**|
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Multiline**|`Entry`<br /><br /> **Wprowadź coś.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Zapisywanie w pliku

Aby dodać możliwość zapisu do pliku za pośrednictwem aplikacji, należy użyć <xref:System.IO.StreamWriter> klasy. <xref:System.IO.StreamWriter>jest przeznaczony do znakowania danych wyjściowych w określonym kodowaniu, <xref:System.IO.Stream> podczas gdy Klasa jest zaprojektowana dla danych wejściowych i wyjściowych bajtów. Służy <xref:System.IO.StreamWriter> do zapisywania wierszy informacji w standardowym pliku tekstowym. Aby uzyskać więcej informacji na <xref:System.IO.StreamWriter> temat klasy, <xref:System.IO.StreamWriter>Zobacz.

### <a name="to-add-writing-functionality"></a>Aby dodać funkcje pisania

1. Z menu **Widok** wybierz polecenie **kod** , aby otworzyć Edytor kodu.

2. Ponieważ aplikacja odwołuje się <xref:System.IO> do przestrzeni nazw, należy dodać następujące instrukcje na początku kodu przed deklaracją klasy dla formularza, która rozpoczyna się `Public Class Form1`.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Przed zapisaniem w pliku należy utworzyć wystąpienie <xref:System.IO.StreamWriter> klasy.

3. Z menu **Widok** wybierz polecenie **Projektant** , aby powrócić do **Projektant formularzy systemu Windows**. Kliknij dwukrotnie `Submit` przycisk, aby utworzyć procedurę obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń dla przycisku, a następnie Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Zintegrowane środowisko programistyczne (IDE) programu Visual Studio powróci do edytora kodu i ustawi punkt wstawiania w ramach procedury obsługi zdarzeń, gdzie należy dodać kod.

1. Aby zapisać w pliku, użyj <xref:System.IO.StreamWriter.Write%2A> metody <xref:System.IO.StreamWriter> klasy. Dodaj poniższy kod bezpośrednio po `Dim fw As StreamWriter`. Nie musisz martwić się o wyjątek, który zostanie wygenerowany, jeśli plik nie zostanie znaleziony, ponieważ zostanie utworzony, jeśli jeszcze nie istnieje.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Upewnij się, że użytkownik nie może przesłać pustego wpisu, dodając Poniższy kod bezpośrednio `Dim ReadString As String`po.

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Ponieważ jest to Diary, użytkownik będzie chciał przypisać datę do każdego wpisu. Wstaw poniższy kod po `fw = New StreamWriter("C:\MyDiary.txt", True)` , aby ustawić zmienną `Today` na bieżącą datę.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Na koniec Dołącz kod, aby wyczyścić <xref:System.Windows.Forms.TextBox>. Dodaj następujący kod do `Clear` <xref:System.Windows.Forms.Control.Click> zdarzenia przycisku.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Dodawanie funkcji wyświetlania do Diary

W tej sekcji dodasz funkcję, która wyświetla najnowszy wpis w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Możesz również dodać <xref:System.Windows.Forms.ComboBox> , który wyświetla różne wpisy i z których użytkownik może wybrać wpis, który ma być wyświetlany w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Wystąpienie <xref:System.IO.StreamReader> klasy odczytuje z `MyDiary.txt`. Podobnie jak <xref:System.IO.StreamWriter> Klasa, <xref:System.IO.StreamReader> jest przeznaczona do użycia z plikami tekstowymi.

W tej części przewodnika Dodaj kontrolki z poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|Kontrola|Właściwości|Wartości|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Widać**<br /><br /> **Rozmiar**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Display`<br /><br /> **Wyświetlanie**|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`GetEntries`<br /><br /> **Pobierz wpisy**|
|<xref:System.Windows.Forms.ComboBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`PickEntries`<br /><br /> **Wybierz wpis**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Aby wypełnić pole kombi

1. `PickEntries` Służy do wyświetlania dat, w których użytkownik przesyła każdy wpis, dzięki czemu użytkownik może wybrać wpis z konkretnej <xref:System.Windows.Forms.ComboBox> daty. Utwórz procedurę <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla `GetEntries` przycisku i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie kliknij pozycję **Pobierz wpisy**. Kliknij strzałkę listy rozwijanej w oknie, <xref:System.Windows.Forms.ComboBox> aby wyświetlić daty wejścia.

### <a name="to-choose-and-display-individual-entries"></a>Aby wybrać i wyświetlić poszczególne wpisy

1. Utwórz procedurę <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla `Display` przycisku i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie prześlij wpis. Kliknij pozycję **Pobierz wpisy**, wybierz wpis z <xref:System.Windows.Forms.ComboBox>, a następnie kliknij przycisk **Wyświetl**. Zawartość wybranego wpisu zostanie wyświetlona w `DisplayEntry` <xref:System.Windows.Forms.TextBox>.

## <a name="enabling-users-to-delete-or-modify-entries"></a>Umożliwienie użytkownikom usuwania lub modyfikowania wpisów

Na koniec możesz dołączyć dodatkowe funkcje, które umożliwiają użytkownikom usuwanie i modyfikowanie wpisów przy użyciu `DeleteEntry` przycisków i `EditEntry` . Oba przyciski pozostają wyłączone, chyba że zostanie wyświetlony wpis.

Dodaj kontrolki w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|Kontrola|Właściwości|Wartości|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`DeleteEntry`<br /><br /> **Usuń wpis**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`EditEntry`<br /><br /> **Edytuj wpis**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`SubmitEdit`<br /><br /> **Prześlij edycję**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Aby włączyć usuwanie i modyfikowanie wpisów

1. Dodaj następujący kod do `Display` <xref:System.Windows.Forms.Control.Click> zdarzenia przycisku. `DisplayEntry.Text = ReadString`

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Utwórz procedurę <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla `DeleteEntry` przycisku i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Gdy użytkownik wyświetla wpis, `EditEntry` przycisk zostaje włączony. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> zdarzenia `Display` przycisku po. `DisplayEntry.Text = ReadString`

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Utwórz procedurę <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla `EditEntry` przycisku i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Utwórz procedurę <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla `SubmitEdit` przycisku i Dodaj następujący kod

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację. Kliknij pozycję **Pobierz wpisy**, wybierz pozycję, a następnie kliknij pozycję **Wyświetl**. Wpis zostanie wyświetlony w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Kliknij pozycję **Edytuj wpis**. Wpis zostanie wyświetlony w `Entry` <xref:System.Windows.Forms.TextBox>. Edytuj wpis w `Entry` <xref:System.Windows.Forms.TextBox> i kliknij pozycję **Prześlij edytować**. Otwórz plik `MyDiary.txt` , aby potwierdzić korektę. Teraz wybierz wpis, a następnie kliknij pozycję **Usuń wpis**. Gdy zostanie <xref:System.Windows.Forms.MessageBox> potwierdzone żądanie, kliknij przycisk **OK**. Zamknij aplikację i Otwórz `MyDiary.txt` , aby potwierdzić usunięcie.

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Wskazówki](../../../../visual-basic/walkthroughs.md)
