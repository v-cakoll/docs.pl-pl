---
title: "Porady: odbieranie ciągów z portów seryjnych w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a58ce248404bfe4d6c55bba741b332acd7fcbf5c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="09a7e-102">Porady: odbieranie ciągów z portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09a7e-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="09a7e-103">W tym temacie opisano sposób użycia `My.Computer.Ports` na odbieranie ciągów z portów szeregowych komputera w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09a7e-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="09a7e-104">Aby odbieranie ciągów z portu szeregowego</span><span class="sxs-lookup"><span data-stu-id="09a7e-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="09a7e-105">Inicjuje zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="09a7e-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  <span data-ttu-id="09a7e-106">Ustal, które portu szeregowego należy podać ciągi.</span><span class="sxs-lookup"><span data-stu-id="09a7e-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="09a7e-107">W tym przykładzie założono jest `COM1`.</span><span class="sxs-lookup"><span data-stu-id="09a7e-107">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="09a7e-108">Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołania do portu.</span><span class="sxs-lookup"><span data-stu-id="09a7e-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="09a7e-109">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="09a7e-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="09a7e-110">`Try...Catch...Finally` Bloku umożliwia zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="09a7e-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="09a7e-111">Cały kod, który manipuluje portu szeregowego powinny być wyświetlane w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="09a7e-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="09a7e-112">Utwórz `Do` pętli do odczytywania wierszy tekstu, dopóki nie są dostępne nie więcej wierszy.</span><span class="sxs-lookup"><span data-stu-id="09a7e-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  <span data-ttu-id="09a7e-113">Użyj <xref:System.IO.Ports.SerialPort.ReadLine> metody można odczytać następnego wiersza dostępne tekstu z portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="09a7e-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  <span data-ttu-id="09a7e-114">Użyj `If` instrukcji, aby ustalić, czy <xref:System.IO.Ports.SerialPort.ReadLine> metoda zwraca `Nothing` (co oznacza, że nie ma więcej tekstu jest dostępna).</span><span class="sxs-lookup"><span data-stu-id="09a7e-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="09a7e-115">Jeśli aplikacja zwracać `Nothing`, zamknąć `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="09a7e-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  <span data-ttu-id="09a7e-116">Dodaj `Else` za pomocą bloku `If` instrukcji do obsługi w przypadku, jeśli ciąg jest rzeczywiście do odczytu.</span><span class="sxs-lookup"><span data-stu-id="09a7e-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="09a7e-117">Blok dołącza ciąg z portu szeregowego zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="09a7e-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  <span data-ttu-id="09a7e-118">Zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="09a7e-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="09a7e-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="09a7e-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 <span data-ttu-id="09a7e-120">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="09a7e-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="09a7e-121">Selektor wstawek kodu, znajduje się się w **sieć i łączność**.</span><span class="sxs-lookup"><span data-stu-id="09a7e-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="09a7e-122">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="09a7e-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09a7e-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="09a7e-123">Compiling the Code</span></span>  
 <span data-ttu-id="09a7e-124">W tym przykładzie założono komputer korzysta z `COM1`.</span><span class="sxs-lookup"><span data-stu-id="09a7e-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="09a7e-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="09a7e-125">Robust Programming</span></span>  
 <span data-ttu-id="09a7e-126">W tym przykładzie założono komputer korzysta z `COM1`.</span><span class="sxs-lookup"><span data-stu-id="09a7e-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="09a7e-127">Zapewnienia większej elastyczności kod powinna zezwalać użytkownikowi na wybranie wybranego portu szeregowego z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="09a7e-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="09a7e-128">Aby uzyskać więcej informacji, zobacz [porady: portów seryjnych dostępne Pokaż](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="09a7e-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="09a7e-129">W tym przykładzie użyto `Try...Catch...Finally` bloku, aby upewnić się, że aplikacja zamyka port i aby wykryć żadnych wyjątków przekroczenia limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="09a7e-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="09a7e-130">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="09a7e-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a7e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09a7e-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="09a7e-132">Instrukcje: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="09a7e-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="09a7e-133">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="09a7e-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="09a7e-134">Instrukcje: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="09a7e-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
