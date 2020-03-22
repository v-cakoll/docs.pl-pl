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
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333807"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Wskazówki: manipulowanie plikami i katalogami w Visual Basic

Ten przewodnik zawiera wprowadzenie do podstaw we/wy pliku w języku Visual Basic. Opisano w nim sposób tworzenia małej aplikacji, która wyświetla listę i sprawdza pliki tekstowe w katalogu. Dla każdego zaznaczonego pliku tekstowego aplikacja udostępnia atrybuty pliku i pierwszy wiersz zawartości. Istnieje możliwość zapisania informacji do pliku dziennika.  
  
 W tym instruktażu `My.Computer.FileSystem Object`użyto członków programu , które są dostępne w języku Visual Basic. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na końcu instruktażu podano równoważny przykład, który używa <xref:System.IO> klas z obszaru nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1. W menu **Plik** kliknij polecenie **Nowy projekt**.  
  
     Zostanie wyświetlone okno dialogowe **Nowy projekt**.  
  
2. W okienku **Zainstalowane szablony** rozwiń węzeł **Visual Basic**, a następnie kliknij pozycję **Windows**. W okienku **Szablony** w środku kliknij pozycję **Aplikacja formularzy systemu Windows**.  
  
3. W polu **Nazwa** `FileExplorer` wpisz, aby ustawić nazwę projektu, a następnie kliknij przycisk **OK**.  
  
     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań**i zostanie otwarty projektant formularzy systemu Windows.  
  
4. Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.  
  
    |Kontrola|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Nazwa**|`filesListBox`|  
    |**Przycisk**|**Nazwa**<br /><br /> **Tekst**|`browseButton`<br /><br /> **Przeglądaj**|  
    |**Przycisk**|**Nazwa**<br /><br /> **Tekst**|`examineButton`<br /><br /> **Zbadać**|  
    |**CheckBox**|**Nazwa**<br /><br /> **Tekst**|`saveCheckBox`<br /><br /> **Zapisz wyniki**|  
    |**Folderbrowserdialog**|**Nazwa**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Aby zaznaczyć folder i wyświetlić listę plików w folderze  
  
1. Utwórz `Click` program `browseButton` obsługi zdarzeń, klikając dwukrotnie formant w formularzu. Zostanie otwarty Edytor kodu.  
  
2. Dodaj następujący kod `Click` do programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     Połączenie `FolderBrowserDialog1.ShowDialog` zostanie otwarte w oknie dialogowym **Przeglądanie folderu.** Po kliknięciu **OK**przycisku <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> OK użytkownik jest wysyłany `ListFiles` jako argument do metody, która jest dodawana w następnym kroku.  
  
3. Dodaj następującą `ListFiles` metodę.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Ten kod najpierw czyści **ListBox**.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> następnie pobiera kolekcję ciągów, po jednym dla każdego pliku w katalogu. Metoda `GetFiles` akceptuje argument wzorca wyszukiwania, aby pobrać pliki, które pasują do określonego wzorca. W tym przykładzie zwracane są tylko pliki, które mają rozszerzenie .txt.  
  
     Ciągi, które są `GetFiles` zwracane przez metodę są następnie dodawane do **ListBox**.  
  
4. Uruchom aplikację. Kliknij przycisk **Przeglądaj.** W oknie dialogowym **Przeglądanie folderu** przejdź do folderu zawierającego pliki txt, a następnie wybierz folder i kliknij przycisk **OK**.  
  
     Zawiera `ListBox` listę plików txt w wybranym folderze.  
  
5. Przestań działać aplikację.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Aby uzyskać atrybuty pliku i zawartości z pliku tekstowego  
  
1. Utwórz `Click` program `examineButton` obsługi zdarzeń, klikając dwukrotnie formant w formularzu.  
  
2. Dodaj następujący kod `Click` do programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kod sprawdza, czy element jest `ListBox`zaznaczony w pliku . Następnie uzyskuje wpis ścieżki pliku `ListBox`z pliku . Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> jest używana do sprawdzania, czy plik nadal istnieje.  
  
     Ścieżka pliku jest wysyłana jako `GetTextForOutput` argument do metody, która jest dodawana w następnym kroku. Ta metoda zwraca ciąg, który zawiera informacje o pliku. Informacje o pliku są wyświetlane w **polu messagebox**.  
  
3. Dodaj następującą `GetTextForOutput` metodę.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kod używa metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> do uzyskania parametrów pliku. Parametry pliku są dodawane do pliku <xref:System.Text.StringBuilder>.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> odczytuje zawartość pliku <xref:System.IO.StreamReader>do pliku . Pierwszy wiersz zawartości jest otrzymywany `StreamReader` z i `StringBuilder`jest dodawany do pliku .  
  
4. Uruchom aplikację. Kliknij **pozycję Przeglądaj**i przejdź do folderu zawierającego pliki txt. Kliknij przycisk **OK**.  
  
     Zaznacz plik w `ListBox`pliku , a następnie kliknij przycisk **Sprawdź**. A `MessageBox` pokazuje informacje o pliku.  
  
5. Przestań działać aplikację.  
  
### <a name="to-add-a-log-entry"></a>Aby dodać wpis dziennika  
  
1. Dodaj następujący kod na końcu `examineButton_Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kod ustawia ścieżkę pliku dziennika, aby umieścić plik dziennika w tym samym katalogu, co w wybranym pliku. Tekst wpisu dziennika jest ustawiony na bieżącą datę i godzinę, po której następują informacje o pliku.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> z argumentem ustawionym na `append` , służy do `True`tworzenia wpisu dziennika.  
  
2. Uruchom aplikację. Przejdź do pliku tekstowego, zaznacz `ListBox`pole wyboru **Zapisz wyniki,** a następnie kliknij przycisk **Sprawdź**. Sprawdź, czy wpis dziennika jest `log.txt` zapisywany w pliku.  
  
3. Przestań działać aplikację.  
  
### <a name="to-use-the-current-directory"></a>Aby użyć bieżącego katalogu  
  
1. Utwórz program `Form1_Load` obsługi zdarzeń, klikając dwukrotnie formularz.  
  
2. Dodaj następujący kod do programu obsługi zdarzeń.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Ten kod ustawia domyślny katalog przeglądarki folderów na bieżący katalog.  
  
3. Uruchom aplikację. Po **kliknięciu przycisku Przeglądaj** po raz pierwszy zostanie otwarte okno dialogowe **Przeglądanie w poszukiwaniu folderu** w bieżącym katalogu.  
  
4. Przestań działać aplikację.  
  
### <a name="to-selectively-enable-controls"></a>Aby selektywnie włączyć formanty  
  
1. Dodaj następującą `SetEnabled` metodę.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     Metoda `SetEnabled` włącza lub wyłącza formanty w zależności `ListBox`od tego, czy element jest wybrany w programie .  
  
2. Utwórz `SelectedIndexChanged` program `filesListBox` obsługi zdarzeń, klikając `ListBox` dwukrotnie formant w formularzu.  
  
3. Dodaj wywołanie `SetEnabled` do `filesListBox_SelectedIndexChanged` w nowym programie obsługi zdarzeń.  
  
4. Dodaj wywołanie `SetEnabled` na końcu `browseButton_Click` programu obsługi zdarzeń.  
  
5. Dodaj wywołanie `SetEnabled` na końcu `Form1_Load` programu obsługi zdarzeń.  
  
6. Uruchom aplikację. Pole **wyboru Zapisz wyniki** i przycisk **Sprawdź** są wyłączone, `ListBox`jeśli element nie jest zaznaczony w polu .  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Pełny przykład przy użyciu systemu My.Computer.FileSystem  

 Oto pełny przykład.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Pełny przykład przy użyciu System.IO  

 Poniższy równoważny przykład używa <xref:System.IO> klas z obszaru `My.Computer.FileSystem` nazw zamiast obiektów.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Wskazówki: manipulowanie plikami za pomocą metod .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
