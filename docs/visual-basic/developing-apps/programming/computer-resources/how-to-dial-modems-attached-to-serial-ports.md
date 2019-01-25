---
title: 'Instrukcje: Modemy dostępowe powiązane z portami seryjnymi w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db99f94d27235a7c9dca4fc5339854a39147b585
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490616"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="caee7-102">Instrukcje: Modemy dostępowe powiązane z portami seryjnymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="caee7-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="caee7-103">W tym temacie opisano sposób użycia `My.Computer.Ports` należy regulować w modem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="caee7-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="caee7-104">Zazwyczaj modem jest podłączony do jednego z portów szeregowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="caee7-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="caee7-105">Dla aplikacji do komunikowania się za pomocą modemu jest w stanie wysyłać polecenia do odpowiedniego portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="caee7-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="caee7-106">Aby wybrać modemu</span><span class="sxs-lookup"><span data-stu-id="caee7-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="caee7-107">Określ, które portu szeregowego, modem jest podłączony do.</span><span class="sxs-lookup"><span data-stu-id="caee7-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="caee7-108">W tym przykładzie przyjęto założenie, że jest na COM1.</span><span class="sxs-lookup"><span data-stu-id="caee7-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="caee7-109">Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołanie do tego portu.</span><span class="sxs-lookup"><span data-stu-id="caee7-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="caee7-110">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="caee7-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="caee7-111">`Using` Bloku zezwala aplikacji na zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="caee7-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="caee7-112">Cały kod, który obsługuje portu szeregowego, powinna zostać wyświetlona w ramach tego bloku lub w ramach `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="caee7-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  <span data-ttu-id="caee7-113">Ustaw `DtrEnable` właściwości, aby wskazać, że komputer jest gotowy do akceptowania przychodzących transmisji z modemu.</span><span class="sxs-lookup"><span data-stu-id="caee7-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="caee7-114">Wyślij polecenie wybierania i numer telefonu z modemem za pośrednictwem portu szeregowego przez <xref:System.IO.Ports.SerialPort.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="caee7-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="caee7-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="caee7-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 <span data-ttu-id="caee7-116">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="caee7-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="caee7-117">W selektorze fragmentów kodu, znajduje się w **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="caee7-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="caee7-118">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="caee7-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="caee7-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="caee7-119">Compiling the Code</span></span>  
 <span data-ttu-id="caee7-120">W tym przykładzie wymaga odwołania do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="caee7-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="caee7-121">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="caee7-121">Robust Programming</span></span>  
 <span data-ttu-id="caee7-122">W tym przykładzie przyjęto założenie, że modem jest podłączony do portu COM1.</span><span class="sxs-lookup"><span data-stu-id="caee7-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="caee7-123">Zaleca się, że kod umożliwia użytkownikowi wybrać odpowiedni port szeregowy z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="caee7-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="caee7-124">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="caee7-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="caee7-125">W tym przykładzie użyto `Using` bloku, aby upewnić się, że aplikacja zamyka port, nawet wtedy, gdy występuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="caee7-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="caee7-126">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="caee7-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="caee7-127">W tym przykładzie aplikacja odłącza portu szeregowego, po wywoływaniu modemu.</span><span class="sxs-lookup"><span data-stu-id="caee7-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="caee7-128">Realistycznie rzecz biorąc należy przenieść dane do i z modemu.</span><span class="sxs-lookup"><span data-stu-id="caee7-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="caee7-129">Aby uzyskać więcej informacji, zobacz [jak: Odbieranie ciągów z portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="caee7-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caee7-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="caee7-130">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="caee7-131">Instrukcje: Wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="caee7-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="caee7-132">Instrukcje: Odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="caee7-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="caee7-133">Instrukcje: Wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="caee7-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
