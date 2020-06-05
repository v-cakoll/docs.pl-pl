---
title: 'Instrukcje: odbieranie ciągów z portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 93b6b47d89d05331c85a6459bba7d6fd5e2e3377
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401839"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="a078d-102">Porady: odbieranie ciągów z portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a078d-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="a078d-103">W tym temacie opisano, jak używać `My.Computer.Ports` programu do odbierania ciągów z portów szeregowych komputera w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a078d-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="a078d-104">Aby odbierać ciągi z portu szeregowego</span><span class="sxs-lookup"><span data-stu-id="a078d-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="a078d-105">Zainicjuj ciąg Return.</span><span class="sxs-lookup"><span data-stu-id="a078d-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="a078d-106">Ustal, który port szeregowy powinien dostarczać ciągi.</span><span class="sxs-lookup"><span data-stu-id="a078d-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="a078d-107">W tym przykładzie założono, że jest to `COM1` .</span><span class="sxs-lookup"><span data-stu-id="a078d-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="a078d-108">Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu.</span><span class="sxs-lookup"><span data-stu-id="a078d-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="a078d-109">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a078d-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="a078d-110">`Try...Catch...Finally`Blok umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a078d-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="a078d-111">Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="a078d-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="a078d-112">Utwórz `Do` pętlę do czytania wierszy tekstu, dopóki nie będzie dostępnych więcej wierszy.</span><span class="sxs-lookup"><span data-stu-id="a078d-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="a078d-113">Użyj <xref:System.IO.Ports.SerialPort.ReadLine> metody, aby odczytać następny dostępny wiersz tekstu z portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="a078d-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="a078d-114">Użyj `If` instrukcji, aby określić, czy <xref:System.IO.Ports.SerialPort.ReadLine> Metoda zwraca `Nothing` (co oznacza, że nie jest dostępny żaden tekst).</span><span class="sxs-lookup"><span data-stu-id="a078d-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="a078d-115">Jeśli jest zwracana `Nothing` , Zamknij `Do` pętlę.</span><span class="sxs-lookup"><span data-stu-id="a078d-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="a078d-116">Dodaj `Else` blok do instrukcji, `If` Aby obsłużyć przypadek, jeśli ciąg jest faktycznie odczytywany.</span><span class="sxs-lookup"><span data-stu-id="a078d-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="a078d-117">Blok dołącza ciąg z portu szeregowego do zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="a078d-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="a078d-118">Zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="a078d-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="a078d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a078d-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="a078d-120">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a078d-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a078d-121">W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="a078d-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="a078d-122">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a078d-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a078d-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a078d-123">Compiling the Code</span></span>  

 <span data-ttu-id="a078d-124">W tym przykładzie przyjęto założenie, że komputer korzysta z programu `COM1` .</span><span class="sxs-lookup"><span data-stu-id="a078d-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a078d-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a078d-125">Robust Programming</span></span>  

 <span data-ttu-id="a078d-126">W tym przykładzie przyjęto założenie, że komputer korzysta z programu `COM1` .</span><span class="sxs-lookup"><span data-stu-id="a078d-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="a078d-127">Aby zapewnić większą elastyczność, kod powinien zezwalać użytkownikowi na wybranie żądanego portu szeregowego z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="a078d-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="a078d-128">Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a078d-128">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="a078d-129">W tym przykładzie używa `Try...Catch...Finally` bloku, aby upewnić się, że aplikacja zamknie port i przechwytuje wszystkie wyjątki limitów czasu.</span><span class="sxs-lookup"><span data-stu-id="a078d-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="a078d-130">Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a078d-130">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a078d-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a078d-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="a078d-132">Instrukcje: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="a078d-132">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="a078d-133">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="a078d-133">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="a078d-134">Instrukcje: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="a078d-134">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
