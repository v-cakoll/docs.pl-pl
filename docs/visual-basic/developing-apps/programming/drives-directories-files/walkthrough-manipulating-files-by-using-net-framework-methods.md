---
title: Manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed363efeeef008927f2c34b393de66ca4ccbb0bb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="60aae-102">Wskazówki: manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60aae-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>
<span data-ttu-id="60aae-103">W tym przewodniku pokazano, jak otwieranie i Odczyt pliku przy użyciu <xref:System.IO.StreamReader> klasy, sprawdź, czy plik jest dostępny, wyszukaj ciąg w pliku do odczytu z wystąpieniem <xref:System.IO.StreamReader> klasy, a następnie zapisać do pliku przy użyciu <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="60aae-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a><span data-ttu-id="60aae-104">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="60aae-104">Creating the Application</span></span>  
 <span data-ttu-id="60aae-105">Uruchom program Visual Studio i rozpocząć projektu przez tworzenie formularza, którego użytkownik może zapisać do wskazanego pliku.</span><span class="sxs-lookup"><span data-stu-id="60aae-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="60aae-106">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="60aae-106">To create the project</span></span>  
  
1.  <span data-ttu-id="60aae-107">Na **pliku** menu, wybierz opcję **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="60aae-107">On the **File** menu, select **New Project**.</span></span>  
  
2.  <span data-ttu-id="60aae-108">W **nowy projekt** okienku, kliknij przycisk **aplikacji systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="60aae-108">In the **New Project** pane, click **Windows Application**.</span></span>  
  
3.  <span data-ttu-id="60aae-109">W **nazwa** wpisz `MyDiary` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="60aae-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>  
  
     <span data-ttu-id="60aae-110">Visual Studio dodaje projekt do **Eksploratora rozwiązań**i **Projektant formularzy systemu Windows** otwiera.</span><span class="sxs-lookup"><span data-stu-id="60aae-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>  
  
4.  <span data-ttu-id="60aae-111">Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="60aae-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="60aae-112">**Obiekt**</span><span class="sxs-lookup"><span data-stu-id="60aae-112">**Object**</span></span>|<span data-ttu-id="60aae-113">**Właściwości**</span><span class="sxs-lookup"><span data-stu-id="60aae-113">**Properties**</span></span>|<span data-ttu-id="60aae-114">**Wartość**</span><span class="sxs-lookup"><span data-stu-id="60aae-114">**Value**</span></span>|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="60aae-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-115">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-116">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="60aae-117">**Prześlij wpis**</span><span class="sxs-lookup"><span data-stu-id="60aae-117">**Submit Entry**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="60aae-118">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-118">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-119">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="60aae-120">**Usuń wpis**</span><span class="sxs-lookup"><span data-stu-id="60aae-120">**Clear Entry**</span></span>|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="60aae-121">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-121">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-122">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-122">**Text**</span></span><br /><br /> <span data-ttu-id="60aae-123">**Wiele linii**</span><span class="sxs-lookup"><span data-stu-id="60aae-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="60aae-124">**Wprowadź inną.**</span><span class="sxs-lookup"><span data-stu-id="60aae-124">**Please enter something.**</span></span><br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a><span data-ttu-id="60aae-125">Zapisywanie do pliku</span><span class="sxs-lookup"><span data-stu-id="60aae-125">Writing to the File</span></span>  
 <span data-ttu-id="60aae-126">Aby dodać możliwość zapisywania do pliku za pośrednictwem aplikacji, użyj <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="60aae-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="60aae-127"><xref:System.IO.StreamWriter> jest przeznaczony dla danych wyjściowych znak, przy użyciu określonego kodowania, natomiast <xref:System.IO.Stream> klasy jest przeznaczona dla bajtu danych wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="60aae-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="60aae-128">Użyj <xref:System.IO.StreamWriter> dla liniami informacji do pliku tekstowego standardowa.</span><span class="sxs-lookup"><span data-stu-id="60aae-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="60aae-129">Aby uzyskać więcej informacji na temat <xref:System.IO.StreamWriter> , zobacz <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="60aae-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>  
  
#### <a name="to-add-writing-functionality"></a><span data-ttu-id="60aae-130">Aby dodać funkcję zapisywania</span><span class="sxs-lookup"><span data-stu-id="60aae-130">To add writing functionality</span></span>  
  
1.  <span data-ttu-id="60aae-131">Z **widoku** menu, wybierz **kod** można otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="60aae-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="60aae-132">Ponieważ aplikacja odwołuje się <xref:System.IO> przestrzeni nazw, Dodaj następujące instrukcje na samym początku kodu, przed deklaracją klasy formularza, który rozpoczyna się `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="60aae-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     <span data-ttu-id="60aae-133">Przed zapisaniem do pliku, należy utworzyć wystąpienie <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="60aae-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>  
  
3.  <span data-ttu-id="60aae-134">Z **widoku** menu, wybierz **projektanta** aby powrócić do **Projektant formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="60aae-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="60aae-135">Kliknij dwukrotnie `Submit` przycisk, aby utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla przycisku, a następnie dodaj poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="60aae-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="60aae-136">Visual Studio programowanie środowiska IDE (Integrated) będzie powrócić do edytora kodu i umieść punkt wstawiania w ramach programu obsługi zdarzeń, w którym należy dodać kodu.</span><span class="sxs-lookup"><span data-stu-id="60aae-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>  
  
1.  <span data-ttu-id="60aae-137">Aby zapisać do pliku, należy użyć <xref:System.IO.StreamWriter.Write%2A> metody <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="60aae-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="60aae-138">Dodaj poniższy kod bezpośrednio po `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="60aae-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="60aae-139">Nie trzeba się martwić się, że zostanie wygenerowany wyjątek, jeśli plik nie zostanie znaleziony, ponieważ zostanie utworzony, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="60aae-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  <span data-ttu-id="60aae-140">Upewnij się, że użytkownik nie może przesłać pusty wpis, dodając następujący kod bezpośrednio po `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="60aae-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  <span data-ttu-id="60aae-141">Ponieważ jest to niedawno dzienniki, użytkownik będzie można przypisać do każdego wpisu datę.</span><span class="sxs-lookup"><span data-stu-id="60aae-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="60aae-142">Wstaw następujący kod po `fw = New StreamWriter("C:\MyDiary.txt", True)` można ustawić zmiennej `Today` do bieżącej daty.</span><span class="sxs-lookup"><span data-stu-id="60aae-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  <span data-ttu-id="60aae-143">Na koniec należy dołączyć kod, aby wyczyścić <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60aae-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="60aae-144">Dodaj następujący kod do `Clear` przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="60aae-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="60aae-145">Dodawanie funkcji wyświetlania do pamiętnik</span><span class="sxs-lookup"><span data-stu-id="60aae-145">Adding Display Features to the Diary</span></span>  
 <span data-ttu-id="60aae-146">W tej sekcji możesz dodać funkcja, która wyświetla najnowsze wpisy w `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60aae-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="60aae-147">Można również dodać <xref:System.Windows.Forms.ComboBox> wyświetlającym poszczególnych wpisów i z którego użytkownik może wybrać wpis do wyświetlenia w `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60aae-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="60aae-148">Wystąpienie <xref:System.IO.StreamReader> klasy odczyty `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="60aae-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="60aae-149">Podobnie jak <xref:System.IO.StreamWriter> klasy <xref:System.IO.StreamReader> jest przeznaczony do użytku z plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="60aae-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>  
  
 <span data-ttu-id="60aae-150">W tej sekcji tego przewodnika Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="60aae-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="60aae-151">Formant</span><span class="sxs-lookup"><span data-stu-id="60aae-151">Control</span></span>|<span data-ttu-id="60aae-152">Właściwości</span><span class="sxs-lookup"><span data-stu-id="60aae-152">Properties</span></span>|<span data-ttu-id="60aae-153">Wartości</span><span class="sxs-lookup"><span data-stu-id="60aae-153">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="60aae-154">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-154">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-155">**Widoczne**</span><span class="sxs-lookup"><span data-stu-id="60aae-155">**Visible**</span></span><br /><br /> <span data-ttu-id="60aae-156">**Rozmiar**</span><span class="sxs-lookup"><span data-stu-id="60aae-156">**Size**</span></span><br /><br /> <span data-ttu-id="60aae-157">**Wiele linii**</span><span class="sxs-lookup"><span data-stu-id="60aae-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="60aae-158">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-158">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-159">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="60aae-160">**Wyświetl**</span><span class="sxs-lookup"><span data-stu-id="60aae-160">**Display**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="60aae-161">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-161">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-162">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="60aae-163">**Pobierz zapisy**</span><span class="sxs-lookup"><span data-stu-id="60aae-163">**Get Entries**</span></span>|  
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="60aae-164">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-164">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-165">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-165">**Text**</span></span><br /><br /> <span data-ttu-id="60aae-166">**włączone**</span><span class="sxs-lookup"><span data-stu-id="60aae-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="60aae-167">**Wybierz pozycję**</span><span class="sxs-lookup"><span data-stu-id="60aae-167">**Select an Entry**</span></span><br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a><span data-ttu-id="60aae-168">Aby wypełnić pola kombi</span><span class="sxs-lookup"><span data-stu-id="60aae-168">To populate the combo box</span></span>  
  
1.  <span data-ttu-id="60aae-169">`PickEntries` <xref:System.Windows.Forms.ComboBox> Służy do wyświetlania dat, na których użytkownik prześle każdego wpisu, więc użytkownik może wybrać wpis od określonej daty.</span><span class="sxs-lookup"><span data-stu-id="60aae-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="60aae-170">Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń do `GetEntries` przycisk i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="60aae-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  <span data-ttu-id="60aae-171">Do testowania kodu, naciśnij klawisz F5, aby skompilować aplikację, a następnie kliknij przycisk **Pobierz zapisy**.</span><span class="sxs-lookup"><span data-stu-id="60aae-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="60aae-172">Kliknij strzałkę listy rozwijanej w <xref:System.Windows.Forms.ComboBox> na potrzeby wyświetlania dat wpisu.</span><span class="sxs-lookup"><span data-stu-id="60aae-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>  
  
#### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="60aae-173">Aby wybrać i wyświetlić poszczególne pozycje</span><span class="sxs-lookup"><span data-stu-id="60aae-173">To choose and display individual entries</span></span>  
  
1.  <span data-ttu-id="60aae-174">Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `Display` przycisk i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="60aae-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  <span data-ttu-id="60aae-175">Do testowania kodu, naciśnij klawisz F5, aby skompilować aplikację, a następnie Prześlij wpis.</span><span class="sxs-lookup"><span data-stu-id="60aae-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="60aae-176">Kliknij przycisk **Pobierz zapisy**, wybierz pozycję z <xref:System.Windows.Forms.ComboBox>, a następnie kliknij przycisk **wyświetlania**.</span><span class="sxs-lookup"><span data-stu-id="60aae-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="60aae-177">Zawartość wybranego wpisu jest wyświetlana w `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60aae-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="60aae-178">Umożliwienie użytkownikom do usunięcia lub zmodyfikowania wpisów</span><span class="sxs-lookup"><span data-stu-id="60aae-178">Enabling Users to Delete or Modify Entries</span></span>  
 <span data-ttu-id="60aae-179">Ponadto może zawierać dodatkowe funkcje umożliwia użytkownikom usunąć ani zmodyfikować wpis za pomocą `DeleteEntry` i `EditEntry` przycisków.</span><span class="sxs-lookup"><span data-stu-id="60aae-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="60aae-180">Przyciski pozostaną wyłączone, chyba że wpis jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="60aae-180">Both buttons remain disabled unless an entry is displayed.</span></span>  
  
 <span data-ttu-id="60aae-181">Dodaj formanty w poniższej tabeli do formularza i ustaw wartości odpowiednich dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="60aae-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="60aae-182">Formant</span><span class="sxs-lookup"><span data-stu-id="60aae-182">Control</span></span>|<span data-ttu-id="60aae-183">Właściwości</span><span class="sxs-lookup"><span data-stu-id="60aae-183">Properties</span></span>|<span data-ttu-id="60aae-184">Wartości</span><span class="sxs-lookup"><span data-stu-id="60aae-184">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="60aae-185">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-185">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-186">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-186">**Text**</span></span><br /><br /> <span data-ttu-id="60aae-187">**włączone**</span><span class="sxs-lookup"><span data-stu-id="60aae-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="60aae-188">**Usuń wpis**</span><span class="sxs-lookup"><span data-stu-id="60aae-188">**Delete Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="60aae-189">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-189">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-190">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-190">**Text**</span></span><br /><br /> <span data-ttu-id="60aae-191">**włączone**</span><span class="sxs-lookup"><span data-stu-id="60aae-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="60aae-192">**Edytuj wpis**</span><span class="sxs-lookup"><span data-stu-id="60aae-192">**Edit Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="60aae-193">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="60aae-193">**Name**</span></span><br /><br /> <span data-ttu-id="60aae-194">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="60aae-194">**Text**</span></span><br /><br /> <span data-ttu-id="60aae-195">**włączone**</span><span class="sxs-lookup"><span data-stu-id="60aae-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="60aae-196">**Zatwierdź Edytuj**</span><span class="sxs-lookup"><span data-stu-id="60aae-196">**Submit Edit**</span></span><br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="60aae-197">Aby włączyć, usuwanie i modyfikowanie wpisów</span><span class="sxs-lookup"><span data-stu-id="60aae-197">To enable deletion and modification of entries</span></span>  
  
1.  <span data-ttu-id="60aae-198">Dodaj następujący kod do `Display` przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń, po `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="60aae-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  <span data-ttu-id="60aae-199">Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `DeleteEntry` przycisk i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="60aae-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  <span data-ttu-id="60aae-200">Gdy użytkownik wyświetla wpis `EditEntry` przycisk staje się dostępny.</span><span class="sxs-lookup"><span data-stu-id="60aae-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="60aae-201">Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> zdarzenie `Display` przycisku po `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="60aae-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  <span data-ttu-id="60aae-202">Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `EditEntry` przycisk i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="60aae-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  <span data-ttu-id="60aae-203">Utwórz <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `SubmitEdit` przycisk i Dodaj następujący kod</span><span class="sxs-lookup"><span data-stu-id="60aae-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 <span data-ttu-id="60aae-204">Do testowania kodu, naciśnij klawisz F5, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="60aae-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="60aae-205">Kliknij przycisk **Pobierz zapisy**, wybierz wpis, a następnie kliknij przycisk **wyświetlania**.</span><span class="sxs-lookup"><span data-stu-id="60aae-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="60aae-206">Wpis zostanie wyświetlony `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60aae-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="60aae-207">Kliknij przycisk **Edytuj wpis**.</span><span class="sxs-lookup"><span data-stu-id="60aae-207">Click **Edit Entry**.</span></span> <span data-ttu-id="60aae-208">Wpis zostanie wyświetlony `Entry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60aae-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="60aae-209">Edytuj wpis w `Entry` <xref:System.Windows.Forms.TextBox> i kliknij przycisk **przesłać Edytuj**.</span><span class="sxs-lookup"><span data-stu-id="60aae-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="60aae-210">Otwórz `MyDiary.txt` plik, aby potwierdzić poprawki.</span><span class="sxs-lookup"><span data-stu-id="60aae-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="60aae-211">Teraz wybierz wpis i kliknij przycisk **Usuń wpis**.</span><span class="sxs-lookup"><span data-stu-id="60aae-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="60aae-212">Gdy <xref:System.Windows.Forms.MessageBox> zażąda potwierdzenia, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="60aae-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="60aae-213">Zamknij aplikację i otworzyć `MyDiary.txt` aby potwierdzić usunięcie.</span><span class="sxs-lookup"><span data-stu-id="60aae-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60aae-214">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60aae-214">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="60aae-215">Przewodniki</span><span class="sxs-lookup"><span data-stu-id="60aae-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
