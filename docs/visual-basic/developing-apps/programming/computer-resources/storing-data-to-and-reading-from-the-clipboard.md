---
title: Zapisywanie danych i odczytywania ze Schowka (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 19d0fcafb76c40a00939de59968dfaf2e6bd683c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921306"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="655d3-102">Zapisywanie danych i odczytywania ze Schowka (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="655d3-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="655d3-103">Schowek może służyć do przechowywania danych, takich jak tekst i obrazy.</span><span class="sxs-lookup"><span data-stu-id="655d3-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="655d3-104">Ponieważ Schowek jest współużytkowany przez wszystkie aktywne procesy, może służyć do przesyłania danych między nimi.</span><span class="sxs-lookup"><span data-stu-id="655d3-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="655d3-105">`My.Computer.Clipboard` Pozwala łatwo uzyskiwać dostęp do Schowka, a także odczytywanie i zapisywanie do niego.</span><span class="sxs-lookup"><span data-stu-id="655d3-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="655d3-106">Odczytywanie ze Schowka</span><span class="sxs-lookup"><span data-stu-id="655d3-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="655d3-107">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metodę w celu odczytania tekstu w Schowku.</span><span class="sxs-lookup"><span data-stu-id="655d3-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="655d3-108">Poniższy kod odczytuje tekst i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="655d3-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="655d3-109">Musi to być tekst są przechowywane w Schowku, na przykład by działała poprawnie.</span><span class="sxs-lookup"><span data-stu-id="655d3-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="655d3-110">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="655d3-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="655d3-111">W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > Schowka**.</span><span class="sxs-lookup"><span data-stu-id="655d3-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="655d3-112">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="655d3-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="655d3-113">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metodę, aby pobrać obraz ze Schowka.</span><span class="sxs-lookup"><span data-stu-id="655d3-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="655d3-114">W tym przykładzie sprawdza, czy obraz w Schowku przed ich pobraniem i przypisywanie jej do `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="655d3-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="655d3-115">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="655d3-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="655d3-116">W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > Schowka**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="655d3-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="655d3-117">Elementy umieszczane w Schowku zostanie utrzymany, nawet w przypadku, po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="655d3-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="655d3-118">Określanie typu plików przechowywanych w Schowku</span><span class="sxs-lookup"><span data-stu-id="655d3-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="655d3-119">Dane w Schowku może potrwać szereg różnych formularzy, takich jak tekst, plik dźwiękowy lub obrazu.</span><span class="sxs-lookup"><span data-stu-id="655d3-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="655d3-120">Aby ustalić, jakiego rodzaju plik znajduje się na Schowka, możesz używać metod takich jak <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, i <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="655d3-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="655d3-121"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metody można użyć, jeśli ma format niestandardowy, który chcesz sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="655d3-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="655d3-122">Użyj `ContainsImage` funkcję, aby określić, czy dane zawarte w Schowku jest obrazem.</span><span class="sxs-lookup"><span data-stu-id="655d3-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="655d3-123">Poniższy kod sprawdza, czy dane są obrazu, a następnie odpowiednio raporty.</span><span class="sxs-lookup"><span data-stu-id="655d3-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="655d3-124">Wyczyszczenie Schowka</span><span class="sxs-lookup"><span data-stu-id="655d3-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="655d3-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda czyści Schowka.</span><span class="sxs-lookup"><span data-stu-id="655d3-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="655d3-126">Ponieważ Schowek jest współużytkowany przez inne procesy, czyszczenie może mieć wpływ na tych procesów.</span><span class="sxs-lookup"><span data-stu-id="655d3-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="655d3-127">Poniższy kod przedstawia sposób użycia `Clear` metody.</span><span class="sxs-lookup"><span data-stu-id="655d3-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="655d3-128">Zapisywanie do Schowka</span><span class="sxs-lookup"><span data-stu-id="655d3-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="655d3-129">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metodę, aby wpisać tekst do Schowka.</span><span class="sxs-lookup"><span data-stu-id="655d3-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="655d3-130">Poniższy kod zapisuje ciąg "To jest testowany ciąg" do Schowka.</span><span class="sxs-lookup"><span data-stu-id="655d3-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="655d3-131">`SetText` Metoda może akceptować parametr formatu, który zawiera typ <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="655d3-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="655d3-132">Poniższy kod zapisuje ciąg "To jest testowany ciąg" do Schowka jako tekst w formacie RTF.</span><span class="sxs-lookup"><span data-stu-id="655d3-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="655d3-133">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metodę, aby zapisywać dane do Schowka.</span><span class="sxs-lookup"><span data-stu-id="655d3-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="655d3-134">Ten przykład Przepisuje `DataObject` `dataChunk` do Schowka w niestandardowy formacie `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="655d3-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="655d3-135">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metodę, aby zapisać dane audio do Schowka.</span><span class="sxs-lookup"><span data-stu-id="655d3-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="655d3-136">Ten przykład tworzy tablicę bajtów `musicReader`, odczytuje plik `cool.wav` do niego, a następnie zapisuje je do Schowka.</span><span class="sxs-lookup"><span data-stu-id="655d3-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="655d3-137">Ponieważ inni użytkownicy mogą uzyskać dostępu do Schowka, nie należy używać go do przechowywania poufne informacje, takie jak hasła lub poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="655d3-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655d3-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="655d3-138">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="655d3-139">Instrukcje: Odczytywanie danych o obiektach z pliku XML</span><span class="sxs-lookup"><span data-stu-id="655d3-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="655d3-140">Instrukcje: Zapisywania obiektów danych do pliku XML</span><span class="sxs-lookup"><span data-stu-id="655d3-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
