---
title: 'Instrukcje: Wysyłanie ciągów do portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: ca799f4aa1b1c535e6955eda1bcb9740b5b2de3c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971705"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="111d4-102">Instrukcje: Wysyłanie ciągów do portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="111d4-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="111d4-103">W tym temacie opisano sposób użycia `My.Computer.Ports` na wysyłanie ciągów do portów szeregowych komputera w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="111d4-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="111d4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="111d4-104">Example</span></span>  
 <span data-ttu-id="111d4-105">W tym przykładzie wysyła ciąg do portu szeregowego COM1.</span><span class="sxs-lookup"><span data-stu-id="111d4-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="111d4-106">Może być konieczne użycie innego portu szeregowego na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="111d4-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="111d4-107">Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołanie do tego portu.</span><span class="sxs-lookup"><span data-stu-id="111d4-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="111d4-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="111d4-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="111d4-109">`Using` Bloku zezwala aplikacji na zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="111d4-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="111d4-110">Cały kod, który obsługuje portu szeregowego, powinna zostać wyświetlona w ramach tego bloku lub w ramach `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="111d4-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="111d4-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> Metoda wysyła dane do portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="111d4-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="111d4-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="111d4-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="111d4-113">W tym przykładzie przyjęto założenie, komputer używa `COM1`.</span><span class="sxs-lookup"><span data-stu-id="111d4-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="111d4-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="111d4-114">Robust Programming</span></span>  
 <span data-ttu-id="111d4-115">W tym przykładzie przyjęto założenie, komputer używa `COM1`; większej elastyczności, kod powinien pozwalać użytkownikowi wybrać odpowiedni port szeregowy z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="111d4-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="111d4-116">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie dostępnych portów seryjnych](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="111d4-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="111d4-117">W tym przykładzie użyto `Using` bloku, aby upewnić się, że aplikacja zamyka port, nawet wtedy, gdy występuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="111d4-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="111d4-118">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="111d4-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="111d4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="111d4-119">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="111d4-120">Instrukcje: Modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="111d4-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="111d4-121">Instrukcje: Wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="111d4-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
