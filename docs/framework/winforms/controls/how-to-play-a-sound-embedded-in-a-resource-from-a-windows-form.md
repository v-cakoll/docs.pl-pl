---
title: 'Instrukcje: Odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza Windows'
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
ms.openlocfilehash: 390f70acc99d8950a23ce514d90c79c3da765f2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631337"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Instrukcje: Odtwarzanie dźwięku osadzonego w zasobie za pomocą formularza Windows
Możesz użyć <xref:System.Media.SoundPlayer> klasy odtwarzanie dźwięku z zasobu osadzonego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
 Importowanie <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
 W tym pliku dźwiękowego postaci zasobów osadzonych, w projekcie.  
  
 Zastępowanie "\<Nazwa_zestawu >" o nazwie zestawu, w którym jest osadzony w pliku dźwiękowego. Nie zawiera sufiksu ".dll".  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Media.SoundPlayer>
- [Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
- [Instrukcje: Odtwarzanie w formularzu Windows dźwięku w pętli](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
