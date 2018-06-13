---
title: 'Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: 6bef611b96c8c86a6eaf2802840e96769cd6fa34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588911"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="43ec8-102">Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43ec8-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="43ec8-103">W tym temacie opisano sposób użycia `My.Computer.Ports` do nawiązywania połączenia z modemem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43ec8-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="43ec8-104">Zazwyczaj modem jest podłączony do jednego z portów szeregowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="43ec8-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="43ec8-105">Aplikacji do komunikowania się z modemu jej wysyłać polecenia do właściwego portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="43ec8-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="43ec8-106">Aby wybrać modemu</span><span class="sxs-lookup"><span data-stu-id="43ec8-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="43ec8-107">Określ, które portu szeregowego modem jest podłączony do.</span><span class="sxs-lookup"><span data-stu-id="43ec8-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="43ec8-108">W tym przykładzie przyjęto założenie, że jest na COM1.</span><span class="sxs-lookup"><span data-stu-id="43ec8-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="43ec8-109">Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołania do portu.</span><span class="sxs-lookup"><span data-stu-id="43ec8-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="43ec8-110">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="43ec8-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="43ec8-111">`Using` Bloku umożliwia zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="43ec8-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="43ec8-112">Cały kod, który manipuluje portu szeregowego powinien pojawić się w tym bloku lub poziomu `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="43ec8-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  <span data-ttu-id="43ec8-113">Ustaw `DtrEnable` właściwości, aby wskazać, że komputer jest gotowy do akceptowania przychodzących transmisji z modemu.</span><span class="sxs-lookup"><span data-stu-id="43ec8-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="43ec8-114">Wysyłanie polecenia wybierania i numer telefonu z modemem za pośrednictwem portu szeregowego za pomocą klasy <xref:System.IO.Ports.SerialPort.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="43ec8-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="43ec8-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="43ec8-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 <span data-ttu-id="43ec8-116">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="43ec8-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="43ec8-117">Selektor wstawek kodu, znajduje się się w **sieć i łączność**.</span><span class="sxs-lookup"><span data-stu-id="43ec8-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="43ec8-118">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="43ec8-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43ec8-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="43ec8-119">Compiling the Code</span></span>  
 <span data-ttu-id="43ec8-120">W tym przykładzie wymaga odwołania do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="43ec8-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="43ec8-121">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="43ec8-121">Robust Programming</span></span>  
 <span data-ttu-id="43ec8-122">W tym przykładzie przyjęto założenie, że modem jest podłączony do COM1.</span><span class="sxs-lookup"><span data-stu-id="43ec8-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="43ec8-123">Firma Microsoft zaleca kodu pozwala na wybierz żądany port szeregowy z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="43ec8-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="43ec8-124">Aby uzyskać więcej informacji, zobacz [porady: portów seryjnych dostępne Pokaż](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="43ec8-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="43ec8-125">W tym przykładzie użyto `Using` bloku, aby się upewnić, że aplikacja zamyka port, nawet jeśli zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="43ec8-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="43ec8-126">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="43ec8-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="43ec8-127">W tym przykładzie aplikacja rozłącza portu szeregowego po wywoływaniu modemu.</span><span class="sxs-lookup"><span data-stu-id="43ec8-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="43ec8-128">Realistycznie rzecz biorąc można na przesyłanie danych do i z modemu.</span><span class="sxs-lookup"><span data-stu-id="43ec8-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="43ec8-129">Aby uzyskać więcej informacji, zobacz [porady: odbieranie ciągów z portów szeregowych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="43ec8-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ec8-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43ec8-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="43ec8-131">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="43ec8-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="43ec8-132">Instrukcje: odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="43ec8-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [<span data-ttu-id="43ec8-133">Instrukcje: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="43ec8-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
