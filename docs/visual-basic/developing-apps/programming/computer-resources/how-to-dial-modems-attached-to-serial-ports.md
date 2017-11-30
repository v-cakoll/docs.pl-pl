---
title: "Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea1b2d6152af8919ac1aa272def4ba198b33867c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="ebacb-102">Porady: modemy dostępowe powiązane z portami seryjnymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebacb-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="ebacb-103">W tym temacie opisano sposób użycia `My.Computer.Ports` do nawiązywania połączenia z modemem w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ebacb-103">This topic describes how to use `My.Computer.Ports` to dial a modem in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="ebacb-104">Zazwyczaj modem jest podłączony do jednego z portów szeregowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ebacb-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="ebacb-105">Aplikacji do komunikowania się z modemu jej wysyłać polecenia do właściwego portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="ebacb-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="ebacb-106">Aby wybrać modemu</span><span class="sxs-lookup"><span data-stu-id="ebacb-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="ebacb-107">Określ, które portu szeregowego modem jest podłączony do.</span><span class="sxs-lookup"><span data-stu-id="ebacb-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="ebacb-108">W tym przykładzie przyjęto założenie, że jest na COM1.</span><span class="sxs-lookup"><span data-stu-id="ebacb-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="ebacb-109">Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołania do portu.</span><span class="sxs-lookup"><span data-stu-id="ebacb-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="ebacb-110">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebacb-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="ebacb-111">`Using` Bloku umożliwia zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ebacb-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="ebacb-112">Cały kod, który manipuluje portu szeregowego powinien pojawić się w tym bloku lub poziomu `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="ebacb-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  <span data-ttu-id="ebacb-113">Ustaw `DtrEnable` właściwości, aby wskazać, że komputer jest gotowy do akceptowania przychodzących transmisji z modemu.</span><span class="sxs-lookup"><span data-stu-id="ebacb-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="ebacb-114">Wysyłanie polecenia wybierania i numer telefonu z modemem za pośrednictwem portu szeregowego za pomocą klasy <xref:System.IO.Ports.SerialPort.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ebacb-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="ebacb-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="ebacb-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 <span data-ttu-id="ebacb-116">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ebacb-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ebacb-117">Selektor wstawek kodu, znajduje się się w **sieć i łączność**.</span><span class="sxs-lookup"><span data-stu-id="ebacb-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="ebacb-118">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="ebacb-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebacb-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ebacb-119">Compiling the Code</span></span>  
 <span data-ttu-id="ebacb-120">W tym przykładzie wymaga odwołania do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ebacb-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ebacb-121">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ebacb-121">Robust Programming</span></span>  
 <span data-ttu-id="ebacb-122">W tym przykładzie przyjęto założenie, że modem jest podłączony do COM1.</span><span class="sxs-lookup"><span data-stu-id="ebacb-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="ebacb-123">Firma Microsoft zaleca kodu pozwala na wybierz żądany port szeregowy z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="ebacb-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="ebacb-124">Aby uzyskać więcej informacji, zobacz [porady: portów seryjnych dostępne Pokaż](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="ebacb-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="ebacb-125">W tym przykładzie użyto `Using` bloku, aby się upewnić, że aplikacja zamyka port, nawet jeśli zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ebacb-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="ebacb-126">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ebacb-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="ebacb-127">W tym przykładzie aplikacja rozłącza portu szeregowego po wywoływaniu modemu.</span><span class="sxs-lookup"><span data-stu-id="ebacb-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="ebacb-128">Realistycznie rzecz biorąc można na przesyłanie danych do i z modemu.</span><span class="sxs-lookup"><span data-stu-id="ebacb-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="ebacb-129">Aby uzyskać więcej informacji, zobacz [porady: odbieranie ciągów z portów szeregowych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="ebacb-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebacb-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebacb-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="ebacb-131">Porady: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="ebacb-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="ebacb-132">Porady: odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="ebacb-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [<span data-ttu-id="ebacb-133">Porady: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="ebacb-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
