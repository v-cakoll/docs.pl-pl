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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333807"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="b6b5f-102">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6b5f-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="b6b5f-103">Ten Instruktaż zawiera wprowadzenie do podstawowych podstaw we/wy plików w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="b6b5f-104">Opisano w nim sposób tworzenia małej aplikacji, która wyświetla i bada pliki tekstowe w katalogu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="b6b5f-105">Dla każdego zaznaczonego pliku tekstowego aplikacja zawiera atrybuty pliku i pierwszy wiersz zawartości.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="b6b5f-106">Istnieje możliwość zapisu informacji w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="b6b5f-107">W tym instruktażu są stosowane składniki `My.Computer.FileSystem Object`, które są dostępne w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="b6b5f-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="b6b5f-109">Na końcu przewodnika jest dostarczany równoważny przykład, który używa klas z przestrzeni nazw <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="b6b5f-110">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="b6b5f-110">To create the project</span></span>  
  
1. <span data-ttu-id="b6b5f-111">W menu **plik** kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="b6b5f-112">Pojawi się okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="b6b5f-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="b6b5f-113">W okienku **zainstalowane szablony** rozwiń węzeł **Visual Basic**, a następnie kliknij pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="b6b5f-114">W okienku **Szablony** w środkowym kliknij pozycję **Windows Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="b6b5f-115">W polu **Nazwa** wpisz `FileExplorer`, aby ustawić nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b6b5f-116">Program Visual Studio dodaje projekt do **Eksplorator rozwiązań**, a Projektant formularzy systemu Windows zostanie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="b6b5f-117">Dodaj kontrolki w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="b6b5f-118">Kontrolka</span><span class="sxs-lookup"><span data-stu-id="b6b5f-118">Control</span></span>|<span data-ttu-id="b6b5f-119">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b6b5f-119">Property</span></span>|<span data-ttu-id="b6b5f-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="b6b5f-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="b6b5f-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-121">**ListBox**</span></span>|<span data-ttu-id="b6b5f-122">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="b6b5f-123">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-123">**Button**</span></span>|<span data-ttu-id="b6b5f-124">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-124">**Name**</span></span><br /><br /> <span data-ttu-id="b6b5f-125">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="b6b5f-126">**Przycisku**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-126">**Browse**</span></span>|  
    |<span data-ttu-id="b6b5f-127">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-127">**Button**</span></span>|<span data-ttu-id="b6b5f-128">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-128">**Name**</span></span><br /><br /> <span data-ttu-id="b6b5f-129">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="b6b5f-130">**Sprawdzić**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-130">**Examine**</span></span>|  
    |<span data-ttu-id="b6b5f-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-131">**CheckBox**</span></span>|<span data-ttu-id="b6b5f-132">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-132">**Name**</span></span><br /><br /> <span data-ttu-id="b6b5f-133">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="b6b5f-134">**Zapisz wyniki**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-134">**Save Results**</span></span>|  
    |<span data-ttu-id="b6b5f-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="b6b5f-136">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b6b5f-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="b6b5f-137">Aby wybrać folder i wyświetlić listę plików w folderze</span><span class="sxs-lookup"><span data-stu-id="b6b5f-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="b6b5f-138">Utwórz procedurę obsługi zdarzeń `Click` dla `browseButton` przez dwukrotne kliknięcie kontrolki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="b6b5f-139">Zostanie otwarty Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="b6b5f-140">Dodaj następujący kod do programu obsługi zdarzeń `Click`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="b6b5f-141">Wywołanie `FolderBrowserDialog1.ShowDialog` otwiera okno dialogowe **przeglądanie w poszukiwaniu folderu** .</span><span class="sxs-lookup"><span data-stu-id="b6b5f-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="b6b5f-142">Po kliknięciu przycisku **OK**Właściwość <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> jest wysyłana jako argument do metody `ListFiles`, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="b6b5f-143">Dodaj następującą metodę `ListFiles`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="b6b5f-144">Ten kod najpierw czyści element **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="b6b5f-145">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> następnie pobiera kolekcję ciągów, po jednej dla każdego pliku w katalogu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="b6b5f-146">Metoda `GetFiles` akceptuje argument wzorca wyszukiwania w celu pobrania plików zgodnych z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="b6b5f-147">W tym przykładzie zwracane są tylko pliki z rozszerzeniem txt.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="b6b5f-148">Ciągi zwracane przez metodę `GetFiles` są następnie dodawane do elementu **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="b6b5f-149">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-149">Run the application.</span></span> <span data-ttu-id="b6b5f-150">Kliknij przycisk **Przeglądaj** .</span><span class="sxs-lookup"><span data-stu-id="b6b5f-150">Click the **Browse** button.</span></span> <span data-ttu-id="b6b5f-151">W oknie dialogowym **Przeglądaj w poszukiwaniu folderu** przejdź do folderu, który zawiera pliki. txt, a następnie wybierz folder, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="b6b5f-152">`ListBox` zawiera listę plików txt w wybranym folderze.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="b6b5f-153">Zatrzymaj uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="b6b5f-154">Aby uzyskać atrybuty pliku oraz zawartość z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="b6b5f-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="b6b5f-155">Utwórz procedurę obsługi zdarzeń `Click` dla `examineButton` przez dwukrotne kliknięcie kontrolki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="b6b5f-156">Dodaj następujący kod do programu obsługi zdarzeń `Click`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="b6b5f-157">Kod sprawdza, czy element jest zaznaczony w `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="b6b5f-158">Następnie uzyskuje wpis ścieżki pliku z `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="b6b5f-159">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> służy do sprawdzania, czy plik nadal istnieje.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="b6b5f-160">Ścieżka pliku jest wysyłana jako argument do metody `GetTextForOutput`, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="b6b5f-161">Ta metoda zwraca ciąg, który zawiera informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="b6b5f-162">Informacje o pliku są wyświetlane w elemencie **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="b6b5f-163">Dodaj następującą metodę `GetTextForOutput`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="b6b5f-164">Kod używa metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>, aby uzyskać parametry pliku.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="b6b5f-165">Parametry pliku są dodawane do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="b6b5f-166">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> odczytuje zawartość pliku do <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="b6b5f-167">Pierwszy wiersz zawartości jest uzyskiwany z `StreamReader` i jest dodawany do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="b6b5f-168">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-168">Run the application.</span></span> <span data-ttu-id="b6b5f-169">Kliknij przycisk **Przeglądaj**, a następnie przejdź do folderu, który zawiera pliki. txt.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="b6b5f-170">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="b6b5f-171">Wybierz plik w `ListBox`, a następnie kliknij pozycję **Badaj**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="b6b5f-172">`MessageBox` wyświetla informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="b6b5f-173">Zatrzymaj uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="b6b5f-174">Aby dodać wpis dziennika</span><span class="sxs-lookup"><span data-stu-id="b6b5f-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="b6b5f-175">Dodaj następujący kod na końcu programu obsługi zdarzeń `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="b6b5f-176">Kod ustawia ścieżkę pliku dziennika, aby umieścić plik dziennika w tym samym katalogu co wybrany plik.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="b6b5f-177">Tekst wpisu dziennika jest ustawiany na bieżącą datę i godzinę oraz informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="b6b5f-178">Do utworzenia wpisu dziennika zostanie użyta metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> z argumentem `append` ustawionym na `True`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="b6b5f-179">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-179">Run the application.</span></span> <span data-ttu-id="b6b5f-180">Przejdź do pliku tekstowego, zaznacz go w `ListBox`, zaznacz pole wyboru **Zapisz wyniki** , a następnie kliknij przycisk **Sprawdź**.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="b6b5f-181">Sprawdź, czy wpis dziennika jest zapisany w pliku `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="b6b5f-182">Zatrzymaj uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="b6b5f-183">Aby użyć bieżącego katalogu</span><span class="sxs-lookup"><span data-stu-id="b6b5f-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="b6b5f-184">Utwórz procedurę obsługi zdarzeń dla `Form1_Load` przez dwukrotne kliknięcie formularza.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="b6b5f-185">Dodaj następujący kod do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="b6b5f-186">Ten kod ustawia domyślny katalog przeglądarki folderu w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="b6b5f-187">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-187">Run the application.</span></span> <span data-ttu-id="b6b5f-188">Po kliknięciu przycisku **Przeglądaj** zostanie otwarte okno dialogowe **przeglądanie w poszukiwaniu folderu** w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="b6b5f-189">Zatrzymaj uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="b6b5f-190">Aby wybiórczo włączyć kontrolki</span><span class="sxs-lookup"><span data-stu-id="b6b5f-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="b6b5f-191">Dodaj następującą metodę `SetEnabled`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="b6b5f-192">Metoda `SetEnabled` włącza lub wyłącza kontrolki w zależności od tego, czy element jest zaznaczony w `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="b6b5f-193">Utwórz procedurę obsługi zdarzeń `SelectedIndexChanged` dla `filesListBox` przez dwukrotne kliknięcie kontrolki `ListBox` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="b6b5f-194">Dodaj wywołanie do `SetEnabled` w nowej procedurze obsługi zdarzeń `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="b6b5f-195">Dodaj wywołanie do `SetEnabled` na końcu programu obsługi zdarzeń `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="b6b5f-196">Dodaj wywołanie do `SetEnabled` na końcu programu obsługi zdarzeń `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="b6b5f-197">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-197">Run the application.</span></span> <span data-ttu-id="b6b5f-198">Pole wyboru **Zapisz wyniki** i przycisk **Sprawdź** są wyłączone, jeśli element nie jest zaznaczony w `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="b6b5f-199">Pełny przykład przy użyciu my. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="b6b5f-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="b6b5f-200">Poniżej znajduje się kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="b6b5f-201">Pełny przykład przy użyciu System.IO</span><span class="sxs-lookup"><span data-stu-id="b6b5f-201">Full example using System.IO</span></span>  

 <span data-ttu-id="b6b5f-202">Poniższy odpowiednik przykładu używa klas z przestrzeni nazw <xref:System.IO>, zamiast używać obiektów `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="b6b5f-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="b6b5f-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6b5f-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="b6b5f-204">Przewodnik: manipulowanie plikami za pomocą metod .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b6b5f-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
