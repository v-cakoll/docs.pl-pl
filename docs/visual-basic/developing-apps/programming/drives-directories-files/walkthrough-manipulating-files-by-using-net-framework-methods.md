---
title: Manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)
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
ms.openlocfilehash: fc02b795834dba4a777dc78f4c8179238ac593af
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582486"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Wskazówki: manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)

W tym instruktażu pokazano, jak otworzyć i odczytać plik przy użyciu klasy <xref:System.IO.StreamReader>, sprawdzić, czy dostęp do pliku jest uzyskiwany, wyszukaj ciąg w pliku jako odczytany z wystąpieniem klasy <xref:System.IO.StreamReader> i Zapisz w pliku przy użyciu klasy <xref:System.IO.StreamWriter>.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Tworzenie aplikacji

Uruchom program Visual Studio i Rozpocznij projekt, tworząc formularz, którego użytkownik może użyć do zapisu w wytworzonym pliku.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. W menu **plik** wybierz pozycję **Nowy projekt**.

2. W okienku **Nowy projekt** kliknij pozycję **aplikacja systemu Windows**.

3. W polu **Nazwa** wpisz `MyDiary` i kliknij przycisk **OK**.

     Program Visual Studio dodaje projekt do **Eksplorator rozwiązań**, a **Projektant formularzy systemu Windows** zostanie otwarty.

4. Dodaj kontrolki w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|**Stream**|**Właściwości**|**Wartość**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Submit`<br /><br /> **Prześlij wpis**|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Clear`<br /><br /> **Wyczyść wpis**|
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Multiline**|`Entry`<br /><br /> **Wprowadź coś.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Zapisywanie w pliku

Aby dodać możliwość zapisu do pliku za pośrednictwem aplikacji, należy użyć klasy <xref:System.IO.StreamWriter>. <xref:System.IO.StreamWriter> jest przeznaczony do znakowania danych wyjściowych w określonym kodowaniu, podczas gdy Klasa <xref:System.IO.Stream> jest zaprojektowana dla danych wejściowych i wyjściowych bajtów. Użyj <xref:System.IO.StreamWriter> do zapisywania wierszy informacji w standardowym pliku tekstowym. Aby uzyskać więcej informacji na temat klasy <xref:System.IO.StreamWriter>, zobacz <xref:System.IO.StreamWriter>.

### <a name="to-add-writing-functionality"></a>Aby dodać funkcje pisania

1. Z menu **Widok** wybierz polecenie **kod** , aby otworzyć Edytor kodu.

2. Ponieważ aplikacja odwołuje się do przestrzeni nazw <xref:System.IO>, należy dodać następujące instrukcje na początku kodu przed deklaracją klasy dla formularza, która rozpoczyna się `Public Class Form1`.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Przed zapisaniem w pliku należy utworzyć wystąpienie klasy <xref:System.IO.StreamWriter>.

3. Z menu **Widok** wybierz polecenie **Projektant** , aby powrócić do **Projektant formularzy systemu Windows**. Kliknij dwukrotnie przycisk `Submit`, aby utworzyć procedurę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla przycisku, a następnie Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Zintegrowane środowisko programistyczne (IDE) programu Visual Studio powróci do edytora kodu i ustawi punkt wstawiania w ramach procedury obsługi zdarzeń, gdzie należy dodać kod.

1. Aby zapisać w pliku, użyj metody <xref:System.IO.StreamWriter.Write%2A> klasy <xref:System.IO.StreamWriter>. Dodaj poniższy kod bezpośrednio po `Dim fw As StreamWriter`. Nie musisz martwić się o wyjątek, który zostanie wygenerowany, jeśli plik nie zostanie znaleziony, ponieważ zostanie utworzony, jeśli jeszcze nie istnieje.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Upewnij się, że użytkownik nie może przesłać pustego wpisu, dodając Poniższy kod bezpośrednio po `Dim ReadString As String`.

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Ponieważ jest to Diary, użytkownik będzie chciał przypisać datę do każdego wpisu. Wstaw poniższy kod po `fw = New StreamWriter("C:\MyDiary.txt", True)`, aby ustawić zmienną `Today` do bieżącej daty.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Na koniec Dołącz kod, aby wyczyścić <xref:System.Windows.Forms.TextBox>. Dodaj następujący kod do zdarzenia <xref:System.Windows.Forms.Control.Click> `Clear` przycisku.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Dodawanie funkcji wyświetlania do Diary

W tej sekcji dodasz funkcję, która wyświetla najnowszy wpis w <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Możesz również dodać <xref:System.Windows.Forms.ComboBox>, w którym są wyświetlane różne wpisy, z których użytkownik może wybrać wpis, który ma być wyświetlany w <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Wystąpienie klasy <xref:System.IO.StreamReader> odczytuje z `MyDiary.txt`. Podobnie jak Klasa <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader> jest przeznaczona do użycia z plikami tekstowymi.

W tej części przewodnika Dodaj kontrolki z poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|formant|Właściwości|Wartości|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Widać**<br /><br /> **Zmienia**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Display`<br /><br /> **Wyświetlany**|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`GetEntries`<br /><br /> **Pobierz wpisy**|
|<xref:System.Windows.Forms.ComboBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Dostępny**|`PickEntries`<br /><br /> **Wybierz wpis**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Aby wypełnić pole kombi

1. @No__t_0 <xref:System.Windows.Forms.ComboBox> służy do wyświetlania dat, w których użytkownik przesyła każdy wpis, więc użytkownik może wybrać wpis z określonej daty. Utwórz procedurę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> do przycisku `GetEntries` i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie kliknij pozycję **Pobierz wpisy**. Kliknij strzałkę listy rozwijanej w <xref:System.Windows.Forms.ComboBox>, aby wyświetlić daty wejścia.

### <a name="to-choose-and-display-individual-entries"></a>Aby wybrać i wyświetlić poszczególne wpisy

1. Utwórz procedurę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla przycisku `Display` i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie prześlij wpis. Kliknij pozycję **Pobierz wpisy**, wybierz pozycję z <xref:System.Windows.Forms.ComboBox>, a następnie kliknij pozycję **Wyświetl**. Zawartość wybranego wpisu pojawia się w <xref:System.Windows.Forms.TextBox> `DisplayEntry`.

## <a name="enabling-users-to-delete-or-modify-entries"></a>Umożliwienie użytkownikom usuwania lub modyfikowania wpisów

Na koniec możesz dołączyć dodatkowe funkcje, które umożliwiają użytkownikom usuwanie i modyfikowanie wpisów przy użyciu przycisków `DeleteEntry` i `EditEntry`. Oba przyciski pozostają wyłączone, chyba że zostanie wyświetlony wpis.

Dodaj kontrolki w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|formant|Właściwości|Wartości|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Dostępny**|`DeleteEntry`<br /><br /> **Usuń wpis**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Dostępny**|`EditEntry`<br /><br /> **Edytuj wpis**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Dostępny**|`SubmitEdit`<br /><br /> **Prześlij edycję**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Aby włączyć usuwanie i modyfikowanie wpisów

1. Po `DisplayEntry.Text = ReadString` należy dodać następujący kod do zdarzenia <xref:System.Windows.Forms.Control.Click> `Display` przycisku.

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Utwórz procedurę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla przycisku `DeleteEntry` i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Gdy użytkownik wyświetla wpis, przycisk `EditEntry` zostanie włączony. Dodaj następujący kod do zdarzenia <xref:System.Windows.Forms.Control.Click> przycisku `Display` po `DisplayEntry.Text = ReadString`.

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Utwórz procedurę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla przycisku `EditEntry` i Dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Utwórz procedurę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla przycisku `SubmitEdit` i Dodaj następujący kod

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację. Kliknij pozycję **Pobierz wpisy**, wybierz pozycję, a następnie kliknij pozycję **Wyświetl**. Wpis zostanie wyświetlony w <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Kliknij pozycję **Edytuj wpis**. Wpis zostanie wyświetlony w <xref:System.Windows.Forms.TextBox> `Entry`. Edytuj wpis w <xref:System.Windows.Forms.TextBox> `Entry` i kliknij przycisk **Prześlij Edytuj**. Otwórz plik `MyDiary.txt`, aby potwierdzić korektę. Teraz wybierz wpis, a następnie kliknij pozycję **Usuń wpis**. Po potwierdzeniu <xref:System.Windows.Forms.MessageBox> żądania kliknij przycisk **OK**. Zamknij aplikację i Otwórz `MyDiary.txt`, aby potwierdzić usunięcie.

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Przewodniki](../../../../visual-basic/walkthroughs.md)
