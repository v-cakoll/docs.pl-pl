---
title: 'Instrukcje: odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078580"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="17d7b-102">Instrukcje: odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="17d7b-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="17d7b-103">Możesz użyć <xref:System.Media.SoundPlayer> klasy odtwarzanie dźwięku z zasobu osadzonego.</span><span class="sxs-lookup"><span data-stu-id="17d7b-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d7b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="17d7b-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17d7b-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="17d7b-105">Compiling the Code</span></span>  
 <span data-ttu-id="17d7b-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="17d7b-106">This example requires:</span></span>  
  
 <span data-ttu-id="17d7b-107">Importowanie <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="17d7b-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="17d7b-108">W tym pliku dźwiękowego postaci zasobów osadzonych, w projekcie.</span><span class="sxs-lookup"><span data-stu-id="17d7b-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="17d7b-109">Zastępowanie "\<Nazwa_zestawu >" o nazwie zestawu, w którym jest osadzony w pliku dźwiękowego.</span><span class="sxs-lookup"><span data-stu-id="17d7b-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="17d7b-110">Nie zawiera sufiksu ".dll".</span><span class="sxs-lookup"><span data-stu-id="17d7b-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d7b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17d7b-111">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="17d7b-112">Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows</span><span class="sxs-lookup"><span data-stu-id="17d7b-112">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="17d7b-113">Instrukcje: Odtwarzanie w formularzu Windows dźwięku w pętli</span><span class="sxs-lookup"><span data-stu-id="17d7b-113">How to: Loop a Sound Playing on a Windows Form</span></span>](how-to-loop-a-sound-playing-on-a-windows-form.md)
