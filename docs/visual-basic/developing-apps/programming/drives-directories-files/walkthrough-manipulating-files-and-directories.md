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
ms.openlocfilehash: ab1c119d2c5cd9bfa0ff725774144bc65817cad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592512"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Wskazówki: manipulowanie plikami i katalogami w Visual Basic
Ten przewodnik zawiera wprowadzenie do podstawy we/wy pliku w Visual Basic. Przedstawiono sposób tworzenie małych aplikacji, która zawiera listę i sprawdza, czy pliki tekstowe w katalogu. Dla każdego pliku zaznaczonego tekstu aplikacja udostępnia Atrybuty pliku i pierwszego wiersza zawartości. Ma opcji, aby zapisać informacje o pliku dziennika.  
  
 W tym przewodniku zastosowano członkami `My.Computer.FileSystem Object`, które są dostępne w języku Visual Basic. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na końcu tego przewodnika, odpowiednik przykład została podana używającą klas z <xref:System.IO> przestrzeni nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Na **pliku** menu, kliknij przycisk **nowy projekt**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  W **zainstalowane szablony** okienku rozwiń **Visual Basic**, a następnie kliknij przycisk **Windows**. W **szablony** w środkowej, kliknij w okienku **aplikacji Windows Forms**.  
  
3.  W **nazwa** wpisz `FileExplorer` Ustaw nazwę projektu, a następnie kliknij przycisk **OK**.  
  
     Visual Studio dodaje projekt do **Eksploratora rozwiązań**, i otwiera Projektant formularzy systemu Windows.  
  
4.  Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.  
  
    |Formant|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Nazwa**|`filesListBox`|  
    |**Przycisk**|**Nazwa**<br /><br /> **Tekst**|`browseButton`<br /><br /> **Przeglądaj**|  
    |**Przycisk**|**Nazwa**<br /><br /> **Tekst**|`examineButton`<br /><br /> **Sprawdź**|  
    |**CheckBox**|**Nazwa**<br /><br /> **Tekst**|`saveCheckBox`<br /><br /> **Zapisz wyniki**|  
    |**FolderBrowserDialog —**|**Nazwa**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Wybierz folder, oraz wyświetlanie listy plików w folderze  
  
1.  Utwórz `Click` programu obsługi zdarzeń dla `browseButton` przez dwukrotne kliknięcie formantu w formularzu. Edytor kodu.  
  
2.  Dodaj następujący kod do `Click` obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     `FolderBrowserDialog1.ShowDialog` Wywołać otwiera **przeglądanie w poszukiwaniu folderu** okno dialogowe. Gdy użytkownik kliknie **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwości są wysyłane jako argument `ListFiles` — metoda, która jest dodawana w następnym kroku.  
  
3.  Dodaj następujące `ListFiles` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     Ten kod najpierw wyczyści **ListBox**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pobiera następnie kolekcji ciągów, po jednej dla każdego pliku w katalogu. `GetFiles` Metoda przyjmuje argument wzorzec wyszukiwania, pobierania plików, które jest zgodny z określonym wzorcem. W tym przykładzie zwracane są tylko pliki mające rozszerzenie .txt.  
  
     Ciągi, które są zwracane przez `GetFiles` metody jest następnie dodawana do **ListBox**.  
  
4.  Uruchom aplikację. Kliknij przycisk **Przeglądaj** przycisku. W **przeglądanie w poszukiwaniu folderu** okno dialogowe, przejdź do folderu, który zawiera pliki txt, a następnie wybierz folder i kliknij przycisk **OK**.  
  
     `ListBox` Zawiera listę plików txt w wybranym folderze.  
  
5.  Przestaną działać aplikacja.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Aby uzyskać atrybuty pliku i zawartości z pliku tekstowego  
  
1.  Utwórz `Click` programu obsługi zdarzeń dla `examineButton` przez dwukrotne kliknięcie formantu w formularzu.  
  
2.  Dodaj następujący kod do `Click` obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     Kod sprawdza, czy element jest wybrany w `ListBox`. Następnie uzyskuje wpis ścieżkę pliku z `ListBox`. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda służy do sprawdzenia, czy plik nadal istnieje.  
  
     Ścieżka pliku jest wysyłany jako argument `GetTextForOutput` — metoda, która jest dodawana w następnym kroku. Ta metoda zwraca ciąg, który zawiera informacje o pliku. Informacje o pliku, który jest wyświetlany w **MessageBox**.  
  
3.  Dodaj następujące `GetTextForOutput` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     W kodzie użyto <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metody do uzyskania pliku parametrów. Parametry pliku są dodawane do <xref:System.Text.StringBuilder>.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda odczytuje zawartość pliku do <xref:System.IO.StreamReader>. Pierwszy wiersz zawartości są uzyskiwane z `StreamReader` oraz dodawane do `StringBuilder`.  
  
4.  Uruchom aplikację. Kliknij przycisk **Przeglądaj**, a następnie przejdź do folderu zawierającego pliki txt. Kliknij przycisk **OK**.  
  
     Wybierz plik w `ListBox`, a następnie kliknij przycisk **Sprawdź**. A `MessageBox` zawiera informacje o pliku.  
  
5.  Przestaną działać aplikacja.  
  
### <a name="to-add-a-log-entry"></a>Aby dodać wpis dziennika  
  
1.  Dodaj następujący kod na końcu `examineButton_Click` obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     Kod ustawia ścieżkę do pliku można umieścić w pliku dziennika w tym samym katalogu co wybranego pliku. Tekst wpisu dziennika jest ustawiona na bieżącą datę i godzinę następuje informacje o pliku.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody z `append` argument wartość `True`, jest używany do utworzenia wpisu dziennika.  
  
2.  Uruchom aplikację. Przejdź do pliku tekstowego, wybierz ją w `ListBox`, wybierz pozycję **Zapisz wyniki** pole wyboru, a następnie kliknij przycisk **Sprawdź**. Sprawdź, czy wpis dziennika są zapisywane `log.txt` pliku.  
  
3.  Przestaną działać aplikacja.  
  
### <a name="to-use-the-current-directory"></a>Aby użyć bieżącego katalogu  
  
1.  Tworzenie procedury obsługi zdarzeń dla `Form1_Load` przez dwukrotne kliknięcie formularza.  
  
2.  Dodaj następujący kod do obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     Ten kod ustawia domyślny katalog przeglądarki folderu do bieżącego katalogu.  
  
3.  Uruchom aplikację. Po kliknięciu **Przeglądaj** po raz pierwszy, **przeglądanie w poszukiwaniu folderu** zostanie otwarte okno dialogowe do bieżącego katalogu.  
  
4.  Przestaną działać aplikacja.  
  
### <a name="to-selectively-enable-controls"></a>Aby włączyć formantów  
  
1.  Dodaj następujące `SetEnabled` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     `SetEnabled` Metoda włącza lub wyłącza formantów w zależności od tego, czy element jest wybrany w `ListBox`.  
  
2.  Utwórz `SelectedIndexChanged` programu obsługi zdarzeń dla `filesListBox` przez dwukrotne kliknięcie `ListBox` formantu w formularzu.  
  
3.  Dodaj wywołanie do `SetEnabled` w nowym `filesListBox_SelectedIndexChanged` obsługi zdarzeń.  
  
4.  Dodaj wywołanie do `SetEnabled` na końcu `browseButton_Click` obsługi zdarzeń.  
  
5.  Dodaj wywołanie do `SetEnabled` na końcu `Form1_Load` obsługi zdarzeń.  
  
6.  Uruchom aplikację. **Zapisz wyniki** pole wyboru i **Sprawdź** przycisk są wyłączone, jeśli nie wybrano elementu `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Pełny przykład za pomocą My.Computer.FileSystem —  
 Poniżej znajduje się pełny przykład.  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a>Pełny przykład wykorzystania System.IO  
 W poniższym przykładzie równoważne użyto klas z <xref:System.IO> przestrzeni nazw zamiast `My.Computer.FileSystem` obiektów.  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [Przewodnik: manipulowanie plikami za pomocą metod .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
