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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314688"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="0f701-102">Przewodnik: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f701-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="0f701-103">Ten przewodnik zawiera wprowadzenie do podstaw we/wy pliku w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f701-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="0f701-104">Ją opisuje sposób tworzenia mała aplikacja, która zawiera listę i sprawdza, czy pliki tekstowe, w katalogu.</span><span class="sxs-lookup"><span data-stu-id="0f701-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="0f701-105">Dla każdego pliku zaznaczony tekst aplikacji zawiera atrybuty pliku i pierwszego wiersza zawartości.</span><span class="sxs-lookup"><span data-stu-id="0f701-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="0f701-106">Istnieje możliwość zapisywania informacji w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="0f701-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="0f701-107">W tym instruktażu wykorzystano członkowie `My.Computer.FileSystem Object`, które są dostępne w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f701-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="0f701-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="0f701-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="0f701-109">Na końcu tego przewodnika, równoważne to na przykład pod warunkiem, że używa klasy z <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0f701-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="0f701-110">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="0f701-110">To create the project</span></span>  
  
1. <span data-ttu-id="0f701-111">Na **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="0f701-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="0f701-112">**Nowy projekt** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="0f701-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="0f701-113">W **zainstalowane szablony** okienku rozwiń **języka Visual Basic**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="0f701-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="0f701-114">W **szablony** okienku kliknięcie środkowym przyciskiem myszy, **aplikacja interfejsu Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="0f701-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="0f701-115">W **nazwa** wpisz `FileExplorer` Ustaw nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f701-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0f701-116">Program Visual Studio dodaje projekt do **Eksploratora rozwiązań**, i otwiera Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="0f701-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="0f701-117">Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="0f701-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="0f701-118">formant</span><span class="sxs-lookup"><span data-stu-id="0f701-118">Control</span></span>|<span data-ttu-id="0f701-119">Właściwość</span><span class="sxs-lookup"><span data-stu-id="0f701-119">Property</span></span>|<span data-ttu-id="0f701-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="0f701-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="0f701-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="0f701-121">**ListBox**</span></span>|<span data-ttu-id="0f701-122">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="0f701-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="0f701-123">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="0f701-123">**Button**</span></span>|<span data-ttu-id="0f701-124">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="0f701-124">**Name**</span></span><br /><br /> <span data-ttu-id="0f701-125">**Text**</span><span class="sxs-lookup"><span data-stu-id="0f701-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="0f701-126">**Przeglądaj**</span><span class="sxs-lookup"><span data-stu-id="0f701-126">**Browse**</span></span>|  
    |<span data-ttu-id="0f701-127">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="0f701-127">**Button**</span></span>|<span data-ttu-id="0f701-128">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="0f701-128">**Name**</span></span><br /><br /> <span data-ttu-id="0f701-129">**Text**</span><span class="sxs-lookup"><span data-stu-id="0f701-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="0f701-130">**Sprawdź**</span><span class="sxs-lookup"><span data-stu-id="0f701-130">**Examine**</span></span>|  
    |<span data-ttu-id="0f701-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="0f701-131">**CheckBox**</span></span>|<span data-ttu-id="0f701-132">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="0f701-132">**Name**</span></span><br /><br /> <span data-ttu-id="0f701-133">**Text**</span><span class="sxs-lookup"><span data-stu-id="0f701-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="0f701-134">**Zapisz wyniki**</span><span class="sxs-lookup"><span data-stu-id="0f701-134">**Save Results**</span></span>|  
    |<span data-ttu-id="0f701-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="0f701-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="0f701-136">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="0f701-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="0f701-137">Wybierz folder i wyświetlać listę plików w folderze</span><span class="sxs-lookup"><span data-stu-id="0f701-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="0f701-138">Tworzenie `Click` program obsługi zdarzeń dla `browseButton` przez dwukrotne kliknięcie formantu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0f701-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="0f701-139">Zostanie otwarty Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="0f701-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="0f701-140">Dodaj następujący kod do `Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f701-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="0f701-141">`FolderBrowserDialog1.ShowDialog` Wywołanie zostanie otwarta **przeglądanie w poszukiwaniu folderu** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="0f701-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="0f701-142">Po użytkownik klika **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwość jest wysyłany jako argument do `ListFiles` metody, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="0f701-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="0f701-143">Dodaj następujący kod `ListFiles` metody.</span><span class="sxs-lookup"><span data-stu-id="0f701-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="0f701-144">Ten kod najpierw wyczyści **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="0f701-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="0f701-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pobiera następnie Kolekcja ciągów, jeden dla każdego pliku w katalogu.</span><span class="sxs-lookup"><span data-stu-id="0f701-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="0f701-146">`GetFiles` Metoda przyjmuje argumentu pattern wyszukiwania, aby pobrać pliki, które pasują do wzorca określonego.</span><span class="sxs-lookup"><span data-stu-id="0f701-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="0f701-147">W tym przykładzie zwracane są tylko pliki mające rozszerzenie .txt.</span><span class="sxs-lookup"><span data-stu-id="0f701-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="0f701-148">Ciągi, które są zwracane przez `GetFiles` metody zostaną następnie dodane do **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="0f701-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="0f701-149">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="0f701-149">Run the application.</span></span> <span data-ttu-id="0f701-150">Kliknij przycisk **Przeglądaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0f701-150">Click the **Browse** button.</span></span> <span data-ttu-id="0f701-151">W **przeglądanie w poszukiwaniu folderu** okno dialogowe, przejdź do folderu, który zawiera pliki txt, wybierz folder, a następnie kliknij polecenie **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f701-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="0f701-152">`ListBox` Zawiera listę plików txt w wybranym folderze.</span><span class="sxs-lookup"><span data-stu-id="0f701-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="0f701-153">Zatrzymywanie, uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f701-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="0f701-154">Aby uzyskać atrybuty pliku i zawartości z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="0f701-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="0f701-155">Tworzenie `Click` program obsługi zdarzeń dla `examineButton` przez dwukrotne kliknięcie formantu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0f701-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="0f701-156">Dodaj następujący kod do `Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f701-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="0f701-157">Kod sprawdza, czy element jest zaznaczony na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="0f701-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="0f701-158">Następnie uzyskuje wpis ścieżki pliku z `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="0f701-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="0f701-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda jest używana w celu sprawdzenia, czy plik nadal istnieje.</span><span class="sxs-lookup"><span data-stu-id="0f701-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="0f701-160">Ścieżka pliku jest wysyłany jako argument do `GetTextForOutput` metody, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="0f701-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="0f701-161">Ta metoda zwraca ciąg, który zawiera informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="0f701-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="0f701-162">Informacje o pliku, który pojawia się w **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="0f701-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="0f701-163">Dodaj następujący kod `GetTextForOutput` metody.</span><span class="sxs-lookup"><span data-stu-id="0f701-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="0f701-164">Kod używa <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metodę, aby uzyskać plik parametrów.</span><span class="sxs-lookup"><span data-stu-id="0f701-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="0f701-165">Parametry pliku są dodawane do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="0f701-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="0f701-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda odczytuje zawartość pliku do <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="0f701-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="0f701-167">Pierwszy wiersz zawartości jest uzyskiwana z `StreamReader` i jest dodawany do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="0f701-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="0f701-168">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="0f701-168">Run the application.</span></span> <span data-ttu-id="0f701-169">Kliknij przycisk **Przeglądaj**, a następnie przejdź do folderu zawierającego pliki txt.</span><span class="sxs-lookup"><span data-stu-id="0f701-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="0f701-170">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f701-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="0f701-171">Wybierz plik w `ListBox`, a następnie kliknij przycisk **Sprawdź**.</span><span class="sxs-lookup"><span data-stu-id="0f701-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="0f701-172">Element `MessageBox` zawiera informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="0f701-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="0f701-173">Zatrzymywanie, uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f701-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="0f701-174">Aby dodać wpis dziennika</span><span class="sxs-lookup"><span data-stu-id="0f701-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="0f701-175">Dodaj następujący kod na końcu `examineButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f701-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="0f701-176">Kod ustawia ścieżka pliku dziennika, aby umieścić ten plik dziennika w tym samym katalogu co w przypadku wybranego pliku.</span><span class="sxs-lookup"><span data-stu-id="0f701-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="0f701-177">Tekst wpisu dziennika jest ustawiona na bieżącą datę i godzinę, o których następuje informacji o pliku.</span><span class="sxs-lookup"><span data-stu-id="0f701-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="0f701-178"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda, za pomocą `append` argument wartość `True`, służy do tworzenia wpisu dziennika.</span><span class="sxs-lookup"><span data-stu-id="0f701-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="0f701-179">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="0f701-179">Run the application.</span></span> <span data-ttu-id="0f701-180">Przejdź do pliku tekstowego, wybierz ją w `ListBox`, wybierz opcję **Zapisz wyniki** pole wyboru, a następnie kliknij przycisk **Sprawdź**.</span><span class="sxs-lookup"><span data-stu-id="0f701-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="0f701-181">Sprawdź, czy wpis dziennika są zapisywane do `log.txt` pliku.</span><span class="sxs-lookup"><span data-stu-id="0f701-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="0f701-182">Zatrzymywanie, uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f701-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="0f701-183">Aby użyć bieżącego katalogu</span><span class="sxs-lookup"><span data-stu-id="0f701-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="0f701-184">Utwórz procedurę obsługi zdarzeń dla `Form1_Load` przez dwukrotne kliknięcie formularza.</span><span class="sxs-lookup"><span data-stu-id="0f701-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="0f701-185">Dodaj następujący kod do narzędzia obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f701-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="0f701-186">Ten kod ustawia domyślny katalog przeglądarkę folderów w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0f701-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="0f701-187">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="0f701-187">Run the application.</span></span> <span data-ttu-id="0f701-188">Po kliknięciu **Przeglądaj** po raz pierwszy, **przeglądanie w poszukiwaniu folderu** zostanie otwarte okno dialogowe w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0f701-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="0f701-189">Zatrzymywanie, uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f701-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="0f701-190">Aby selektywnie włączyć kontrolki</span><span class="sxs-lookup"><span data-stu-id="0f701-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="0f701-191">Dodaj następujący kod `SetEnabled` metody.</span><span class="sxs-lookup"><span data-stu-id="0f701-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="0f701-192">`SetEnabled` Metoda włącza lub wyłącza kontrolek, w zależności od tego, czy element jest zaznaczony na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="0f701-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="0f701-193">Tworzenie `SelectedIndexChanged` program obsługi zdarzeń dla `filesListBox` przez dwukrotne kliknięcie `ListBox` formant w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0f701-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="0f701-194">Dodaj wywołanie do `SetEnabled` w nowym `filesListBox_SelectedIndexChanged` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f701-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="0f701-195">Dodaj wywołanie do `SetEnabled` na końcu `browseButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f701-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="0f701-196">Dodaj wywołanie do `SetEnabled` na końcu `Form1_Load` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f701-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="0f701-197">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="0f701-197">Run the application.</span></span> <span data-ttu-id="0f701-198">**Zapisz wyniki** pole wyboru i **Sprawdź** przycisk są wyłączone, jeśli element nie jest wybrane w `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="0f701-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="0f701-199">Pełny przykład za pomocą My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="0f701-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="0f701-200">Oto kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="0f701-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="0f701-201">Pełny przykład za pomocą System.IO</span><span class="sxs-lookup"><span data-stu-id="0f701-201">Full example using System.IO</span></span>  
 <span data-ttu-id="0f701-202">W poniższym przykładzie równoważne użyto klas z <xref:System.IO> przestrzeni nazw, zamiast `My.Computer.FileSystem` obiektów.</span><span class="sxs-lookup"><span data-stu-id="0f701-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="0f701-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f701-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="0f701-204">Przewodnik: Manipulowanie plikami za pomocą metod .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f701-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
