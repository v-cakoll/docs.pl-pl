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
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="2048f-102">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2048f-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="2048f-103">Ten przewodnik zawiera wprowadzenie do podstaw we/wy pliku w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2048f-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="2048f-104">Opisano w nim sposób tworzenia małej aplikacji, która wyświetla listę i sprawdza pliki tekstowe w katalogu.</span><span class="sxs-lookup"><span data-stu-id="2048f-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="2048f-105">Dla każdego zaznaczonego pliku tekstowego aplikacja udostępnia atrybuty pliku i pierwszy wiersz zawartości.</span><span class="sxs-lookup"><span data-stu-id="2048f-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="2048f-106">Istnieje możliwość zapisania informacji do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="2048f-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="2048f-107">W tym instruktażu `My.Computer.FileSystem Object`użyto członków programu , które są dostępne w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2048f-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="2048f-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="2048f-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="2048f-109">Na końcu instruktażu podano równoważny przykład, który używa <xref:System.IO> klas z obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="2048f-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="2048f-110">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="2048f-110">To create the project</span></span>  
  
1. <span data-ttu-id="2048f-111">W menu **Plik** kliknij polecenie **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="2048f-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="2048f-112">Zostanie wyświetlone okno dialogowe **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="2048f-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="2048f-113">W okienku **Zainstalowane szablony** rozwiń węzeł **Visual Basic**, a następnie kliknij pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="2048f-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="2048f-114">W okienku **Szablony** w środku kliknij pozycję **Aplikacja formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2048f-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="2048f-115">W polu **Nazwa** `FileExplorer` wpisz, aby ustawić nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2048f-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="2048f-116">Program Visual Studio dodaje projekt do **Eksploratora rozwiązań**i zostanie otwarty projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2048f-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="2048f-117">Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="2048f-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="2048f-118">Kontrola</span><span class="sxs-lookup"><span data-stu-id="2048f-118">Control</span></span>|<span data-ttu-id="2048f-119">Właściwość</span><span class="sxs-lookup"><span data-stu-id="2048f-119">Property</span></span>|<span data-ttu-id="2048f-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="2048f-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="2048f-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="2048f-121">**ListBox**</span></span>|<span data-ttu-id="2048f-122">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="2048f-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="2048f-123">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="2048f-123">**Button**</span></span>|<span data-ttu-id="2048f-124">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="2048f-124">**Name**</span></span><br /><br /> <span data-ttu-id="2048f-125">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="2048f-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="2048f-126">**Przeglądaj**</span><span class="sxs-lookup"><span data-stu-id="2048f-126">**Browse**</span></span>|  
    |<span data-ttu-id="2048f-127">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="2048f-127">**Button**</span></span>|<span data-ttu-id="2048f-128">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="2048f-128">**Name**</span></span><br /><br /> <span data-ttu-id="2048f-129">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="2048f-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="2048f-130">**Zbadać**</span><span class="sxs-lookup"><span data-stu-id="2048f-130">**Examine**</span></span>|  
    |<span data-ttu-id="2048f-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="2048f-131">**CheckBox**</span></span>|<span data-ttu-id="2048f-132">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="2048f-132">**Name**</span></span><br /><br /> <span data-ttu-id="2048f-133">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="2048f-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="2048f-134">**Zapisz wyniki**</span><span class="sxs-lookup"><span data-stu-id="2048f-134">**Save Results**</span></span>|  
    |<span data-ttu-id="2048f-135">**Folderbrowserdialog**</span><span class="sxs-lookup"><span data-stu-id="2048f-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="2048f-136">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="2048f-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="2048f-137">Aby zaznaczyć folder i wyświetlić listę plików w folderze</span><span class="sxs-lookup"><span data-stu-id="2048f-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="2048f-138">Utwórz `Click` program `browseButton` obsługi zdarzeń, klikając dwukrotnie formant w formularzu.</span><span class="sxs-lookup"><span data-stu-id="2048f-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="2048f-139">Zostanie otwarty Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="2048f-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="2048f-140">Dodaj następujący kod `Click` do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2048f-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="2048f-141">Połączenie `FolderBrowserDialog1.ShowDialog` zostanie otwarte w oknie dialogowym **Przeglądanie folderu.**</span><span class="sxs-lookup"><span data-stu-id="2048f-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="2048f-142">Po kliknięciu **OK**przycisku <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> OK użytkownik jest wysyłany `ListFiles` jako argument do metody, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="2048f-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="2048f-143">Dodaj następującą `ListFiles` metodę.</span><span class="sxs-lookup"><span data-stu-id="2048f-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="2048f-144">Ten kod najpierw czyści **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="2048f-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="2048f-145">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> następnie pobiera kolekcję ciągów, po jednym dla każdego pliku w katalogu.</span><span class="sxs-lookup"><span data-stu-id="2048f-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="2048f-146">Metoda `GetFiles` akceptuje argument wzorca wyszukiwania, aby pobrać pliki, które pasują do określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="2048f-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="2048f-147">W tym przykładzie zwracane są tylko pliki, które mają rozszerzenie .txt.</span><span class="sxs-lookup"><span data-stu-id="2048f-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="2048f-148">Ciągi, które są `GetFiles` zwracane przez metodę są następnie dodawane do **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="2048f-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="2048f-149">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-149">Run the application.</span></span> <span data-ttu-id="2048f-150">Kliknij przycisk **Przeglądaj.**</span><span class="sxs-lookup"><span data-stu-id="2048f-150">Click the **Browse** button.</span></span> <span data-ttu-id="2048f-151">W oknie dialogowym **Przeglądanie folderu** przejdź do folderu zawierającego pliki txt, a następnie wybierz folder i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2048f-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="2048f-152">Zawiera `ListBox` listę plików txt w wybranym folderze.</span><span class="sxs-lookup"><span data-stu-id="2048f-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="2048f-153">Przestań działać aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="2048f-154">Aby uzyskać atrybuty pliku i zawartości z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="2048f-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="2048f-155">Utwórz `Click` program `examineButton` obsługi zdarzeń, klikając dwukrotnie formant w formularzu.</span><span class="sxs-lookup"><span data-stu-id="2048f-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="2048f-156">Dodaj następujący kod `Click` do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2048f-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="2048f-157">Kod sprawdza, czy element jest `ListBox`zaznaczony w pliku .</span><span class="sxs-lookup"><span data-stu-id="2048f-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="2048f-158">Następnie uzyskuje wpis ścieżki pliku `ListBox`z pliku .</span><span class="sxs-lookup"><span data-stu-id="2048f-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="2048f-159">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> jest używana do sprawdzania, czy plik nadal istnieje.</span><span class="sxs-lookup"><span data-stu-id="2048f-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="2048f-160">Ścieżka pliku jest wysyłana jako `GetTextForOutput` argument do metody, która jest dodawana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="2048f-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="2048f-161">Ta metoda zwraca ciąg, który zawiera informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="2048f-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="2048f-162">Informacje o pliku są wyświetlane w **polu messagebox**.</span><span class="sxs-lookup"><span data-stu-id="2048f-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="2048f-163">Dodaj następującą `GetTextForOutput` metodę.</span><span class="sxs-lookup"><span data-stu-id="2048f-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="2048f-164">Kod używa metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> do uzyskania parametrów pliku.</span><span class="sxs-lookup"><span data-stu-id="2048f-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="2048f-165">Parametry pliku są dodawane do pliku <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="2048f-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="2048f-166">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> odczytuje zawartość pliku <xref:System.IO.StreamReader>do pliku .</span><span class="sxs-lookup"><span data-stu-id="2048f-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="2048f-167">Pierwszy wiersz zawartości jest otrzymywany `StreamReader` z i `StringBuilder`jest dodawany do pliku .</span><span class="sxs-lookup"><span data-stu-id="2048f-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="2048f-168">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-168">Run the application.</span></span> <span data-ttu-id="2048f-169">Kliknij **pozycję Przeglądaj**i przejdź do folderu zawierającego pliki txt.</span><span class="sxs-lookup"><span data-stu-id="2048f-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="2048f-170">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2048f-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="2048f-171">Zaznacz plik w `ListBox`pliku , a następnie kliknij przycisk **Sprawdź**.</span><span class="sxs-lookup"><span data-stu-id="2048f-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="2048f-172">A `MessageBox` pokazuje informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="2048f-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="2048f-173">Przestań działać aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="2048f-174">Aby dodać wpis dziennika</span><span class="sxs-lookup"><span data-stu-id="2048f-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="2048f-175">Dodaj następujący kod na końcu `examineButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2048f-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="2048f-176">Kod ustawia ścieżkę pliku dziennika, aby umieścić plik dziennika w tym samym katalogu, co w wybranym pliku.</span><span class="sxs-lookup"><span data-stu-id="2048f-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="2048f-177">Tekst wpisu dziennika jest ustawiony na bieżącą datę i godzinę, po której następują informacje o pliku.</span><span class="sxs-lookup"><span data-stu-id="2048f-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="2048f-178">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> z argumentem ustawionym na `append` , służy do `True`tworzenia wpisu dziennika.</span><span class="sxs-lookup"><span data-stu-id="2048f-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="2048f-179">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-179">Run the application.</span></span> <span data-ttu-id="2048f-180">Przejdź do pliku tekstowego, zaznacz `ListBox`pole wyboru **Zapisz wyniki,** a następnie kliknij przycisk **Sprawdź**.</span><span class="sxs-lookup"><span data-stu-id="2048f-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="2048f-181">Sprawdź, czy wpis dziennika jest `log.txt` zapisywany w pliku.</span><span class="sxs-lookup"><span data-stu-id="2048f-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="2048f-182">Przestań działać aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="2048f-183">Aby użyć bieżącego katalogu</span><span class="sxs-lookup"><span data-stu-id="2048f-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="2048f-184">Utwórz program `Form1_Load` obsługi zdarzeń, klikając dwukrotnie formularz.</span><span class="sxs-lookup"><span data-stu-id="2048f-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="2048f-185">Dodaj następujący kod do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2048f-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="2048f-186">Ten kod ustawia domyślny katalog przeglądarki folderów na bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="2048f-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="2048f-187">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-187">Run the application.</span></span> <span data-ttu-id="2048f-188">Po **kliknięciu przycisku Przeglądaj** po raz pierwszy zostanie otwarte okno dialogowe **Przeglądanie w poszukiwaniu folderu** w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2048f-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="2048f-189">Przestań działać aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="2048f-190">Aby selektywnie włączyć formanty</span><span class="sxs-lookup"><span data-stu-id="2048f-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="2048f-191">Dodaj następującą `SetEnabled` metodę.</span><span class="sxs-lookup"><span data-stu-id="2048f-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="2048f-192">Metoda `SetEnabled` włącza lub wyłącza formanty w zależności `ListBox`od tego, czy element jest wybrany w programie .</span><span class="sxs-lookup"><span data-stu-id="2048f-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="2048f-193">Utwórz `SelectedIndexChanged` program `filesListBox` obsługi zdarzeń, klikając `ListBox` dwukrotnie formant w formularzu.</span><span class="sxs-lookup"><span data-stu-id="2048f-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="2048f-194">Dodaj wywołanie `SetEnabled` do `filesListBox_SelectedIndexChanged` w nowym programie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2048f-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="2048f-195">Dodaj wywołanie `SetEnabled` na końcu `browseButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2048f-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="2048f-196">Dodaj wywołanie `SetEnabled` na końcu `Form1_Load` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2048f-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="2048f-197">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2048f-197">Run the application.</span></span> <span data-ttu-id="2048f-198">Pole **wyboru Zapisz wyniki** i przycisk **Sprawdź** są wyłączone, `ListBox`jeśli element nie jest zaznaczony w polu .</span><span class="sxs-lookup"><span data-stu-id="2048f-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="2048f-199">Pełny przykład przy użyciu systemu My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="2048f-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="2048f-200">Oto pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="2048f-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="2048f-201">Pełny przykład przy użyciu System.IO</span><span class="sxs-lookup"><span data-stu-id="2048f-201">Full example using System.IO</span></span>  

 <span data-ttu-id="2048f-202">Poniższy równoważny przykład używa <xref:System.IO> klas z obszaru `My.Computer.FileSystem` nazw zamiast obiektów.</span><span class="sxs-lookup"><span data-stu-id="2048f-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="2048f-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2048f-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="2048f-204">Wskazówki: manipulowanie plikami za pomocą metod .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2048f-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
