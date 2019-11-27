---
title: 'Porady: modemy dostępowe powiązane z portami seryjnymi'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345638"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="3e5a2-102">Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e5a2-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="3e5a2-103">W tym temacie opisano sposób użycia `My.Computer.Ports` do nawiązywania połączenia z modemem w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="3e5a2-104">Zwykle modem jest podłączony do jednego z portów szeregowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="3e5a2-105">Aby aplikacja mogła komunikować się z modemem, musi wysłać polecenia do odpowiedniego portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="3e5a2-106">Aby nawiązać połączenie z modemem</span><span class="sxs-lookup"><span data-stu-id="3e5a2-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="3e5a2-107">Określ port szeregowy, z którym jest połączony modem.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="3e5a2-108">W tym przykładzie przyjęto założenie, że modem jest na COM1.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="3e5a2-109">Użyj metody `My.Computer.Ports.OpenSerialPort`, aby uzyskać odwołanie do portu.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="3e5a2-110">Aby uzyskać więcej informacji, zobacz temat <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="3e5a2-111">Blok `Using` umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="3e5a2-112">Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku lub w bloku `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="3e5a2-113">Ustaw właściwość `DtrEnable` tak, aby wskazywała, że komputer jest gotowy do akceptowania przychodzącej transmisji z modemu.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="3e5a2-114">Wyślij polecenie wybierania numeru i numer telefonu do modemu przez port szeregowy za pomocą metody <xref:System.IO.Ports.SerialPort.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="3e5a2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e5a2-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="3e5a2-116">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3e5a2-117">W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="3e5a2-118">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="3e5a2-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e5a2-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3e5a2-119">Compiling the Code</span></span>  

 <span data-ttu-id="3e5a2-120">Ten przykład wymaga odwołania do przestrzeni nazw <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3e5a2-121">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="3e5a2-121">Robust Programming</span></span>  

 <span data-ttu-id="3e5a2-122">W tym przykładzie przyjęto założenie, że modem jest połączony z COM1.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="3e5a2-123">Zalecamy, aby Twój kod umożliwiał użytkownikowi wybranie żądanego portu szeregowego z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="3e5a2-124">Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="3e5a2-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="3e5a2-125">W tym przykładzie używa bloku `Using`, aby upewnić się, że aplikacja zamknie port nawet wtedy, gdy zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="3e5a2-126">Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e5a2-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="3e5a2-127">W tym przykładzie aplikacja rozłącza port szeregowy po nawiązaniu połączenia z modemem.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="3e5a2-128">Realistycznie można przesłać dane do i z modemu.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="3e5a2-129">Aby uzyskać więcej informacji, zobacz [jak to zrobić: otrzymywanie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="3e5a2-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e5a2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e5a2-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="3e5a2-131">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="3e5a2-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="3e5a2-132">Instrukcje: odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="3e5a2-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="3e5a2-133">Instrukcje: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="3e5a2-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
