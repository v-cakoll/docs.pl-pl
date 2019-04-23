---
title: 'Instrukcje: Odbieranie ciągów z portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 6c832cd9ef5df904850261f4de2d769bfc28c3cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296723"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="f39a1-102">Instrukcje: Odbieranie ciągów z portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f39a1-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="f39a1-103">W tym temacie opisano sposób użycia `My.Computer.Ports` na odbieranie ciągów z portów szeregowych komputera w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f39a1-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="f39a1-104">Aby odbieranie ciągów z portu szeregowego</span><span class="sxs-lookup"><span data-stu-id="f39a1-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="f39a1-105">Inicjuje ciąg zwracany.</span><span class="sxs-lookup"><span data-stu-id="f39a1-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="f39a1-106">Określ port szeregowy, który powinien zapewnić ciągi.</span><span class="sxs-lookup"><span data-stu-id="f39a1-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="f39a1-107">W tym przykładzie przyjęto założenie, jest `COM1`.</span><span class="sxs-lookup"><span data-stu-id="f39a1-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="f39a1-108">Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołanie do tego portu.</span><span class="sxs-lookup"><span data-stu-id="f39a1-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="f39a1-109">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="f39a1-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="f39a1-110">`Try...Catch...Finally` Bloku zezwala aplikacji na zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f39a1-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="f39a1-111">Cały kod, który obsługuje portu szeregowego powinna zostać wyświetlona w ramach tego bloku.</span><span class="sxs-lookup"><span data-stu-id="f39a1-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="f39a1-112">Utwórz `Do` pętli do odczytywania wierszy tekstu, dopóki nie ma więcej wierszy są dostępne.</span><span class="sxs-lookup"><span data-stu-id="f39a1-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="f39a1-113">Użyj <xref:System.IO.Ports.SerialPort.ReadLine> metodę w celu odczytania następnego dostępnego wiersza tekstu z portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="f39a1-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="f39a1-114">Użyj `If` instrukcję, aby określić, czy <xref:System.IO.Ports.SerialPort.ReadLine> metoda zwraca `Nothing` (co oznacza brak więcej tekstu jest dostępna).</span><span class="sxs-lookup"><span data-stu-id="f39a1-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="f39a1-115">Jeśli jest on zwrócić `Nothing`, Zamknij `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="f39a1-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="f39a1-116">Dodaj `Else` za pomocą bloku `If` instrukcję, aby obsłużyć przypadek, jeśli ciąg jest faktycznie do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f39a1-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="f39a1-117">Blok dołącza ciąg z portu szeregowego do zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="f39a1-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="f39a1-118">Zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="f39a1-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="f39a1-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="f39a1-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="f39a1-120">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f39a1-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f39a1-121">W selektorze fragmentów kodu, znajduje się w **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="f39a1-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="f39a1-122">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="f39a1-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f39a1-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f39a1-123">Compiling the Code</span></span>  
 <span data-ttu-id="f39a1-124">W tym przykładzie przyjęto założenie, komputer używa `COM1`.</span><span class="sxs-lookup"><span data-stu-id="f39a1-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f39a1-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f39a1-125">Robust Programming</span></span>  
 <span data-ttu-id="f39a1-126">W tym przykładzie przyjęto założenie, komputer używa `COM1`.</span><span class="sxs-lookup"><span data-stu-id="f39a1-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="f39a1-127">W celu zwiększenia elastyczności kod powinien pozwalać użytkownikowi wybrać odpowiedni port szeregowy z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="f39a1-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="f39a1-128">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="f39a1-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="f39a1-129">W tym przykładzie użyto `Try...Catch...Finally` bloku, aby upewnić się, że aplikacja zostanie zamknięty port i przechwycić wyjątków przekroczenia limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="f39a1-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="f39a1-130">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f39a1-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39a1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f39a1-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="f39a1-132">Instrukcje: Modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="f39a1-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="f39a1-133">Instrukcje: Wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="f39a1-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="f39a1-134">Instrukcje: Wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="f39a1-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
