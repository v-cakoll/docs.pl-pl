---
title: 'Porady: odbieranie ciągów z portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345595"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="be30d-102">Porady: odbieranie ciągów z portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be30d-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="be30d-103">W tym temacie `My.Computer.Ports` opisano sposób odbierania ciągów z portów szeregowych komputera w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="be30d-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="be30d-104">Aby odbierać ciągi z portu szeregowego</span><span class="sxs-lookup"><span data-stu-id="be30d-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="be30d-105">Zainicjować ciąg zwrotny.</span><span class="sxs-lookup"><span data-stu-id="be30d-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="be30d-106">Określ, który port szeregowy powinien dostarczać ciągi.</span><span class="sxs-lookup"><span data-stu-id="be30d-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="be30d-107">W tym przykładzie `COM1`przyjęto założenie, że jest .</span><span class="sxs-lookup"><span data-stu-id="be30d-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="be30d-108">Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu.</span><span class="sxs-lookup"><span data-stu-id="be30d-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="be30d-109">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="be30d-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="be30d-110">Blok `Try...Catch...Finally` umożliwia aplikacji, aby zamknąć port szeregowy, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="be30d-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="be30d-111">Cały kod, który manipuluje portem szeregowym powinny pojawić się w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="be30d-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="be30d-112">Utwórz `Do` pętlę do czytania wierszy tekstu, dopóki nie będzie dostępnych więcej wierszy.</span><span class="sxs-lookup"><span data-stu-id="be30d-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="be30d-113">Użyj <xref:System.IO.Ports.SerialPort.ReadLine> tej metody, aby odczytać następny dostępny wiersz tekstu z portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="be30d-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="be30d-114">Użyj `If` instrukcji, aby <xref:System.IO.Ports.SerialPort.ReadLine> ustalić, `Nothing` czy metoda zwraca (co oznacza, że nie ma więcej tekstu).</span><span class="sxs-lookup"><span data-stu-id="be30d-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="be30d-115">Jeśli `Nothing`powróci, wyjdź z `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="be30d-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="be30d-116">Dodaj `Else` blok do `If` instrukcji do obsługi sprawy, jeśli ciąg jest rzeczywiście odczytywany.</span><span class="sxs-lookup"><span data-stu-id="be30d-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="be30d-117">Blok dołącza ciąg z portu szeregowego do ciągu zwracany.</span><span class="sxs-lookup"><span data-stu-id="be30d-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="be30d-118">Zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="be30d-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="be30d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="be30d-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="be30d-120">W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="be30d-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="be30d-121">W selektorze fragmentów kodu znajduje się w **sekcji Łączność i sieć**.</span><span class="sxs-lookup"><span data-stu-id="be30d-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="be30d-122">Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="be30d-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be30d-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="be30d-123">Compiling the Code</span></span>  

 <span data-ttu-id="be30d-124">W tym przykładzie przyjęto założenie, że komputer jest używany `COM1`.</span><span class="sxs-lookup"><span data-stu-id="be30d-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="be30d-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="be30d-125">Robust Programming</span></span>  

 <span data-ttu-id="be30d-126">W tym przykładzie przyjęto założenie, że komputer jest używany `COM1`.</span><span class="sxs-lookup"><span data-stu-id="be30d-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="be30d-127">Aby uzyskać większą elastyczność, kod powinien umożliwić użytkownikowi wybranie żądanego portu szeregowego z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="be30d-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="be30d-128">Aby uzyskać więcej informacji, zobacz [Jak: Pokaż dostępne porty szeregowe](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="be30d-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="be30d-129">W tym przykładzie `Try...Catch...Finally` użyto bloku, aby upewnić się, że aplikacja zamyka port i przechwytują wszelkie wyjątki limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="be30d-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="be30d-130">Aby uzyskać więcej informacji, zobacz [Try... Złapać... Wreszcie Oświadczenie](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="be30d-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be30d-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be30d-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="be30d-132">Instrukcje: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="be30d-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="be30d-133">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="be30d-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="be30d-134">Instrukcje: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="be30d-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
