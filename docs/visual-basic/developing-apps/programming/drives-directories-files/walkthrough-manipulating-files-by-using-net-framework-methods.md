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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333787"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="6407d-102">Wskazówki: manipulowanie plikami za pomocą metod .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6407d-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="6407d-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span><span class="sxs-lookup"><span data-stu-id="6407d-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="6407d-104">Creating the Application</span><span class="sxs-lookup"><span data-stu-id="6407d-104">Creating the Application</span></span>

<span data-ttu-id="6407d-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span><span class="sxs-lookup"><span data-stu-id="6407d-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="6407d-106">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="6407d-106">To create the project</span></span>

1. <span data-ttu-id="6407d-107">On the **File** menu, select **New Project**.</span><span class="sxs-lookup"><span data-stu-id="6407d-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="6407d-108">In the **New Project** pane, click **Windows Application**.</span><span class="sxs-lookup"><span data-stu-id="6407d-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="6407d-109">In the **Name** box type `MyDiary` and click **OK**.</span><span class="sxs-lookup"><span data-stu-id="6407d-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="6407d-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span><span class="sxs-lookup"><span data-stu-id="6407d-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="6407d-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span><span class="sxs-lookup"><span data-stu-id="6407d-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="6407d-112">**Object**</span><span class="sxs-lookup"><span data-stu-id="6407d-112">**Object**</span></span>|<span data-ttu-id="6407d-113">**Właściwości**</span><span class="sxs-lookup"><span data-stu-id="6407d-113">**Properties**</span></span>|<span data-ttu-id="6407d-114">**Wartość**</span><span class="sxs-lookup"><span data-stu-id="6407d-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6407d-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-115">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-116">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="6407d-117">**Submit Entry**</span><span class="sxs-lookup"><span data-stu-id="6407d-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6407d-118">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-118">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-119">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="6407d-120">**Clear Entry**</span><span class="sxs-lookup"><span data-stu-id="6407d-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="6407d-121">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-121">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-122">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-122">**Text**</span></span><br /><br /> <span data-ttu-id="6407d-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="6407d-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="6407d-124">**Please enter something.**</span><span class="sxs-lookup"><span data-stu-id="6407d-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="6407d-125">Writing to the File</span><span class="sxs-lookup"><span data-stu-id="6407d-125">Writing to the File</span></span>

<span data-ttu-id="6407d-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span><span class="sxs-lookup"><span data-stu-id="6407d-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="6407d-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span><span class="sxs-lookup"><span data-stu-id="6407d-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="6407d-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span><span class="sxs-lookup"><span data-stu-id="6407d-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="6407d-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="6407d-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="6407d-130">To add writing functionality</span><span class="sxs-lookup"><span data-stu-id="6407d-130">To add writing functionality</span></span>

1. <span data-ttu-id="6407d-131">From the **View** menu, choose **Code** to open the Code Editor.</span><span class="sxs-lookup"><span data-stu-id="6407d-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="6407d-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="6407d-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="6407d-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span><span class="sxs-lookup"><span data-stu-id="6407d-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="6407d-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span><span class="sxs-lookup"><span data-stu-id="6407d-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="6407d-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span><span class="sxs-lookup"><span data-stu-id="6407d-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="6407d-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span><span class="sxs-lookup"><span data-stu-id="6407d-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="6407d-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span><span class="sxs-lookup"><span data-stu-id="6407d-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="6407d-138">Add the following code directly after `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="6407d-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="6407d-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span><span class="sxs-lookup"><span data-stu-id="6407d-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="6407d-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="6407d-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="6407d-141">Because this is a diary, the user will want to assign a date to each entry.</span><span class="sxs-lookup"><span data-stu-id="6407d-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="6407d-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span><span class="sxs-lookup"><span data-stu-id="6407d-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="6407d-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6407d-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6407d-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span><span class="sxs-lookup"><span data-stu-id="6407d-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="6407d-145">Adding Display Features to the Diary</span><span class="sxs-lookup"><span data-stu-id="6407d-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="6407d-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6407d-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6407d-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6407d-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6407d-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="6407d-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="6407d-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span><span class="sxs-lookup"><span data-stu-id="6407d-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="6407d-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span><span class="sxs-lookup"><span data-stu-id="6407d-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="6407d-151">formant</span><span class="sxs-lookup"><span data-stu-id="6407d-151">Control</span></span>|<span data-ttu-id="6407d-152">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6407d-152">Properties</span></span>|<span data-ttu-id="6407d-153">Wartości</span><span class="sxs-lookup"><span data-stu-id="6407d-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="6407d-154">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-154">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-155">**Visible**</span><span class="sxs-lookup"><span data-stu-id="6407d-155">**Visible**</span></span><br /><br /> <span data-ttu-id="6407d-156">**Size**</span><span class="sxs-lookup"><span data-stu-id="6407d-156">**Size**</span></span><br /><br /> <span data-ttu-id="6407d-157">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="6407d-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6407d-158">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-158">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-159">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="6407d-160">**Display**</span><span class="sxs-lookup"><span data-stu-id="6407d-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6407d-161">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-161">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-162">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="6407d-163">**Get Entries**</span><span class="sxs-lookup"><span data-stu-id="6407d-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="6407d-164">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-164">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-165">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-165">**Text**</span></span><br /><br /> <span data-ttu-id="6407d-166">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="6407d-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="6407d-167">**Select an Entry**</span><span class="sxs-lookup"><span data-stu-id="6407d-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="6407d-168">To populate the combo box</span><span class="sxs-lookup"><span data-stu-id="6407d-168">To populate the combo box</span></span>

1. <span data-ttu-id="6407d-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span><span class="sxs-lookup"><span data-stu-id="6407d-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="6407d-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span><span class="sxs-lookup"><span data-stu-id="6407d-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="6407d-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span><span class="sxs-lookup"><span data-stu-id="6407d-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="6407d-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span><span class="sxs-lookup"><span data-stu-id="6407d-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="6407d-173">To choose and display individual entries</span><span class="sxs-lookup"><span data-stu-id="6407d-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="6407d-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span><span class="sxs-lookup"><span data-stu-id="6407d-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="6407d-175">To test your code, press F5 to compile the application, and then submit an entry.</span><span class="sxs-lookup"><span data-stu-id="6407d-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="6407d-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span><span class="sxs-lookup"><span data-stu-id="6407d-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="6407d-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6407d-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="6407d-178">Enabling Users to Delete or Modify Entries</span><span class="sxs-lookup"><span data-stu-id="6407d-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="6407d-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span><span class="sxs-lookup"><span data-stu-id="6407d-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="6407d-180">Both buttons remain disabled unless an entry is displayed.</span><span class="sxs-lookup"><span data-stu-id="6407d-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="6407d-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span><span class="sxs-lookup"><span data-stu-id="6407d-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="6407d-182">formant</span><span class="sxs-lookup"><span data-stu-id="6407d-182">Control</span></span>|<span data-ttu-id="6407d-183">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6407d-183">Properties</span></span>|<span data-ttu-id="6407d-184">Wartości</span><span class="sxs-lookup"><span data-stu-id="6407d-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6407d-185">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-185">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-186">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-186">**Text**</span></span><br /><br /> <span data-ttu-id="6407d-187">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="6407d-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="6407d-188">**Delete Entry**</span><span class="sxs-lookup"><span data-stu-id="6407d-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6407d-189">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-189">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-190">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-190">**Text**</span></span><br /><br /> <span data-ttu-id="6407d-191">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="6407d-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="6407d-192">**Edit Entry**</span><span class="sxs-lookup"><span data-stu-id="6407d-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6407d-193">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6407d-193">**Name**</span></span><br /><br /> <span data-ttu-id="6407d-194">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6407d-194">**Text**</span></span><br /><br /> <span data-ttu-id="6407d-195">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="6407d-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="6407d-196">**Submit Edit**</span><span class="sxs-lookup"><span data-stu-id="6407d-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="6407d-197">To enable deletion and modification of entries</span><span class="sxs-lookup"><span data-stu-id="6407d-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="6407d-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="6407d-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="6407d-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span><span class="sxs-lookup"><span data-stu-id="6407d-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="6407d-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span><span class="sxs-lookup"><span data-stu-id="6407d-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="6407d-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="6407d-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="6407d-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span><span class="sxs-lookup"><span data-stu-id="6407d-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="6407d-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span><span class="sxs-lookup"><span data-stu-id="6407d-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="6407d-204">To test your code, press F5 to compile the application.</span><span class="sxs-lookup"><span data-stu-id="6407d-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="6407d-205">Click **Get Entries**, select an entry, and then click **Display**.</span><span class="sxs-lookup"><span data-stu-id="6407d-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="6407d-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6407d-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6407d-207">Click **Edit Entry**.</span><span class="sxs-lookup"><span data-stu-id="6407d-207">Click **Edit Entry**.</span></span> <span data-ttu-id="6407d-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6407d-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6407d-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span><span class="sxs-lookup"><span data-stu-id="6407d-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="6407d-210">Open the `MyDiary.txt` file to confirm your correction.</span><span class="sxs-lookup"><span data-stu-id="6407d-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="6407d-211">Now select an entry and click **Delete Entry**.</span><span class="sxs-lookup"><span data-stu-id="6407d-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="6407d-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span><span class="sxs-lookup"><span data-stu-id="6407d-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="6407d-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span><span class="sxs-lookup"><span data-stu-id="6407d-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="6407d-214">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6407d-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="6407d-215">Przewodniki</span><span class="sxs-lookup"><span data-stu-id="6407d-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
