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
ms.openlocfilehash: eb8ae25f260ed434c4aafcc064be8fb6bebaaac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591382"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="3498c-102">Zapisywanie danych i odczytywania ze Schowka (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3498c-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="3498c-103">Schowek może służyć do przechowywania danych, takich jak tekst i obrazy.</span><span class="sxs-lookup"><span data-stu-id="3498c-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="3498c-104">Ponieważ Schowka jest wspólna dla wszystkich aktywnych procesów, może służyć do transferu danych między nimi.</span><span class="sxs-lookup"><span data-stu-id="3498c-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="3498c-105">`My.Computer.Clipboard` Obiektu pozwala łatwo uzyskiwać dostęp do Schowka i można odczytywać i zapisywać do niego.</span><span class="sxs-lookup"><span data-stu-id="3498c-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="3498c-106">Odczytywanie ze Schowka</span><span class="sxs-lookup"><span data-stu-id="3498c-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="3498c-107">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metody tekstu w Schowku.</span><span class="sxs-lookup"><span data-stu-id="3498c-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="3498c-108">Poniższy kod odczytuje tekst i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="3498c-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="3498c-109">Musi to być tekstu w Schowku, na przykład aby działała poprawnie.</span><span class="sxs-lookup"><span data-stu-id="3498c-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 <span data-ttu-id="3498c-110">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3498c-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3498c-111">Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > Schowka**.</span><span class="sxs-lookup"><span data-stu-id="3498c-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="3498c-112">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="3498c-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="3498c-113">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metoda pobierania obraz ze Schowka.</span><span class="sxs-lookup"><span data-stu-id="3498c-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="3498c-114">W tym przykładzie sprawdza, czy jest obraz w Schowku przed ich pobraniem i przypisywania go do `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="3498c-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 <span data-ttu-id="3498c-115">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3498c-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3498c-116">Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > Schowka**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="3498c-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="3498c-117">Elementy umieszczane w Schowku pozostają, nawet po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3498c-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="3498c-118">Określanie typu pliku przechowywanych w Schowku</span><span class="sxs-lookup"><span data-stu-id="3498c-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="3498c-119">Dane w Schowku może zająć wiele różnych formularzy, takich jak tekst, plik dźwiękowy lub obraz.</span><span class="sxs-lookup"><span data-stu-id="3498c-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="3498c-120">Aby określić, jaki rodzaj plików jest w Schowku, można użyć metody takie jak <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, i <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="3498c-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="3498c-121"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metody można użyć, jeśli masz formatu niestandardowego, który chcesz sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="3498c-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="3498c-122">Użyj `ContainsImage` funkcji, aby określić, czy dane zawarte w Schowku jest obraz.</span><span class="sxs-lookup"><span data-stu-id="3498c-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="3498c-123">Poniższy kod sprawdza, czy dane są obrazu i odpowiednio raportów.</span><span class="sxs-lookup"><span data-stu-id="3498c-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="3498c-124">Wyczyszczenie Schowka</span><span class="sxs-lookup"><span data-stu-id="3498c-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="3498c-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metody czyści Schowka.</span><span class="sxs-lookup"><span data-stu-id="3498c-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="3498c-126">Ponieważ Schowek jest współużytkowana przez inne procesy, czyszczenie może mieć wpływ na tych procesów.</span><span class="sxs-lookup"><span data-stu-id="3498c-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="3498c-127">Poniższy kod przedstawia sposób użycia `Clear` metody.</span><span class="sxs-lookup"><span data-stu-id="3498c-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="3498c-128">Zapisywanie do Schowka</span><span class="sxs-lookup"><span data-stu-id="3498c-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="3498c-129">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metodę zapisywanie tekstu do Schowka.</span><span class="sxs-lookup"><span data-stu-id="3498c-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="3498c-130">Poniższy kod zapisuje ciąg "To jest test ciąg" do Schowka.</span><span class="sxs-lookup"><span data-stu-id="3498c-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 <span data-ttu-id="3498c-131">`SetText` Metody może akceptować parametr formatu, który zawiera typ <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="3498c-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="3498c-132">Poniższy kod zapisuje ciąg "To jest test ciąg" do Schowka jako tekst w formacie RTF.</span><span class="sxs-lookup"><span data-stu-id="3498c-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 <span data-ttu-id="3498c-133">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metody można zapisać danych do Schowka.</span><span class="sxs-lookup"><span data-stu-id="3498c-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="3498c-134">W tym przykładzie zapisuje `DataObject``dataChunk` do Schowka w formatu niestandardowego `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="3498c-134">This example writes the `DataObject``dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 <span data-ttu-id="3498c-135">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metody można zapisać danych do Schowka.</span><span class="sxs-lookup"><span data-stu-id="3498c-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="3498c-136">W tym przykładzie tworzy tablicę bajtów `musicReader`, odczytuje plik `cool.wav` i zapisuje go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="3498c-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="3498c-137">Ponieważ przez innych użytkowników można uzyskać dostępu do Schowka, nie jest używana do przechowywania poufne informacje, takie jak hasła lub poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="3498c-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3498c-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3498c-138">See also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [<span data-ttu-id="3498c-139">Instrukcje: odczytywanie danych o obiektach z pliku XML</span><span class="sxs-lookup"><span data-stu-id="3498c-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="3498c-140">Instrukcje: wpisywanie danych o obiektach do pliku XML</span><span class="sxs-lookup"><span data-stu-id="3498c-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
