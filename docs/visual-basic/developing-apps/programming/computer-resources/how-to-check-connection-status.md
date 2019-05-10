---
title: 'Instrukcje: Sprawdzanie stanu połączenia w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 1a03b181c2e363c3380c4f9858b629713641f2c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620674"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="52e35-102">Instrukcje: Sprawdzanie stanu połączenia w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52e35-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="52e35-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Właściwość może służyć do określenia, czy komputer ma pracy sieci lub połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="52e35-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="52e35-104">Aby sprawdzić, czy komputer ma działające połączenie</span><span class="sxs-lookup"><span data-stu-id="52e35-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="52e35-105">Określić, czy `IsAvailable` właściwość `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="52e35-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="52e35-106">Poniższy kod umożliwia sprawdzenie stanu właściwości i zgłasza go:</span><span class="sxs-lookup"><span data-stu-id="52e35-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="52e35-107">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="52e35-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="52e35-108">W selektorze fragmentów kodu, znajduje się w **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="52e35-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="52e35-109">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="52e35-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e35-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52e35-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
