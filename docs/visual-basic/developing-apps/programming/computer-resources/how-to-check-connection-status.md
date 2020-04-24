---
title: 'Instrukcje: sprawdzanie stanu połączenia'
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
# <a name="how-to-check-connection-status-in-visual-basic"></a>Porady: sprawdzanie stanu połączenia w Visual Basic

<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Właściwość może służyć do określenia, czy komputer ma działającą sieć czy połączenie internetowe.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>Aby sprawdzić, czy komputer ma działające połączenie  
  
- Ustal, `IsAvailable` czy właściwość jest `True` lub `False`. Poniższy kod sprawdza stan właściwości i raportuje:  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
