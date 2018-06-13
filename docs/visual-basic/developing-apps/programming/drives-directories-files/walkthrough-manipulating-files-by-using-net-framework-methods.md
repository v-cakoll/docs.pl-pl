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
ms.openlocfilehash: 20150326308513325a9f1219de3e3023e6c5192b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592538"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Wskazówki: manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)
W tym przewodniku pokazano, jak otwieranie i Odczyt pliku przy użyciu <xref:System.IO.StreamReader> klasy, sprawdź, czy plik jest dostępny, wyszukaj ciąg w pliku do odczytu z wystąpieniem <xref:System.IO.StreamReader> klasy, a następnie zapisać do pliku przy użyciu <xref:System.IO.StreamWriter> klasy.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a>Tworzenie aplikacji  
 Uruchom program Visual Studio i rozpocząć projektu przez tworzenie formularza, którego użytkownik może zapisać do wskazanego pliku.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Na **pliku** menu, wybierz opcję **nowy projekt**.  
  
2.  W **nowy projekt** okienku, kliknij przycisk **aplikacji systemu Windows**.  
  
3.  W **nazwa** wpisz `MyDiary` i kliknij przycisk **OK**.  
  
     Visual Studio dodaje projekt do **Eksploratora rozwiązań**i **Projektant formularzy systemu Windows** otwiera.  
  
4.  Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.  
  
|**Obiekt**|**Właściwości**|**Wartość**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Submit`<br /><br /> **Prześlij wpis**|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Clear`<br /><br /> **Usuń wpis**|  
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **Wiele linii**|`Entry`<br /><br /> **Wprowadź inną.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Zapisywanie do pliku  
 Aby dodać możliwość zapisywania do pliku za pośrednictwem aplikacji, użyj <xref:System.IO.StreamWriter> klasy. <xref:System.IO.StreamWriter> jest przeznaczony dla danych wyjściowych znak, przy użyciu określonego kodowania, natomiast <xref:System.IO.Stream> klasy jest przeznaczona dla bajtu danych wejściowych i wyjściowych. Użyj <xref:System.IO.StreamWriter> dla liniami informacji do pliku tekstowego standardowa. Aby uzyskać więcej informacji na temat <xref:System.IO.StreamWriter> , zobacz <xref:System.IO.StreamWriter>.  
  
#### <a name="to-add-writing-functionality"></a>Aby dodać funkcję zapisywania  
  
1.  Z **widoku** menu, wybierz **kod** można otworzyć edytora kodu.  
  
2.  Ponieważ aplikacja odwołuje się <xref:System.IO> przestrzeni nazw, Dodaj następujące instrukcje na samym początku kodu, przed deklaracją klasy formularza, który rozpoczyna się `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     Przed zapisaniem do pliku, należy utworzyć wystąpienie <xref:System.IO.StreamWriter> klasy.  
  
3.  Z **widoku** menu, wybierz **projektanta** aby powrócić do **Projektant formularzy systemu Windows**. Kliknij dwukrotnie `Submit` przycisk, aby utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla przycisku, a następnie dodaj poniższy kod.  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  Visual Studio programowanie środowiska IDE (Integrated) będzie powrócić do edytora kodu i umieść punkt wstawiania w ramach programu obsługi zdarzeń, w którym należy dodać kodu.  
  
1.  Aby zapisać do pliku, należy użyć <xref:System.IO.StreamWriter.Write%2A> metody <xref:System.IO.StreamWriter> klasy. Dodaj poniższy kod bezpośrednio po `Dim fw As StreamWriter`. Nie trzeba się martwić się, że zostanie wygenerowany wyjątek, jeśli plik nie zostanie znaleziony, ponieważ zostanie utworzony, jeśli jeszcze nie istnieje.  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  Upewnij się, że użytkownik nie może przesłać pusty wpis, dodając następujący kod bezpośrednio po `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  Ponieważ jest to niedawno dzienniki, użytkownik będzie można przypisać do każdego wpisu datę. Wstaw następujący kod po `fw = New StreamWriter("C:\MyDiary.txt", True)` można ustawić zmiennej `Today` do bieżącej daty.  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  Na koniec należy dołączyć kod, aby wyczyścić <xref:System.Windows.Forms.TextBox>. Dodaj następujący kod do `Clear` przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a>Dodawanie funkcji wyświetlania do pamiętnik  
 W tej sekcji możesz dodać funkcja, która wyświetla najnowsze wpisy w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Można również dodać <xref:System.Windows.Forms.ComboBox> wyświetlającym poszczególnych wpisów i z którego użytkownik może wybrać wpis do wyświetlenia w `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Wystąpienie <xref:System.IO.StreamReader> klasy odczyty `MyDiary.txt`. Podobnie jak <xref:System.IO.StreamWriter> klasy <xref:System.IO.StreamReader> jest przeznaczony do użytku z plików tekstowych.  
  
 W tej sekcji tego przewodnika Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.  
  
|Formant|Właściwości|Wartości|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Nazwa**<br /><br /> **Widoczne**<br /><br /> **Rozmiar**<br /><br /> **Wiele linii**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`Display`<br /><br /> **Wyświetl**|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**|`GetEntries`<br /><br /> **Pobierz zapisy**|  
|<xref:System.Windows.Forms.ComboBox>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **włączone**|`PickEntries`<br /><br /> **Wybierz pozycję**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>Aby wypełnić pola kombi  
  
1.  `PickEntries` <xref:System.Windows.Forms.ComboBox> Służy do wyświetlania dat, na których użytkownik prześle każdego wpisu, więc użytkownik może wybrać wpis od określonej daty. Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń do `GetEntries` przycisk i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  Do testowania kodu, naciśnij klawisz F5, aby skompilować aplikację, a następnie kliknij przycisk **Pobierz zapisy**. Kliknij strzałkę listy rozwijanej w <xref:System.Windows.Forms.ComboBox> na potrzeby wyświetlania dat wpisu.  
  
#### <a name="to-choose-and-display-individual-entries"></a>Aby wybrać i wyświetlić poszczególne pozycje  
  
1.  Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `Display` przycisk i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  Do testowania kodu, naciśnij klawisz F5, aby skompilować aplikację, a następnie Prześlij wpis. Kliknij przycisk **Pobierz zapisy**, wybierz pozycję z <xref:System.Windows.Forms.ComboBox>, a następnie kliknij przycisk **wyświetlania**. Zawartość wybranego wpisu jest wyświetlana w `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Umożliwienie użytkownikom do usunięcia lub zmodyfikowania wpisów  
 Ponadto może zawierać dodatkowe funkcje umożliwia użytkownikom usunąć ani zmodyfikować wpis za pomocą `DeleteEntry` i `EditEntry` przycisków. Przyciski pozostaną wyłączone, chyba że wpis jest wyświetlany.  
  
 Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.  
  
|Formant|Właściwości|Wartości|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **włączone**|`DeleteEntry`<br /><br /> **Usuń wpis**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **włączone**|`EditEntry`<br /><br /> **Edytuj wpis**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nazwa**<br /><br /> **Tekst**<br /><br /> **włączone**|`SubmitEdit`<br /><br /> **Zatwierdź Edytuj**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>Aby włączyć, usuwanie i modyfikowanie wpisów  
  
1.  Dodaj następujący kod do `Display` przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń, po `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `DeleteEntry` przycisk i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  Gdy użytkownik wyświetla wpis `EditEntry` przycisk staje się dostępny. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> zdarzenie `Display` przycisku po `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `EditEntry` przycisk i Dodaj następujący kod.  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `SubmitEdit` przycisk i Dodaj następujący kod  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 Do testowania kodu, naciśnij klawisz F5, aby skompilować aplikację. Kliknij przycisk **Pobierz zapisy**, wybierz wpis, a następnie kliknij przycisk **wyświetlania**. Wpis zostanie wyświetlony `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Kliknij przycisk **Edytuj wpis**. Wpis zostanie wyświetlony `Entry` <xref:System.Windows.Forms.TextBox>. Edytuj wpis w `Entry` <xref:System.Windows.Forms.TextBox> i kliknij przycisk **przesłać Edytuj**. Otwórz `MyDiary.txt` plik, aby potwierdzić poprawki. Teraz wybierz wpis i kliknij przycisk **Usuń wpis**. Gdy <xref:System.Windows.Forms.MessageBox> zażąda potwierdzenia, kliknij przycisk **OK**. Zamknij aplikację i otworzyć `MyDiary.txt` aby potwierdzić usunięcie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamWriter>  
 [Przewodniki](../../../../visual-basic/walkthroughs.md)
