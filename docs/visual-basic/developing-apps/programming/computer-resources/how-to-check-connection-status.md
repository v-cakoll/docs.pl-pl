---
title: 'Instrukcje: Sprawdzanie stanu połączenia w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: bb3d5751ae7d88af05c2a77e9b64f9cb28179a35
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973018"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="6a635-102">Instrukcje: Sprawdzanie stanu połączenia w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a635-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="6a635-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Właściwość może służyć do określenia, czy komputer ma pracy sieci lub połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="6a635-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="6a635-104">Aby sprawdzić, czy komputer ma działające połączenie</span><span class="sxs-lookup"><span data-stu-id="6a635-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="6a635-105">Określić, czy `IsAvailable` właściwość `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="6a635-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="6a635-106">Poniższy kod umożliwia sprawdzenie stanu właściwości i zgłasza go:</span><span class="sxs-lookup"><span data-stu-id="6a635-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="6a635-107">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6a635-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="6a635-108">W selektorze fragmentów kodu, znajduje się w **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="6a635-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="6a635-109">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="6a635-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a635-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a635-110">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
