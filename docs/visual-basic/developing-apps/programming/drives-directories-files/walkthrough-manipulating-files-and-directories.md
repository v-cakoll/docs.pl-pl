---
title: Manipulowanie plikami i katalogami w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 4d0aac533759f8cc20ac4f19d7f0e49fef17bf56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052524"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Przewodnik: Manipulowanie plikami i katalogami w Visual Basic
Ten przewodnik zawiera wprowadzenie do podstaw we/wy pliku w Visual Basic. Ją opisuje sposób tworzenia mała aplikacja, która zawiera listę i sprawdza, czy pliki tekstowe, w katalogu. Dla każdego pliku zaznaczony tekst aplikacji zawiera atrybuty pliku i pierwszego wiersza zawartości. Istnieje możliwość zapisywania informacji w pliku dziennika.  
  
 W tym instruktażu wykorzystano członkowie `My.Computer.FileSystem Object`, które są dostępne w języku Visual Basic. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na końcu tego przewodnika, równoważne to na przykład pod warunkiem, że używa klasy z <xref:System.IO> przestrzeni nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1. Na **pliku** menu, kliknij przycisk **nowy projekt**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2. W **zainstalowane szablony** okienku rozwiń **języka Visual Basic**, a następnie kliknij przycisk **Windows**. W **szablony** okienku kliknięcie środkowym przyciskiem myszy, **aplikacja interfejsu Windows Forms**.  
  
3. W **nazwa** wpisz `FileExplorer` Ustaw nazwę projektu, a następnie kliknij przycisk **OK**.  
  
     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań**, i otwiera Windows Forms Designer.  
  
4. Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości ich właściwości.  
  
    |formant|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Nazwa**|`filesListBox`|  
    |**Przycisk**|**Nazwa**<br /><br /> **Text**|`browseButton`<br /><br /> **Przeglądaj**|  
    |**Przycisk**|**Nazwa**<br /><br /> **Text**|`examineButton`<br /><br /> **Sprawdź**|  
    |**CheckBox**|**Nazwa**<br /><br /> **Text**|`saveCheckBox`<br /><br /> **Zapisz wyniki**|  
    |**FolderBrowserDialog**|**Nazwa**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Wybierz folder i wyświetlać listę plików w folderze  
  
1. Tworzenie `Click` program obsługi zdarzeń dla `browseButton` przez dwukrotne kliknięcie formantu w formularzu. Zostanie otwarty Edytor kodu.  
  
2. Dodaj następujący kod do `Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     `FolderBrowserDialog1.ShowDialog` Wywołanie zostanie otwarta **przeglądanie w poszukiwaniu folderu** okno dialogowe. Po użytkownik klika **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwość jest wysyłany jako argument do `ListFiles` metody, która jest dodawana w następnym kroku.  
  
3. Dodaj następujący kod `ListFiles` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Ten kod najpierw wyczyści **ListBox**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pobiera następnie Kolekcja ciągów, jeden dla każdego pliku w katalogu. `GetFiles` Metoda przyjmuje argumentu pattern wyszukiwania, aby pobrać pliki, które pasują do wzorca określonego. W tym przykładzie zwracane są tylko pliki mające rozszerzenie .txt.  
  
     Ciągi, które są zwracane przez `GetFiles` metody zostaną następnie dodane do **ListBox**.  
  
4. Uruchom aplikację. Kliknij przycisk **Przeglądaj** przycisku. W **przeglądanie w poszukiwaniu folderu** okno dialogowe, przejdź do folderu, który zawiera pliki txt, wybierz folder, a następnie kliknij polecenie **OK**.  
  
     `ListBox` Zawiera listę plików txt w wybranym folderze.  
  
5. Zatrzymywanie, uruchamianie aplikacji.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Aby uzyskać atrybuty pliku i zawartości z pliku tekstowego  
  
1. Tworzenie `Click` program obsługi zdarzeń dla `examineButton` przez dwukrotne kliknięcie formantu w formularzu.  
  
2. Dodaj następujący kod do `Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kod sprawdza, czy element jest zaznaczony na `ListBox`. Następnie uzyskuje wpis ścieżki pliku z `ListBox`. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda jest używana w celu sprawdzenia, czy plik nadal istnieje.  
  
     Ścieżka pliku jest wysyłany jako argument do `GetTextForOutput` metody, która jest dodawana w następnym kroku. Ta metoda zwraca ciąg, który zawiera informacje o pliku. Informacje o pliku, który pojawia się w **MessageBox**.  
  
3. Dodaj następujący kod `GetTextForOutput` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kod używa <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metodę, aby uzyskać plik parametrów. Parametry pliku są dodawane do <xref:System.Text.StringBuilder>.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda odczytuje zawartość pliku do <xref:System.IO.StreamReader>. Pierwszy wiersz zawartości jest uzyskiwana z `StreamReader` i jest dodawany do `StringBuilder`.  
  
4. Uruchom aplikację. Kliknij przycisk **Przeglądaj**, a następnie przejdź do folderu zawierającego pliki txt. Kliknij przycisk **OK**.  
  
     Wybierz plik w `ListBox`, a następnie kliknij przycisk **Sprawdź**. Element `MessageBox` zawiera informacje o pliku.  
  
5. Zatrzymywanie, uruchamianie aplikacji.  
  
### <a name="to-add-a-log-entry"></a>Aby dodać wpis dziennika  
  
1. Dodaj następujący kod na końcu `examineButton_Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kod ustawia ścieżka pliku dziennika, aby umieścić ten plik dziennika w tym samym katalogu co w przypadku wybranego pliku. Tekst wpisu dziennika jest ustawiona na bieżącą datę i godzinę, o których następuje informacji o pliku.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda, za pomocą `append` argument wartość `True`, służy do tworzenia wpisu dziennika.  
  
2. Uruchom aplikację. Przejdź do pliku tekstowego, wybierz ją w `ListBox`, wybierz opcję **Zapisz wyniki** pole wyboru, a następnie kliknij przycisk **Sprawdź**. Sprawdź, czy wpis dziennika są zapisywane do `log.txt` pliku.  
  
3. Zatrzymywanie, uruchamianie aplikacji.  
  
### <a name="to-use-the-current-directory"></a>Aby użyć bieżącego katalogu  
  
1. Utwórz procedurę obsługi zdarzeń dla `Form1_Load` przez dwukrotne kliknięcie formularza.  
  
2. Dodaj następujący kod do narzędzia obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Ten kod ustawia domyślny katalog przeglądarkę folderów w bieżącym katalogu.  
  
3. Uruchom aplikację. Po kliknięciu **Przeglądaj** po raz pierwszy, **przeglądanie w poszukiwaniu folderu** zostanie otwarte okno dialogowe w bieżącym katalogu.  
  
4. Zatrzymywanie, uruchamianie aplikacji.  
  
### <a name="to-selectively-enable-controls"></a>Aby selektywnie włączyć kontrolki  
  
1. Dodaj następujący kod `SetEnabled` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     `SetEnabled` Metoda włącza lub wyłącza kontrolek, w zależności od tego, czy element jest zaznaczony na `ListBox`.  
  
2. Tworzenie `SelectedIndexChanged` program obsługi zdarzeń dla `filesListBox` przez dwukrotne kliknięcie `ListBox` formant w formularzu.  
  
3. Dodaj wywołanie do `SetEnabled` w nowym `filesListBox_SelectedIndexChanged` programu obsługi zdarzeń.  
  
4. Dodaj wywołanie do `SetEnabled` na końcu `browseButton_Click` programu obsługi zdarzeń.  
  
5. Dodaj wywołanie do `SetEnabled` na końcu `Form1_Load` programu obsługi zdarzeń.  
  
6. Uruchom aplikację. **Zapisz wyniki** pole wyboru i **Sprawdź** przycisk są wyłączone, jeśli element nie jest wybrane w `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Pełny przykład za pomocą My.Computer.FileSystem  
 Oto kompletny przykład.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Pełny przykład za pomocą System.IO  
 W poniższym przykładzie równoważne użyto klas z <xref:System.IO> przestrzeni nazw, zamiast `My.Computer.FileSystem` obiektów.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Przewodnik: Manipulowanie plikami za pomocą metod .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
