---
title: 'Porady: sprawdzanie stanu połączenia'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 89ef431759dac25bd213fd954db0712ad95434b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345880"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="d675b-102">Porady: sprawdzanie stanu połączenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d675b-102">How to: Check Connection Status in Visual Basic</span></span>

<span data-ttu-id="d675b-103">Właściwości <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> można użyć do określenia, czy komputer ma działającą sieć lub połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="d675b-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="d675b-104">Aby sprawdzić, czy komputer ma połączenie robocze</span><span class="sxs-lookup"><span data-stu-id="d675b-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="d675b-105">Określ, `IsAvailable` czy `True` `False`właściwość jest lub .</span><span class="sxs-lookup"><span data-stu-id="d675b-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="d675b-106">Poniższy kod sprawdza stan właściwości i zgłasza go:</span><span class="sxs-lookup"><span data-stu-id="d675b-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="d675b-107">W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="d675b-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="d675b-108">W selektorze fragmentów kodu znajduje się w **sekcji Łączność i sieć**.</span><span class="sxs-lookup"><span data-stu-id="d675b-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="d675b-109">Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="d675b-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d675b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d675b-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
