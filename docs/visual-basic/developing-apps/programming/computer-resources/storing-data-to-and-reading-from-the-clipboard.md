---
title: Przechowywanie danych i odczytywanie ze Schowka
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 243fb237f3f9ba53f8b29079df08531c102c78dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349735"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="2775d-102">Przechowywanie danych i odczytywanie ze Schowka (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2775d-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>

<span data-ttu-id="2775d-103">Schowek może służyć do przechowywania danych, takich jak tekst i obrazy.</span><span class="sxs-lookup"><span data-stu-id="2775d-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="2775d-104">Ponieważ Schowek jest współużytkowane przez wszystkie aktywne procesy, może służyć do przesyłania danych między nimi.</span><span class="sxs-lookup"><span data-stu-id="2775d-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="2775d-105">Obiekt `My.Computer.Clipboard` umożliwia łatwy dostęp do Schowka oraz odczyt i zapis do niego.</span><span class="sxs-lookup"><span data-stu-id="2775d-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="2775d-106">Czytanie ze Schowka</span><span class="sxs-lookup"><span data-stu-id="2775d-106">Reading from the Clipboard</span></span>  

 <span data-ttu-id="2775d-107">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> tej metody, aby odczytać tekst w Schowku.</span><span class="sxs-lookup"><span data-stu-id="2775d-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="2775d-108">Poniższy kod odczytuje tekst i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="2775d-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="2775d-109">Aby przykład działał poprawnie, musi być przechowywany tekst.</span><span class="sxs-lookup"><span data-stu-id="2775d-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="2775d-110">W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2775d-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2775d-111">W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > Schowek**.</span><span class="sxs-lookup"><span data-stu-id="2775d-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="2775d-112">Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2775d-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="2775d-113">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> tej metody, aby pobrać obraz ze Schowka.</span><span class="sxs-lookup"><span data-stu-id="2775d-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="2775d-114">W tym przykładzie sprawdza, czy w Schowku znajduje się `PictureBox1`obraz przed pobraniem go i przypisaniem go do programu .</span><span class="sxs-lookup"><span data-stu-id="2775d-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="2775d-115">W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2775d-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2775d-116">W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > Schowek**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2775d-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="2775d-117">Elementy umieszczone w Schowku będą zachowywać się nawet po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2775d-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="2775d-118">Określanie typu pliku przechowywanego w Schowku</span><span class="sxs-lookup"><span data-stu-id="2775d-118">Determining the type of file stored in the Clipboard</span></span>  

 <span data-ttu-id="2775d-119">Dane w Schowku mogą przybierać różne formy, takie jak tekst, plik audio lub obraz.</span><span class="sxs-lookup"><span data-stu-id="2775d-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="2775d-120">Aby określić, jaki rodzaj pliku znajduje się w Schowku, można użyć takich metod, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>jak <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, i <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="2775d-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="2775d-121">Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> może być używana, jeśli masz format niestandardowy, który chcesz sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="2775d-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="2775d-122">Użyj `ContainsImage` tej funkcji, aby określić, czy dane zawarte w Schowku są obrazem.</span><span class="sxs-lookup"><span data-stu-id="2775d-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="2775d-123">Poniższy kod sprawdza, czy dane są obrazem i odpowiednio raportuje.</span><span class="sxs-lookup"><span data-stu-id="2775d-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="2775d-124">Czyszczenie Schowka</span><span class="sxs-lookup"><span data-stu-id="2775d-124">Clearing the Clipboard</span></span>  

 <span data-ttu-id="2775d-125">Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> czyści Schowek.</span><span class="sxs-lookup"><span data-stu-id="2775d-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="2775d-126">Ponieważ Schowek jest współużytkowane przez inne procesy, wyczyszczenie może mieć wpływ na te procesy.</span><span class="sxs-lookup"><span data-stu-id="2775d-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="2775d-127">Poniższy kod pokazuje, `Clear` jak używać metody.</span><span class="sxs-lookup"><span data-stu-id="2775d-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="2775d-128">Pisanie do Schowka</span><span class="sxs-lookup"><span data-stu-id="2775d-128">Writing to the Clipboard</span></span>  

 <span data-ttu-id="2775d-129">Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> pisania tekstu w Schowku służy do pisania tekstu.</span><span class="sxs-lookup"><span data-stu-id="2775d-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="2775d-130">Poniższy kod zapisuje ciąg "To jest ciąg testowy" do Schowka.</span><span class="sxs-lookup"><span data-stu-id="2775d-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2775d-131">Metoda `SetText` może zaakceptować parametr formatu, <xref:System.Windows.Forms.TextDataFormat>który zawiera typ .</span><span class="sxs-lookup"><span data-stu-id="2775d-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="2775d-132">Poniższy kod zapisuje ciąg "To jest ciąg testowy" do Schowka jako tekst RTF.</span><span class="sxs-lookup"><span data-stu-id="2775d-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2775d-133">Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> zapisywania danych w Schowku służy do zapisywania danych.</span><span class="sxs-lookup"><span data-stu-id="2775d-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="2775d-134">W tym przykładzie `DataObject` `dataChunk` zapisuje do Schowka w formacie `specialFormat`niestandardowym .</span><span class="sxs-lookup"><span data-stu-id="2775d-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="2775d-135">Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> tej metody, aby zapisać dane audio w Schowku.</span><span class="sxs-lookup"><span data-stu-id="2775d-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="2775d-136">W tym przykładzie `musicReader`tworzy tablicę `cool.wav` bajtów , odczytuje plik do niego, a następnie zapisuje go w Schowku.</span><span class="sxs-lookup"><span data-stu-id="2775d-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> <span data-ttu-id="2775d-137">Ponieważ Schowek jest dostępny dla innych użytkowników, nie należy go używać do przechowywania poufnych informacji, takich jak hasła lub poufne dane.</span><span class="sxs-lookup"><span data-stu-id="2775d-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2775d-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2775d-138">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="2775d-139">Jak: Odczyt danych obiektu z pliku XML</span><span class="sxs-lookup"><span data-stu-id="2775d-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="2775d-140">Jak: Zapisywanie danych obiektów w pliku XML</span><span class="sxs-lookup"><span data-stu-id="2775d-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
