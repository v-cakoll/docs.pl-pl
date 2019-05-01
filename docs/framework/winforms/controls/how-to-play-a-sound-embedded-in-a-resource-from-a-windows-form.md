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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913357"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Instrukcje: odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza systemu Windows
Możesz użyć <xref:System.Media.SoundPlayer> klasy odtwarzanie dźwięku z zasobu osadzonego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
 Importowanie <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
 W tym pliku dźwiękowego postaci zasobów osadzonych, w projekcie.  
  
 Zastępowanie "\<Nazwa_zestawu >" o nazwie zestawu, w którym jest osadzony w pliku dźwiękowego. Nie zawiera sufiksu ".dll".  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Media.SoundPlayer>
- [Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows](how-to-play-a-sound-from-a-windows-form.md)
- [Instrukcje: Odtwarzanie w formularzu Windows dźwięku w pętli](how-to-loop-a-sound-playing-on-a-windows-form.md)
