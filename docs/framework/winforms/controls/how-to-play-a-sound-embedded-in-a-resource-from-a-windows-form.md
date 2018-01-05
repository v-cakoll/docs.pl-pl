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
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="ca649-102">Porady: odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ca649-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="ca649-103">Można użyć <xref:System.Media.SoundPlayer> klasy odtwarzanie dźwięku z zasobu osadzonego.</span><span class="sxs-lookup"><span data-stu-id="ca649-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca649-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca649-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca649-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ca649-105">Compiling the Code</span></span>  
 <span data-ttu-id="ca649-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ca649-106">This example requires:</span></span>  
  
 <span data-ttu-id="ca649-107">Importowanie <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ca649-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="ca649-108">W tym pliku dźwiękowego jako osadzony zasób w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ca649-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="ca649-109">Zastępowanie "\<AssemblyName >" z nazwą zestawu, w której jest osadzony plik dźwiękowy.</span><span class="sxs-lookup"><span data-stu-id="ca649-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="ca649-110">Nie zawiera sufiksu "dll".</span><span class="sxs-lookup"><span data-stu-id="ca649-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca649-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca649-111">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="ca649-112">Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ca649-112">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="ca649-113">Instrukcje: odtwarzanie dźwięku w pętli w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ca649-113">How to: Loop a Sound Playing on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
