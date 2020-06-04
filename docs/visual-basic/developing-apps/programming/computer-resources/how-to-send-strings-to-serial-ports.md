---
title: 'Instrukcje: wysyłanie ciągów do portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: f78df9cf1bd75432ea645c4dcc06498915ceee49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360296"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="a573d-102">Porady: wysyłanie ciągów do portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a573d-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="a573d-103">W tym temacie opisano, jak za pomocą `My.Computer.Ports` programu wysyłać ciągi do portów szeregowych komputera w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a573d-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a573d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a573d-104">Example</span></span>  

 <span data-ttu-id="a573d-105">Ten przykład wysyła ciąg do portu szeregowego COM1.</span><span class="sxs-lookup"><span data-stu-id="a573d-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="a573d-106">Może być konieczne użycie innego portu szeregowego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a573d-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="a573d-107">Użyj `My.Computer.Ports.OpenSerialPort` metody, aby uzyskać odwołanie do portu.</span><span class="sxs-lookup"><span data-stu-id="a573d-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="a573d-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a573d-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="a573d-109">`Using`Blok umożliwia aplikacji zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a573d-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="a573d-110">Cały kod, który operuje na porcie seryjnym, powinien pojawić się w tym bloku lub w `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="a573d-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="a573d-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A>Metoda wysyła dane do portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="a573d-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a573d-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a573d-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="a573d-113">W tym przykładzie przyjęto założenie, że komputer korzysta z programu `COM1` .</span><span class="sxs-lookup"><span data-stu-id="a573d-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a573d-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a573d-114">Robust Programming</span></span>  

 <span data-ttu-id="a573d-115">W tym przykładzie przyjęto założenie, że komputer jest używany `COM1` ; w celu uzyskania większej elastyczności kod powinien zezwalać użytkownikowi na wybranie żądanego portu szeregowego z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="a573d-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="a573d-116">Aby uzyskać więcej informacji, zobacz [jak: pokazać dostępne porty szeregowe](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a573d-116">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="a573d-117">W tym przykładzie używa `Using` bloku, aby upewnić się, że aplikacja zamknie port nawet wtedy, gdy zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a573d-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="a573d-118">Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a573d-118">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a573d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a573d-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="a573d-120">Instrukcje: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="a573d-120">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="a573d-121">Instrukcje: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="a573d-121">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
