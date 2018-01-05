---
title: "Porady: odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90b0c2748960443c0d63d22b33566ebcb2b4545b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Porady: odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza systemu Windows
Można użyć <xref:System.Media.SoundPlayer> klasy odtwarzanie dźwięku z zasobu osadzonego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
 Importowanie <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
 W tym pliku dźwiękowego jako osadzony zasób w projekcie.  
  
 Zastępowanie "\<AssemblyName >" z nazwą zestawu, w której jest osadzony plik dźwiękowy. Nie zawiera sufiksu "dll".  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Media.SoundPlayer>  
 [Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [Instrukcje: odtwarzanie dźwięku w pętli w formularzu systemu Windows](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
