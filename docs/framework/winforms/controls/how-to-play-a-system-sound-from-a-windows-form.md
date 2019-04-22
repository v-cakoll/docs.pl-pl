---
title: 'Instrukcje: odtwarzanie dźwięku systemowego za pomocą formularza systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
ms.openlocfilehash: d85d8cd40ff2b32cb3f2a79cf9a8221964f186c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153234"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>Instrukcje: odtwarzanie dźwięku systemowego za pomocą formularza systemu Windows
Poniższy kod przykładowy odtwarza `Exclamation` dźwięku systemowego w czasie wykonywania. Aby uzyskać więcej informacji na temat dźwięki systemu, zobacz <xref:System.Media.SystemSounds>.  
  
## <a name="example"></a>Przykład  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [Instrukcje: Odtwórz sygnał dźwiękowy z formularza Windows](how-to-play-a-beep-from-a-windows-form.md)
- [Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows](how-to-play-a-sound-from-a-windows-form.md)
