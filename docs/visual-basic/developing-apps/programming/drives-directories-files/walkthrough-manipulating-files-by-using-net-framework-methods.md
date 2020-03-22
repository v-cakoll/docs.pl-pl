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

W tym przewodniku pokazano, jak otworzyć i <xref:System.IO.StreamReader> odczytać plik przy użyciu klasy, sprawdź, czy plik jest dostępny, wyszukaj ciąg w pliku odczytanego z wystąpieniem <xref:System.IO.StreamReader> klasy i zapisu do pliku przy użyciu <xref:System.IO.StreamWriter> klasy.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Tworzenie aplikacji

Uruchom program Visual Studio i rozpocznij projekt, tworząc formularz, którego użytkownik może użyć do zapisania w wyznaczonym pliku.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. W menu **Plik** wybierz polecenie **Nowy projekt**.

2. W okienku **Nowy projekt** kliknij pozycję Aplikacja **systemu Windows**.

3. W **Name** polu Nazwa `MyDiary` wpisz i kliknij przycisk **OK**.

     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań**i zostanie otwarty **projektant formularzy systemu Windows.**

4. Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|**Obiektu**|**Właściwości**|**Wartość**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Submit`<br /><br /> **Prześlij wpis**|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Clear`<br /><br /> **Wyczyść wpis**|
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Multiline**|`Entry`<br /><br /> **Proszę coś wpisać.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Zapisywanie do pliku

Aby dodać możliwość zapisu do pliku za <xref:System.IO.StreamWriter> pośrednictwem aplikacji, należy użyć klasy. <xref:System.IO.StreamWriter>jest przeznaczony do wyjścia znaków w określonym <xref:System.IO.Stream> kodowaniu, podczas gdy klasa jest przeznaczona dla wejścia i wyjścia bajtów. Służy <xref:System.IO.StreamWriter> do zapisywania wierszy informacji do standardowego pliku tekstowego. Aby uzyskać więcej <xref:System.IO.StreamWriter> informacji <xref:System.IO.StreamWriter>na temat klasy, zobacz .

### <a name="to-add-writing-functionality"></a>Aby dodać funkcje pisania

1. Z menu **Widok** wybierz pozycję **Kod,** aby otworzyć Edytor kodu.

2. Ponieważ aplikacja odwołuje <xref:System.IO> się do obszaru nazw, dodaj następujące instrukcje na samym początku kodu, `Public Class Form1`przed deklaracją klasy dla formularza, który rozpoczyna się.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Przed zapisaniem do pliku należy utworzyć <xref:System.IO.StreamWriter> wystąpienie klasy.

3. Z menu **Widok** wybierz polecenie **Projektant,** aby powrócić do **projektanta formularzy systemu Windows**. Kliknij dwukrotnie `Submit` przycisk, aby <xref:System.Windows.Forms.Control.Click> utworzyć program obsługi zdarzeń dla przycisku, a następnie dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Visual Studio zintegrowane środowisko programistyczne (IDE) powróci do Edytora kodu i umieść punkt wstawiania w programie obsługi zdarzeń, gdzie należy dodać kod.

1. Aby zapisać do pliku, <xref:System.IO.StreamWriter.Write%2A> należy <xref:System.IO.StreamWriter> użyć metody klasy. Dodaj następujący kod bezpośrednio `Dim fw As StreamWriter`po . Nie musisz się martwić, że wyjątek zostanie zgłoszony, jeśli plik nie zostanie znaleziony, ponieważ zostanie utworzony, jeśli jeszcze nie istnieje.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Upewnij się, że użytkownik nie może przesłać pustego `Dim ReadString As String`wpisu, dodając następujący kod bezpośrednio po .

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Ponieważ jest to dziennik, użytkownik będzie chciał przypisać datę do każdego wpisu. Wstaw następujący `fw = New StreamWriter("C:\MyDiary.txt", True)` kod po, `Today` aby ustawić zmienną na bieżącą datę.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Na koniec dołącz kod, <xref:System.Windows.Forms.TextBox>aby wyczyścić plik . Dodaj następujący kod `Clear` do zdarzenia <xref:System.Windows.Forms.Control.Click> przycisku.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Dodawanie funkcji wyświetlania do dziennika

W tej sekcji należy dodać funkcję, która `DisplayEntry` <xref:System.Windows.Forms.TextBox>wyświetla najnowszy wpis w pliku . Można również dodać, <xref:System.Windows.Forms.ComboBox> który wyświetla różne wpisy i z którego użytkownik `DisplayEntry` <xref:System.Windows.Forms.TextBox>może wybrać wpis do wyświetlenia w pliku . Wystąpienie <xref:System.IO.StreamReader> klasy odczytuje `MyDiary.txt`z . Podobnie <xref:System.IO.StreamWriter> jak <xref:System.IO.StreamReader> klasa, jest przeznaczony do użytku z plikami tekstowymi.

W tej sekcji instruktażu dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|Kontrola|Właściwości|Wartości|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Widoczne**<br /><br /> **Rozmiar**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Display`<br /><br /> **Wyświetlanie**|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`GetEntries`<br /><br /> **Pobierz wpisy**|
|<xref:System.Windows.Forms.ComboBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`PickEntries`<br /><br /> **Wybieranie wpisu**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Aby wypełnić pole kombi

1. Jest `PickEntries` <xref:System.Windows.Forms.ComboBox> używany do wyświetlania dat, w których użytkownik przesyła każdy wpis, dzięki czemu użytkownik może wybrać wpis z określonej daty. Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `GetEntries` zdarzeń do przycisku i dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie kliknij przycisk **Pobierz wpisy**. Kliknij strzałkę listy rozwijanej w celu <xref:System.Windows.Forms.ComboBox> wyświetlenia dat wejścia.

### <a name="to-choose-and-display-individual-entries"></a>Aby wybrać i wyświetlić poszczególne wpisy

1. Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `Display` zdarzeń dla przycisku i dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie prześlij wpis. Kliknij **pozycję Pobierz wpisy**, <xref:System.Windows.Forms.ComboBox>wybierz wpis z przycisku , a następnie kliknij przycisk **Wyświetl**. Zawartość wybranego wpisu pojawi `DisplayEntry` <xref:System.Windows.Forms.TextBox>się w pliku .

## <a name="enabling-users-to-delete-or-modify-entries"></a>Włączanie użytkownikom usuwania lub modyfikowania wpisów

Na koniec można dołączyć dodatkowe funkcje umożliwia użytkownikom, aby `DeleteEntry` `EditEntry` usunąć lub zmodyfikować wpis za pomocą i przycisków. Oba przyciski pozostają wyłączone, chyba że zostanie wyświetlony wpis.

Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.

|Kontrola|Właściwości|Wartości|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`DeleteEntry`<br /><br /> **Usuń wpis**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`EditEntry`<br /><br /> **Edytuj wpis**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Enabled (Włączony)**|`SubmitEdit`<br /><br /> **Prześlij edytuj**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Aby włączyć usuwanie i modyfikowanie wpisów

1. Dodaj następujący kod `Display` do <xref:System.Windows.Forms.Control.Click> zdarzenia przycisku, po . `DisplayEntry.Text = ReadString`

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `DeleteEntry` zdarzeń dla przycisku i dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Gdy użytkownik wyświetli wpis, `EditEntry` przycisk staje się włączony. Dodaj następujący kod <xref:System.Windows.Forms.Control.Click> do zdarzenia `Display` przycisku po `DisplayEntry.Text = ReadString`.

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `EditEntry` zdarzeń dla przycisku i dodaj następujący kod.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `SubmitEdit` zdarzeń dla przycisku i dodaj następujący kod

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację. Kliknij pozycję **Pobierz wpisy**, zaznacz wpis, a następnie kliknij pozycję **Wyświetl**. Wpis pojawi się `DisplayEntry` <xref:System.Windows.Forms.TextBox>w pliku . Kliknij **pozycję Edytuj wpis**. Wpis pojawi się `Entry` <xref:System.Windows.Forms.TextBox>w pliku . Edytuj wpis w `Entry` <xref:System.Windows.Forms.TextBox> i kliknij przycisk **Prześlij edytuj**. Otwórz `MyDiary.txt` plik, aby potwierdzić poprawek. Teraz wybierz wpis i kliknij przycisk **Usuń wpis**. Po <xref:System.Windows.Forms.MessageBox> potwierdzeniu żądań kliknij przycisk **OK**. Zamknij aplikację i `MyDiary.txt` otwórz, aby potwierdzić usunięcie.

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Przewodniki](../../../../visual-basic/walkthroughs.md)
