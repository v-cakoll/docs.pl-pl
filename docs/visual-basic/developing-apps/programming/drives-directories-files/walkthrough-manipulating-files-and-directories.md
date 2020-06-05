---
title: Manipulowanie plikami i katalogami
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
ms.openlocfilehash: 4b77618e5cd525cf3ad012405f402681aa5bb52c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406667"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Wskazówki: manipulowanie plikami i katalogami w Visual Basic

Ten Instruktaż zawiera wprowadzenie do podstawowych podstaw we/wy plików w Visual Basic. Opisano w nim sposób tworzenia małej aplikacji, która wyświetla i bada pliki tekstowe w katalogu. Dla każdego zaznaczonego pliku tekstowego aplikacja zawiera atrybuty pliku i pierwszy wiersz zawartości. Istnieje możliwość zapisu informacji w pliku dziennika.  
  
 W tym instruktażu są stosowane składniki programu `My.Computer.FileSystem Object` , które są dostępne w Visual Basic. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na końcu przewodnika jest dostarczany równoważny przykład, który używa klas z <xref:System.IO> przestrzeni nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1. W menu **plik** kliknij pozycję **Nowy projekt**.  
  
     Zostanie wyświetlone okno dialogowe **Nowy projekt**.  
  
2. W okienku **zainstalowane szablony** rozwiń węzeł **Visual Basic**, a następnie kliknij pozycję **Windows**. W okienku **Szablony** w środkowym kliknij pozycję **Windows Forms aplikacji**.  
  
3. W polu **Nazwa** wpisz `FileExplorer` nazwę projektu, a następnie kliknij przycisk **OK**.  
  
     Program Visual Studio dodaje projekt do **Eksplorator rozwiązań**, a Projektant formularzy systemu Windows zostanie otwarty.  
  
4. Dodaj kontrolki w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.  
  
    |Kontrola|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Nazwa**|`filesListBox`|  
    |**Przycisk**|**Nazwa**<br /><br /> **Tekst**|`browseButton`<br /><br /> **Przeglądaj**|  
    |**Przycisk**|**Nazwa**<br /><br /> **Tekst**|`examineButton`<br /><br /> **Sprawdzić**|  
    |**CheckBox**|**Nazwa**<br /><br /> **Tekst**|`saveCheckBox`<br /><br /> **Zapisz wyniki**|  
    |**FolderBrowserDialog**|**Nazwa**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Aby wybrać folder i wyświetlić listę plików w folderze  
  
1. Utwórz `Click` procedurę obsługi zdarzeń dla `browseButton` przez dwukrotne kliknięcie kontrolki w formularzu. Zostanie otwarty Edytor kodu.  
  
2. Dodaj następujący kod do `Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     `FolderBrowserDialog1.ShowDialog`Wywołanie otwiera okno dialogowe **przeglądanie w poszukiwaniu folderu** . Gdy użytkownik kliknie **przycisk OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> Właściwość jest wysyłana jako argument do `ListFiles` metody, która jest dodawana w następnym kroku.  
  
3. Dodaj następującą `ListFiles` metodę.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Ten kod najpierw czyści element **ListBox**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>Następnie Metoda pobiera kolekcję ciągów, po jednej dla każdego pliku w katalogu. `GetFiles`Metoda akceptuje argument wzorca wyszukiwania w celu pobrania plików zgodnych z określonym wzorcem. W tym przykładzie zwracane są tylko pliki z rozszerzeniem txt.  
  
     Ciągi zwracane przez `GetFiles` metodę są następnie dodawane do **pola listy**.  
  
4. Uruchom aplikację. Kliknij przycisk **Przeglądaj** . W oknie dialogowym **Przeglądaj w poszukiwaniu folderu** przejdź do folderu, który zawiera pliki. txt, a następnie wybierz folder, a następnie kliknij przycisk **OK**.  
  
     `ListBox`Zawiera listę plików txt w wybranym folderze.  
  
5. Zatrzymaj uruchamianie aplikacji.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Aby uzyskać atrybuty pliku oraz zawartość z pliku tekstowego  
  
1. Utwórz `Click` procedurę obsługi zdarzeń dla `examineButton` przez dwukrotne kliknięcie kontrolki w formularzu.  
  
2. Dodaj następujący kod do `Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kod sprawdza, czy element jest zaznaczony w `ListBox` . Następnie uzyskuje wpis ścieżki pliku z `ListBox` . <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>Metoda jest używana do sprawdzenia, czy plik nadal istnieje.  
  
     Ścieżka pliku jest wysyłana jako argument do `GetTextForOutput` metody, która jest dodawana w następnym kroku. Ta metoda zwraca ciąg, który zawiera informacje o pliku. Informacje o pliku są wyświetlane w elemencie **MessageBox**.  
  
3. Dodaj następującą `GetTextForOutput` metodę.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kod używa metody, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Aby uzyskać parametry pliku. Parametry pliku są dodawane do <xref:System.Text.StringBuilder> .  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>Metoda odczytuje zawartość pliku do <xref:System.IO.StreamReader> . Pierwszy wiersz zawartości jest uzyskiwany z `StreamReader` i zostaje dodany do `StringBuilder` .  
  
4. Uruchom aplikację. Kliknij przycisk **Przeglądaj**, a następnie przejdź do folderu, który zawiera pliki. txt. Kliknij przycisk **OK**.  
  
     Wybierz plik w `ListBox` , a następnie kliknij pozycję **Badaj**. A `MessageBox` wyświetla informacje o pliku.  
  
5. Zatrzymaj uruchamianie aplikacji.  
  
### <a name="to-add-a-log-entry"></a>Aby dodać wpis dziennika  
  
1. Dodaj następujący kod na końcu `examineButton_Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kod ustawia ścieżkę pliku dziennika, aby umieścić plik dziennika w tym samym katalogu co wybrany plik. Tekst wpisu dziennika jest ustawiany na bieżącą datę i godzinę oraz informacje o pliku.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Metoda, z `append` argumentem ustawionym na `True` , jest używana do tworzenia wpisu dziennika.  
  
2. Uruchom aplikację. Przejdź do pliku tekstowego, wybierz go w `ListBox` , zaznacz pole wyboru **Zapisz wyniki** , a następnie kliknij przycisk **Sprawdź**. Sprawdź, czy wpis dziennika jest zapisany w `log.txt` pliku.  
  
3. Zatrzymaj uruchamianie aplikacji.  
  
### <a name="to-use-the-current-directory"></a>Aby użyć bieżącego katalogu  
  
1. Utwórz procedurę obsługi zdarzeń dla `Form1_Load` przez dwukrotne kliknięcie formularza.  
  
2. Dodaj następujący kod do programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Ten kod ustawia domyślny katalog przeglądarki folderu w bieżącym katalogu.  
  
3. Uruchom aplikację. Po kliknięciu przycisku **Przeglądaj** zostanie otwarte okno dialogowe **przeglądanie w poszukiwaniu folderu** w bieżącym katalogu.  
  
4. Zatrzymaj uruchamianie aplikacji.  
  
### <a name="to-selectively-enable-controls"></a>Aby wybiórczo włączyć kontrolki  
  
1. Dodaj następującą `SetEnabled` metodę.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     `SetEnabled`Metoda włącza lub wyłącza kontrolki w zależności od tego, czy element jest zaznaczony w `ListBox` .  
  
2. Utwórz `SelectedIndexChanged` procedurę obsługi zdarzeń dla `filesListBox` przez dwukrotne kliknięcie `ListBox` kontrolki w formularzu.  
  
3. Dodaj wywołanie do `SetEnabled` programu w ramach nowego `filesListBox_SelectedIndexChanged` programu obsługi zdarzeń.  
  
4. Dodaj wywołanie do `SetEnabled` końca `browseButton_Click` procedury obsługi zdarzeń.  
  
5. Dodaj wywołanie do `SetEnabled` końca `Form1_Load` procedury obsługi zdarzeń.  
  
6. Uruchom aplikację. Pole wyboru **Zapisz wyniki** i przycisk **Sprawdź** są wyłączone, jeśli element nie jest zaznaczony w `ListBox` .  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Pełny przykład przy użyciu my. Computer. FileSystem  

 Poniżej znajduje się kompletny przykład.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Pełny przykład przy użyciu System.IO  

 Poniższy odpowiednik przykładu wykorzystuje klasy z <xref:System.IO> przestrzeni nazw zamiast używać `My.Computer.FileSystem` obiektów.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Przewodnik: Manipulowanie plikami za pomocą metod .NET Framework](walkthrough-manipulating-files-by-using-net-framework-methods.md)
