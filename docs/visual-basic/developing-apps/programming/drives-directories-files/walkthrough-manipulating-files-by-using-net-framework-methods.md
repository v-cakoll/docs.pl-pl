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
ms.openlocfilehash: fc96baaff3b70fcb32e19e2ce08bdb0187c86c01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783201"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Przewodnik: Manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)
W tym instruktażu pokazano, jak otwieranie i Odczyt pliku przy użyciu <xref:System.IO.StreamReader> klasy, sprawdź, jeśli plik jest dostępny, wyszukiwanie ciągu w pliku odczytu z wystąpieniem <xref:System.IO.StreamReader> klasy, a następnie zapisać do pliku za pomocą <xref:System.IO.StreamWriter> klasy.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a>Tworzenie aplikacji  
 Uruchom program Visual Studio i rozpocząć projektu, tworząc formularz, który użytkownik może użyć do zapisu do wskazanego pliku.  
  
### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1. Na **pliku** menu, wybierz opcję **nowy projekt**.  
  
2. W **nowy projekt** okienku kliknij **aplikacji Windows**.  
  
3. W **nazwa** wpisz `MyDiary` i kliknij przycisk **OK**.  
  
     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań**i **Windows Forms Designer** zostanie otwarty.  
  
4. Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości ich właściwości.  
  
|**Obiekt**|**Właściwości**|**Wartość**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Text**|`Submit`<br /><br /> **Prześlij wpis**|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Text**|`Clear`<br /><br /> **Wyczyść wpis**|  
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Text**<br /><br /> **Wielowierszowy**|`Entry`<br /><br /> **Podaj nazwę elementu.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Zapisywanie do pliku  
 Aby dodać możliwość zapisu do pliku za pośrednictwem aplikacji, użyj <xref:System.IO.StreamWriter> klasy. <xref:System.IO.StreamWriter> jest przeznaczona dla danych wyjściowych znaków, przy użyciu określonego kodowania, natomiast <xref:System.IO.Stream> klasa jest przeznaczona do obsługi bajtowych danych wejściowych i wyjściowych. Użyj <xref:System.IO.StreamWriter> dla liniami informacji do pliku tekstowego standardowych. Aby uzyskać więcej informacji na temat <xref:System.IO.StreamWriter> klasy, zobacz <xref:System.IO.StreamWriter>.  
  
### <a name="to-add-writing-functionality"></a>Aby dodać funkcję zapisywania  
  
1. Z **widoku** menu, wybierz **kodu** można otworzyć edytora kodu.  
  
2. Ponieważ aplikacja odwołuje się do <xref:System.IO> przestrzeni nazw, Dodaj następujące instrukcje na samym początku kodu, przed deklaracją klasy, formularza, która rozpoczyna się `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]  
  
     Przed zapisaniem pliku, należy utworzyć wystąpienie <xref:System.IO.StreamWriter> klasy.  
  
3. Z **widoku** menu, wybierz **projektanta** aby powrócić do **Windows Forms Designer**. Kliknij dwukrotnie `Submit` przycisk, aby utworzyć <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla przycisku, a następnie dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]  
  
> [!NOTE]
>  Visual Studio rozwoju środowiska IDE (Integrated) będą powrócić do edytora kodu i umieść punkt wstawiania wewnątrz procedury obsługi zdarzeń, w którym należy dodać kod.  
  
1. Aby zapisać do pliku, należy użyć <xref:System.IO.StreamWriter.Write%2A> metody <xref:System.IO.StreamWriter> klasy. Dodaj poniższy kod bezpośrednio po `Dim fw As StreamWriter`. Nie trzeba martwić się, że wyjątek zostanie zgłoszony, jeśli plik nie zostanie znaleziony, ponieważ zostanie utworzony, jeśli jeszcze nie istnieje.  
  
     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]  
  
2. Upewnij się, że użytkownik nie może przesłać jest puste, dodając poniższy kod bezpośrednio po `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]  
  
3. Ponieważ niedawno dzienniki użytkownika chcesz przypisać wartość typu date do każdego wpisu. Wstaw następujący kod po `fw = New StreamWriter("C:\MyDiary.txt", True)` było ustawiać zmiennej `Today` do bieżącej daty.  
  
     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]  
  
4. Na koniec należy dołączyć kod, aby wyczyścić <xref:System.Windows.Forms.TextBox>. Dodaj następujący kod do `Clear` przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]  
  
## <a name="adding-display-features-to-the-diary"></a>Dodawanie funkcji wyświetlania do pamiętnik  
 W tej sekcji dodasz funkcję, która zawiera najnowszy wpis w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Można również dodać <xref:System.Windows.Forms.ComboBox> wyświetlającym poszczególnych wpisów i z którego użytkownik może wybrać wpis do wyświetlenia w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Wystąpienie <xref:System.IO.StreamReader> klasy odczyty `MyDiary.txt`. Podobnie jak <xref:System.IO.StreamWriter> klasy <xref:System.IO.StreamReader> jest przeznaczony do użytku z plików tekstowych.  
  
 W tej sekcji tego przewodnika Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości ich właściwości.  
  
|formant|Właściwości|Wartości|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Widoczne**<br /><br /> **Rozmiar**<br /><br /> **Wielowierszowy**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Text**|`Display`<br /><br /> **Wyświetlanie**|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Text**|`GetEntries`<br /><br /> **Pobieranie wpisów**|  
|<xref:System.Windows.Forms.ComboBox>|**Nazwa**<br /><br /> **Text**<br /><br /> **Włączone**|`PickEntries`<br /><br /> **Wybierz pozycję**<br /><br /> `False`|  
  
### <a name="to-populate-the-combo-box"></a>Aby wypełnić pola kombi.  
  
1. `PickEntries` <xref:System.Windows.Forms.ComboBox> Jest używany na potrzeby wyświetlania dat, w których użytkownik prześle każdego wpisu, dzięki czemu użytkownik może wybrać wpis z określonej daty. Tworzenie <xref:System.Windows.Forms.Control.Click> procedurę obsługi zdarzeń do `GetEntries` przycisku i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]  
  
2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie kliknij przycisk **Pobierz zapisy**. Kliknij strzałkę listy rozwijanej w <xref:System.Windows.Forms.ComboBox> na potrzeby wyświetlania dat wpisu.  
  
### <a name="to-choose-and-display-individual-entries"></a>Aby wybrać i wyświetlić poszczególne wpisy  
  
1. Tworzenie <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `Display` przycisku i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]  
  
2. Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie Prześlij wpis. Kliknij przycisk **Pobierz zapisy**, wybierz pozycję z <xref:System.Windows.Forms.ComboBox>, a następnie kliknij przycisk **wyświetlania**. Zawartość wybranego wpisu jest wyświetlana w `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Umożliwienie użytkownikom usunąć lub zmodyfikować wpisów  
 Na koniec może obejmować użytkowników umożliwia dodatkowe funkcje, aby usunąć lub zmodyfikować wpis, za pomocą `DeleteEntry` i `EditEntry` przycisków. Przyciski pozostaną wyłączone, chyba że jest wyświetlana.  
  
 Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości ich właściwości.  
  
|formant|Właściwości|Wartości|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Text**<br /><br /> **Włączone**|`DeleteEntry`<br /><br /> **Usuń wpis**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Text**<br /><br /> **Włączone**|`EditEntry`<br /><br /> **Edytuj wpis**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Text**<br /><br /> **Włączone**|`SubmitEdit`<br /><br /> **Prześlij edycji**<br /><br /> `False`|  
  
### <a name="to-enable-deletion-and-modification-of-entries"></a>Aby włączyć usuwanie i modyfikowanie wpisów  
  
1. Dodaj następujący kod do `Display` przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń po `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]  
  
2. Tworzenie <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `DeleteEntry` przycisku i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]  
  
3. Gdy użytkownik wyświetla wpis `EditEntry` przycisk staje się dostępny. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> zdarzenia `Display` przycisku po `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]  
  
4. Tworzenie <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `EditEntry` przycisku i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]  
  
5. Tworzenie <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `SubmitEdit` przycisku i Dodaj następujący kod  
  
     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]  
  
 Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację. Kliknij przycisk **Pobierz zapisy**, wybierz wpis, a następnie kliknij **wyświetlania**. Wpis zostanie wyświetlony w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Kliknij przycisk **Edytuj wpis**. Wpis zostanie wyświetlony w `Entry` <xref:System.Windows.Forms.TextBox>. Edytuj wpis w `Entry` <xref:System.Windows.Forms.TextBox> i kliknij przycisk **przesyłania edycji**. Otwórz `MyDiary.txt` plik, aby potwierdzić poprawny. Wybierz wpis i kliknij **Usuń wpis**. Gdy <xref:System.Windows.Forms.MessageBox> zażąda potwierdzenia, kliknij przycisk **OK**. Zamknij aplikację i Otwórz `MyDiary.txt` o potwierdzenie usunięcia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Przewodniki](../../../../visual-basic/walkthroughs.md)
