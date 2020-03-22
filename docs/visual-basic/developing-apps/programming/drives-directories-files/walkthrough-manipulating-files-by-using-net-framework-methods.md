---
title: Manipulowanie plikami za pomocą metod .NET Framework
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
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333787"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="3fd8f-102">Wskazówki: manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fd8f-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="3fd8f-103">W tym przewodniku pokazano, jak otworzyć i <xref:System.IO.StreamReader> odczytać plik przy użyciu klasy, sprawdź, czy plik jest dostępny, wyszukaj ciąg w pliku odczytanego z wystąpieniem <xref:System.IO.StreamReader> klasy i zapisu do pliku przy użyciu <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="3fd8f-104">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3fd8f-104">Creating the Application</span></span>

<span data-ttu-id="3fd8f-105">Uruchom program Visual Studio i rozpocznij projekt, tworząc formularz, którego użytkownik może użyć do zapisania w wyznaczonym pliku.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="3fd8f-106">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="3fd8f-106">To create the project</span></span>

1. <span data-ttu-id="3fd8f-107">W menu **Plik** wybierz polecenie **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="3fd8f-108">W okienku **Nowy projekt** kliknij pozycję Aplikacja **systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="3fd8f-109">W **Name** polu Nazwa `MyDiary` wpisz i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="3fd8f-110">Program Visual Studio dodaje projekt do **Eksploratora rozwiązań**i zostanie otwarty **projektant formularzy systemu Windows.**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="3fd8f-111">Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="3fd8f-112">**Obiektu**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-112">**Object**</span></span>|<span data-ttu-id="3fd8f-113">**Właściwości**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-113">**Properties**</span></span>|<span data-ttu-id="3fd8f-114">**Wartość**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3fd8f-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-115">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-116">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="3fd8f-117">**Prześlij wpis**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3fd8f-118">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-118">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-119">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="3fd8f-120">**Wyczyść wpis**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="3fd8f-121">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-121">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-122">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-122">**Text**</span></span><br /><br /> <span data-ttu-id="3fd8f-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="3fd8f-124">**Proszę coś wpisać.**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="3fd8f-125">Zapisywanie do pliku</span><span class="sxs-lookup"><span data-stu-id="3fd8f-125">Writing to the File</span></span>

<span data-ttu-id="3fd8f-126">Aby dodać możliwość zapisu do pliku za <xref:System.IO.StreamWriter> pośrednictwem aplikacji, należy użyć klasy.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="3fd8f-127"><xref:System.IO.StreamWriter>jest przeznaczony do wyjścia znaków w określonym <xref:System.IO.Stream> kodowaniu, podczas gdy klasa jest przeznaczona dla wejścia i wyjścia bajtów.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="3fd8f-128">Służy <xref:System.IO.StreamWriter> do zapisywania wierszy informacji do standardowego pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="3fd8f-129">Aby uzyskać więcej <xref:System.IO.StreamWriter> informacji <xref:System.IO.StreamWriter>na temat klasy, zobacz .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="3fd8f-130">Aby dodać funkcje pisania</span><span class="sxs-lookup"><span data-stu-id="3fd8f-130">To add writing functionality</span></span>

1. <span data-ttu-id="3fd8f-131">Z menu **Widok** wybierz pozycję **Kod,** aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="3fd8f-132">Ponieważ aplikacja odwołuje <xref:System.IO> się do obszaru nazw, dodaj następujące instrukcje na samym początku kodu, `Public Class Form1`przed deklaracją klasy dla formularza, który rozpoczyna się.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="3fd8f-133">Przed zapisaniem do pliku należy utworzyć <xref:System.IO.StreamWriter> wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="3fd8f-134">Z menu **Widok** wybierz polecenie **Projektant,** aby powrócić do **projektanta formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="3fd8f-135">Kliknij dwukrotnie `Submit` przycisk, aby <xref:System.Windows.Forms.Control.Click> utworzyć program obsługi zdarzeń dla przycisku, a następnie dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="3fd8f-136">Visual Studio zintegrowane środowisko programistyczne (IDE) powróci do Edytora kodu i umieść punkt wstawiania w programie obsługi zdarzeń, gdzie należy dodać kod.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="3fd8f-137">Aby zapisać do pliku, <xref:System.IO.StreamWriter.Write%2A> należy <xref:System.IO.StreamWriter> użyć metody klasy.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="3fd8f-138">Dodaj następujący kod bezpośrednio `Dim fw As StreamWriter`po .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="3fd8f-139">Nie musisz się martwić, że wyjątek zostanie zgłoszony, jeśli plik nie zostanie znaleziony, ponieważ zostanie utworzony, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="3fd8f-140">Upewnij się, że użytkownik nie może przesłać pustego `Dim ReadString As String`wpisu, dodając następujący kod bezpośrednio po .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="3fd8f-141">Ponieważ jest to dziennik, użytkownik będzie chciał przypisać datę do każdego wpisu.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="3fd8f-142">Wstaw następujący `fw = New StreamWriter("C:\MyDiary.txt", True)` kod po, `Today` aby ustawić zmienną na bieżącą datę.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="3fd8f-143">Na koniec dołącz kod, <xref:System.Windows.Forms.TextBox>aby wyczyścić plik .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3fd8f-144">Dodaj następujący kod `Clear` do zdarzenia <xref:System.Windows.Forms.Control.Click> przycisku.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="3fd8f-145">Dodawanie funkcji wyświetlania do dziennika</span><span class="sxs-lookup"><span data-stu-id="3fd8f-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="3fd8f-146">W tej sekcji należy dodać funkcję, która `DisplayEntry` <xref:System.Windows.Forms.TextBox>wyświetla najnowszy wpis w pliku .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3fd8f-147">Można również dodać, <xref:System.Windows.Forms.ComboBox> który wyświetla różne wpisy i z którego użytkownik `DisplayEntry` <xref:System.Windows.Forms.TextBox>może wybrać wpis do wyświetlenia w pliku .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3fd8f-148">Wystąpienie <xref:System.IO.StreamReader> klasy odczytuje `MyDiary.txt`z .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="3fd8f-149">Podobnie <xref:System.IO.StreamWriter> jak <xref:System.IO.StreamReader> klasa, jest przeznaczony do użytku z plikami tekstowymi.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="3fd8f-150">W tej sekcji instruktażu dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="3fd8f-151">Kontrola</span><span class="sxs-lookup"><span data-stu-id="3fd8f-151">Control</span></span>|<span data-ttu-id="3fd8f-152">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3fd8f-152">Properties</span></span>|<span data-ttu-id="3fd8f-153">Wartości</span><span class="sxs-lookup"><span data-stu-id="3fd8f-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="3fd8f-154">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-154">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-155">**Widoczne**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-155">**Visible**</span></span><br /><br /> <span data-ttu-id="3fd8f-156">**Rozmiar**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-156">**Size**</span></span><br /><br /> <span data-ttu-id="3fd8f-157">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3fd8f-158">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-158">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-159">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="3fd8f-160">**Wyświetlanie**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3fd8f-161">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-161">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-162">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="3fd8f-163">**Pobierz wpisy**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="3fd8f-164">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-164">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-165">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-165">**Text**</span></span><br /><br /> <span data-ttu-id="3fd8f-166">**Enabled (Włączony)**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="3fd8f-167">**Wybieranie wpisu**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="3fd8f-168">Aby wypełnić pole kombi</span><span class="sxs-lookup"><span data-stu-id="3fd8f-168">To populate the combo box</span></span>

1. <span data-ttu-id="3fd8f-169">Jest `PickEntries` <xref:System.Windows.Forms.ComboBox> używany do wyświetlania dat, w których użytkownik przesyła każdy wpis, dzięki czemu użytkownik może wybrać wpis z określonej daty.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="3fd8f-170">Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `GetEntries` zdarzeń do przycisku i dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="3fd8f-171">Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie kliknij przycisk **Pobierz wpisy**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="3fd8f-172">Kliknij strzałkę listy rozwijanej w celu <xref:System.Windows.Forms.ComboBox> wyświetlenia dat wejścia.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="3fd8f-173">Aby wybrać i wyświetlić poszczególne wpisy</span><span class="sxs-lookup"><span data-stu-id="3fd8f-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="3fd8f-174">Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `Display` zdarzeń dla przycisku i dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="3fd8f-175">Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację, a następnie prześlij wpis.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="3fd8f-176">Kliknij **pozycję Pobierz wpisy**, <xref:System.Windows.Forms.ComboBox>wybierz wpis z przycisku , a następnie kliknij przycisk **Wyświetl**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="3fd8f-177">Zawartość wybranego wpisu pojawi `DisplayEntry` <xref:System.Windows.Forms.TextBox>się w pliku .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="3fd8f-178">Włączanie użytkownikom usuwania lub modyfikowania wpisów</span><span class="sxs-lookup"><span data-stu-id="3fd8f-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="3fd8f-179">Na koniec można dołączyć dodatkowe funkcje umożliwia użytkownikom, aby `DeleteEntry` `EditEntry` usunąć lub zmodyfikować wpis za pomocą i przycisków.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="3fd8f-180">Oba przyciski pozostają wyłączone, chyba że zostanie wyświetlony wpis.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="3fd8f-181">Dodaj formanty w poniższej tabeli do formularza i ustaw odpowiednie wartości dla ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="3fd8f-182">Kontrola</span><span class="sxs-lookup"><span data-stu-id="3fd8f-182">Control</span></span>|<span data-ttu-id="3fd8f-183">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3fd8f-183">Properties</span></span>|<span data-ttu-id="3fd8f-184">Wartości</span><span class="sxs-lookup"><span data-stu-id="3fd8f-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3fd8f-185">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-185">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-186">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-186">**Text**</span></span><br /><br /> <span data-ttu-id="3fd8f-187">**Enabled (Włączony)**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="3fd8f-188">**Usuń wpis**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3fd8f-189">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-189">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-190">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-190">**Text**</span></span><br /><br /> <span data-ttu-id="3fd8f-191">**Enabled (Włączony)**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="3fd8f-192">**Edytuj wpis**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3fd8f-193">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-193">**Name**</span></span><br /><br /> <span data-ttu-id="3fd8f-194">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-194">**Text**</span></span><br /><br /> <span data-ttu-id="3fd8f-195">**Enabled (Włączony)**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="3fd8f-196">**Prześlij edytuj**</span><span class="sxs-lookup"><span data-stu-id="3fd8f-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="3fd8f-197">Aby włączyć usuwanie i modyfikowanie wpisów</span><span class="sxs-lookup"><span data-stu-id="3fd8f-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="3fd8f-198">Dodaj następujący kod `Display` do <xref:System.Windows.Forms.Control.Click> zdarzenia przycisku, po . `DisplayEntry.Text = ReadString`</span><span class="sxs-lookup"><span data-stu-id="3fd8f-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="3fd8f-199">Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `DeleteEntry` zdarzeń dla przycisku i dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="3fd8f-200">Gdy użytkownik wyświetli wpis, `EditEntry` przycisk staje się włączony.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="3fd8f-201">Dodaj następujący kod <xref:System.Windows.Forms.Control.Click> do zdarzenia `Display` przycisku po `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="3fd8f-202">Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `EditEntry` zdarzeń dla przycisku i dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="3fd8f-203">Utwórz <xref:System.Windows.Forms.Control.Click> program obsługi `SubmitEdit` zdarzeń dla przycisku i dodaj następujący kod</span><span class="sxs-lookup"><span data-stu-id="3fd8f-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="3fd8f-204">Aby przetestować kod, naciśnij klawisz F5, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="3fd8f-205">Kliknij pozycję **Pobierz wpisy**, zaznacz wpis, a następnie kliknij pozycję **Wyświetl**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="3fd8f-206">Wpis pojawi się `DisplayEntry` <xref:System.Windows.Forms.TextBox>w pliku .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3fd8f-207">Kliknij **pozycję Edytuj wpis**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-207">Click **Edit Entry**.</span></span> <span data-ttu-id="3fd8f-208">Wpis pojawi się `Entry` <xref:System.Windows.Forms.TextBox>w pliku .</span><span class="sxs-lookup"><span data-stu-id="3fd8f-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3fd8f-209">Edytuj wpis w `Entry` <xref:System.Windows.Forms.TextBox> i kliknij przycisk **Prześlij edytuj**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="3fd8f-210">Otwórz `MyDiary.txt` plik, aby potwierdzić poprawek.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="3fd8f-211">Teraz wybierz wpis i kliknij przycisk **Usuń wpis**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="3fd8f-212">Po <xref:System.Windows.Forms.MessageBox> potwierdzeniu żądań kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="3fd8f-213">Zamknij aplikację i `MyDiary.txt` otwórz, aby potwierdzić usunięcie.</span><span class="sxs-lookup"><span data-stu-id="3fd8f-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fd8f-214">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fd8f-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="3fd8f-215">Przewodniki</span><span class="sxs-lookup"><span data-stu-id="3fd8f-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
